---
title: "Tip: Resolving gparted freeze on a floppyless system"
date: 2008-01-14
forum: Mythbuntu
---

### Post by ahood on 2008-01-14
**THE PROBLEM**
I am using Mythbuntu (Gutsy) and I needed to partition and format a second hard drive. I installed gparted (a partitioning tool) using Synaptic. When I launched gparted, it would start and scan for various devices. The problem was that it would never stop scanning. The scanning would be endless and I could not use gparted.

**THE SOLUTION EXPLAINED**
After some research on Google, I discovered that the problem was due to gparted getting stuck trying to read the floppy drive. My system does NOT have a floppy drive (i.e., a floppyless system). 

**CONFIRM FLOPPY DRIVE ERROR**
To confirm that gparted is getting hung up with the floppy drive, do one of the following:

(A) Start gparted from the terminal, wait a while, shut down gparted and look for a floppy drive error reported in the terminal.

(B) Look at /var/log/dmesg file and see if there are floppy drive (fd0)  error(s). Do this by entering the following command at a terminal.
> cat /var/log/dmesg | grep "fd0"

**SOLUTION**
The solution that worked for me was disabling the floppy drive in **Standard CMOS Features** section of the system BIOS. 

Unfortunately, it is not possible to provide step-by-step instructions for entering and configuring the system BIOS.

Hope this helps others....

---

