---
title: "[SOLVED] auto mount sda for recordings (darn FSTAB!)"
date: 2007-10-19
forum: Mythbuntu
---

### Post by govee on 2007-10-19
I would like sda1 mounted at bootup but I am not editing the fstab correctly therefore,  when I boot the OS sda1 is not mounted. I can mount sda1 through the terminal  with "sudo mount /dev/sda1 /var/lib/mythtv/recordings". But if I restart I have to do it again. I have the file system in fstab set to auto. Is that ok? It is formatted to xfs. 

This is what I have when  I run Fdisk:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00061fa9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux

Disk /dev/hda: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf5e0f5e0

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1             767        1027     2096482+  82  Linux swap / Solaris
/dev/hda3   *           1         763     6128766   83  Linux

Partition table entries are not in disk order

And here is my Fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=2260e672-c190-41e0-8278-74cbe1b73c2a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=454f45aa-c606-4340-8f38-d06d5df5353f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sda1 	/var/lib/mythtv/recordings     auto      defaults,errors=remount-ro    0     1


thanks

---

### Post by dhorkoff on 2007-10-19
I think you probably want to set the last number 1 in the sda1 line to a 2, indicating you want it mounted during pass two rather than pass one. You can't mount it in pass one since your root file system is probably not yet mounted and so your mount point doesn't yet exist.

Something like this:

/dev/sda1 /var/lib/mythtv/recordings auto defaults 0 2

---

### Post by davemorris on 2007-10-19
You might also need to tell it the filesystem type as it might be struggling

---

### Post by govee on 2007-10-19
Thanks, 
I made both changes and it is now auto mounted.

---

