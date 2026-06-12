---
title: "[SOLVED] 2nd hard drive problems"
date: 2009-01-04
forum: Mythbuntu
---

### Post by quasifly on 2009-01-04
I think I've got my second hard drive (500 gb) mounted but when I add it /media/sda1 to my mythtv storage directories my pvr-150 quits working. When I delete the new storage directory. It works again. Im assuming Im doing something wrong with my new hard drive or maybe my motherboard is no good. Here is some info let me know if you need some more logs or such:

aaron@aaron-desktop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006b8e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xca33ca33

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1459    11719386   83  Linux
/dev/sdb2            1460       19457   144568935    5  Extended
/dev/sdb5            1460        1583      995998+  82  Linux swap / Solaris
/dev/sdb6            1584       19457   143572873+  83  Linux
aaron@aaron-desktop:~$ sudo blkid
/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="e8b470c8-8b09-4b47-9eb9-dcad99136931" TYPE="xfs" 
/dev/sda3: UUID="1027d539-57af-40ae-939d-233641246221" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="314f667a-e7e0-4dcc-9ca4-5c81196724fe" 
/dev/sda6: UUID="4ac9e1e2-bc0a-49bb-936d-2a1e236cd6df" TYPE="xfs" 
/dev/sda7: TYPE="swap" UUID="d83eb9d4-75df-4ee2-9fa0-e5fc7a4df2a0" 
/dev/sda8: UUID="1a2ba968-9b95-4edc-851c-491db7560080" TYPE="xfs" 
/dev/sdb1: UUID="44db7486-6be0-4b6b-8e05-2f413a06130c" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="2ee8f611-daac-463f-9f40-58b609f74fd6" 
/dev/sdb6: UUID="faf9c84d-ac67-412b-bceb-91966285673d" TYPE="xfs" 
aaron@aaron-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=44db7486-6be0-4b6b-8e05-2f413a06130c /               ext3    errors=remount-ro 0       1
# /dev/sdb6
UUID=faf9c84d-ac67-412b-bceb-91966285673d /var/lib        xfs     defaults        0       2
# /dev/sdb5
UUID=2ee8f611-daac-463f-9f40-58b609f74fd6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
UUID=e8b470c8-8b09-4b47-9eb9-dcad99136931 /media/sda1     xfs     defaults        0       2
aaron@aaron-desktop:~$ id
uid=1000(aaron) gid=1000(aaron) groups=4(adm),20(dialout),24(cdrom),46(plugdev),108(mythtv),115(lpadmin),117(sambashare),123(admin),1000(aaron)
aaron@aaron-desktop:~$

---

### Post by murbanci on 2009-01-04
Fdisk is showing one partition on sda but blkid is showing 2 swap, 3 xfs and 1 ext3.  Is this what you want?  If would probably be better if the whole disk is one partition of a single file system if you are just using it for storage.

---

### Post by murbanci on 2009-01-04
Are you sure you have it mounted?  Heres a good guide for installing a new drive [https://help.ubuntu.com/community/InstallingANewHardDrive?highlight=(hard)|(list)|(drives](https://help.ubuntu.com/community/InstallingANewHardDrive?highlight=(hard)|(list)|(drives))

---

### Post by klc5555 on 2009-01-05
> **quasifly said:**
> I think I've got my second hard drive (500 gb) mounted but when I add it /media/sda1 to my mythtv storage directories my pvr-150 quits working. When I delete the new storage directory. It works again. Im assuming Im doing something wrong with my new hard drive or maybe my motherboard is no good. Here is some info let me know if you need some more logs or such:

$


Check the owner/group/permissions of the new partition with ls -l /media  Odds are they're set to "root", so mythtv can't use them. If one directory in the default storage group is unwritable, Livetv kicks you back to the mythtv main menu and all recording fails.

sudo chown mythtv <your new storage directory>
sudo chgrp mythtv <your new storage directory>
sudo chmod 775    <your new storage directory>

should get the new directory up and running for you.

Cheers! :)

---

### Post by quasifly on 2009-01-07
This worked great. Thanks for the help.

> **klc5555 said:**
> Check the owner/group/permissions of the new partition with ls -l /media  Odds are they're set to "root", so mythtv can't use them. If one directory in the default storage group is unwritable, Livetv kicks you back to the mythtv main menu and all recording fails.

sudo chown mythtv <your new storage directory>
sudo chgrp mythtv <your new storage directory>
sudo chmod 775    <your new storage directory>

should get the new directory up and running for you.

Cheers! :)

---

