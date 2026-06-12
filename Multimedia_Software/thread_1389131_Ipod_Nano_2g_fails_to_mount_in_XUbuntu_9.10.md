---
title: "Ipod Nano 2g fails to mount in XUbuntu 9.10"
date: 2010-01-24
forum: Multimedia Software
---

### Post by sasciame on 2010-01-24
My 4 GB 2nd generation Ipod nano will not mount to my Compaq Presario 2105US running Xubuntu 9.10.  I get a message that says, "Failed to mount Ipod" with a description that says, "mount: wrong fs type, bad option, bad superblock on /dev/sdb1,        missing codepage or helper program, or other error        In some cases useful info is found in syslog - try        dmesg | tail  or so  ."


I even went back to my XP to restore the ipod to factory settings essentially formating it, to see if that would help, but I get the same result. 

Does anyone have any suggestions?  Is there something that I may have overlooked?  Any help would be much appreciated.

---

### Post by sasciame on 2010-01-24
I forgot to mention that I do have Xubuntu-restricted-extras package installed.

Based on the above error message, I suspected that maybe something was wrong with the filesystem or integrity of the storage media (ipod itself)  So I ran dosfsck.  The output it gave me said:  Logical sector size (23597) is not a multiple of the physical sector size.

I plugged the ipod into my XP computer and ran chkdsk.  It said there were no problems.

I am not sure what to do next.  The ipod appears to be ok (not damaged) and can be plugged into other computers running XP with no problems.  I trying to figure out why Xubuntu will not mount it.

Any help would be much appreciated.

---

### Post by sasciame on 2010-01-24
Here is some more additional info that I think will be helpful.

steven@steven-laptop:~$ dmesg | tail
[ 2435.688184] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 2435.688202] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 2438.551942] FAT: invalid media value (0x2f)
[ 2438.551964] VFS: Can't find a valid FAT filesystem on dev sdb1.
[ 2439.226748] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[ 2439.236749] FAT: invalid media value (0x2f)
[ 2439.236760] VFS: Can't find a valid FAT filesystem on dev sdb1.
[ 2439.286736] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[ 2439.296749] FAT: invalid media value (0x2f)
[ 2439.296761] VFS: Can't find a valid FAT filesystem on dev sdb1.

---

### Post by sasciame on 2010-01-24
This also might help to get to the bottom of this.  Is this normal? 


steven@steven-laptop:~$ sudo fdisk /dev/sdb
[sudo] password for steven: 
Note: sector size is 2048 (not 512)

Command (m for help): p

Disk /dev/sdb: 4060 MB, 4060086272 bytes
103 heads, 42 sectors/track, 458 cylinders
Units = cylinders of 4326 * 2048 = 8859648 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          12       96264    0  Empty
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 1, 22)
Partition 1 has different physical/logical endings:
     phys=(2, 254, 63) logical=(11, 14, 21)
Partition 1 does not end on cylinder boundary.
/dev/sdb2              12         459     3868536    b  W95 FAT32
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(3, 0, 1) logical=(11, 14, 22)
Partition 2 has different physical/logical endings:
     phys=(123, 102, 42) logical=(458, 27, 21)

Command (m for help):

---

### Post by sasciame on 2010-01-24
Using fdisk I recreated the partitions.

Here is a list of the partitions:

steven@steven-laptop:~$ sudo fdisk -l /dev/sdb
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 4060 MB, 4060086272 bytes
103 heads, 42 sectors/track, 458 cylinders
Units = cylinders of 4326 * 2048 = 8859648 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          11       95088    0  Empty
/dev/sdb2              12         458     3867444    b  W95 FAT32
steven@steven-laptop:~$ 



That looks "cleaner" than before, but this did not fix the actual problem.  When I plug the ipod in I get the message:

Failed to mount "iPod"
mount: wrong fs type, bad option, bad superblock on /dev/sdb2,        missing codepage or helper program, or other error        In some cases useful info is found in syslog - try        dmesg | tail  or so  .

steven@steven-laptop:~$ dmesg | tail
[ 8229.288483] VFS: Can't find a valid FAT filesystem on dev sdb2.
[ 8229.327891] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[ 8229.337845] FAT: bogus number of reserved sectors
[ 8229.337863] VFS: Can't find a valid FAT filesystem on dev sdb2.
[ 8236.439701] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[ 8236.449679] FAT: bogus number of reserved sectors
[ 8236.449697] VFS: Can't find a valid FAT filesystem on dev sdb1.
[ 8236.526485] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[ 8236.535639] FAT: bogus number of reserved sectors
[ 8236.535656] VFS: Can't find a valid FAT filesystem on dev sdb1.



Any ideas?

---

### Post by sasciame on 2010-01-24
I just changedthe partition sdb2 from FAT32 to FAT32 (LBA) to see if that would help, but it didn't.  I still get the same result (my ipod will not mount). (see above)



steven@steven-laptop:~$ sudo fdisk -l /dev/sdb
[sudo] password for steven: 
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 4060 MB, 4060086272 bytes
103 heads, 42 sectors/track, 458 cylinders
Units = cylinders of 4326 * 2048 = 8859648 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          11       95088    0  Empty
/dev/sdb2              12         458     3867444    c  W95 FAT32 (LBA)
steven@steven-laptop:~$ 

It says the sector size is 2048 (not 512)   Is this possibly causing my problem?  How can this be changed or corrected?

---

### Post by sasciame on 2010-01-29
I restored my ipod back to factory settings by connecting it to my computer with windows XP.

It still works perfectly on my computer with XP, but not on my XUbuntu machine.  It is odd to me that the factory settings incorrectly creates the partitions

steven@steven-laptop:~$ sudo fdisk -l /dev/sdb
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 4060 MB, 4060086272 bytes
103 heads, 42 sectors/track, 458 cylinders
Units = cylinders of 4326 * 2048 = 8859648 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          12       96264    0  Empty
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 1, 22)
Partition 1 has different physical/logical endings:
     phys=(2, 254, 63) logical=(11, 14, 21)
Partition 1 does not end on cylinder boundary.
/dev/sdb2              12         459     3868536    b  W95 FAT32
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(3, 0, 1) logical=(11, 14, 22)
Partition 2 has different physical/logical endings:
     phys=(123, 102, 42) logical=(458, 27, 21)


Here is some additional output that might help:
lsusb
Bus 001 Device 002: ID 05ac:1260 Apple, Inc. iPod Nano 2.Gen
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


and dmseg that pertains to this situation:

[30927.640135] usb 1-1: new full speed USB device using ohci_hcd and address 2
[30927.861586] usb 1-1: configuration #1 chosen from 2 choices
[30928.231736] Initializing USB Mass Storage driver...
[30928.235465] scsi2 : SCSI emulation for USB Mass Storage devices
[30928.237742] usbcore: registered new interface driver usb-storage
[30928.237759] USB Mass Storage support registered.
[30928.241006] usb-storage: device found at 2
[30928.241018] usb-storage: waiting for device to settle before scanning
[30933.241484] usb-storage: device scan complete
[30933.250416] scsi 2:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[30933.251970] sd 2:0:0:0: Attached scsi generic sg2 type 0
[30933.280978] sd 2:0:0:0: [sdb] 1982464 2048-byte logical blocks: (4.06 GB/3.78 GiB)
[30933.307356] sd 2:0:0:0: [sdb] Write Protect is off
[30933.307378] sd 2:0:0:0: [sdb] Mode Sense: 68 00 00 08
[30933.307388] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[30933.334429] sd 2:0:0:0: [sdb] 1982464 2048-byte logical blocks: (4.06 GB/3.78 GiB)
[30933.341456] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[30933.341484]  sdb: sdb1 sdb2
[30933.407926] sd 2:0:0:0: [sdb] 1982464 2048-byte logical blocks: (4.06 GB/3.78 GiB)
[30933.429398] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[30933.429425] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[30936.579896] FAT: invalid media value (0x2f)
[30936.579919] VFS: Can't find a valid FAT filesystem on dev sdb1.
[30937.191689] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[30937.209678] FAT: invalid media value (0x2f)
[30937.209692] VFS: Can't find a valid FAT filesystem on dev sdb1.
[30937.276051] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[30937.344189] FAT: invalid media value (0x2f)
[30937.344204] VFS: Can't find a valid FAT filesystem on dev sdb1.
[30942.826756] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!





Is there anybody out there?

---

### Post by sasciame on 2010-02-14
I reinstalled XP and my ipod nano works perfectly!   

Thank you for all of the help!

This has been solved by switching back to Microsoft Windows!

---

