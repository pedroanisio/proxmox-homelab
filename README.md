# Proxmox Disk PassThrough Script
Disk PassThrough Script to PassThrough Physical Disk to Proxmox VM - (excluding those used by ZFS Pools)
#

### Description:

* Enumerates Physical Disks available on your Proxmox Host (excluding those used by ZFS pools)
* Lists all Available VMs
* Lets you pick Disks and a VM, then Generates `qm set` Commands for easy Disk PassThrough

### Key Features: 

* Automatically finds `/dev/disk/by-id` Paths, Prioritizing WWN Identifiers when available
* Prevents SCSI Index conflicts by checking your VM’s Current Configuration and Assigning the next available `scsiX` Parameter
* Outputs the Final Commands you can Run directly or use in your Automation Scripts

### Requirements: 

* Must Run on a Proxmox Host with `qm` and `zpool` Commands available

* Python 3.x

* Sufficient Privileges to run `lsblk`, `zpool`, and `qm` Commands

**NOTE:**

* This Script does not Automatically Apply Changes; it only Generates 
  the necessary Commands. 

* **Use at Your Own Risk** - Users should Carefully Review the Output before Running the Commands.

* Ensure you have proper Backups and Understand the Implications of PassingThrough Disks to a VM.

### Usage: 

1. Run the Script directly on the Host with the Command: `python3 disk_passthrough.py`
2. Select the desired Disks from the Enumerated List
3. Choose your Target VM from the Displayed List
4. Review and Run the Generated Commands

## MIT License

Copyright (c) 2024 Pedro Anisio Silva

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
