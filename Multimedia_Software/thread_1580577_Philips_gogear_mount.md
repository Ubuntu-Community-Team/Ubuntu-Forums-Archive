---
title: "Philips gogear mount"
date: 2010-09-23
forum: Multimedia Software
---

### Post by Ka Fish on 2010-09-23
My mp3 player somehow has 2 mount points. Sometimes when I plug it in, it will just mount & unmount by itself for a while. How can I tell which 1 is the good mount-point? How do I delete the bad 1? Sorry I'm not that good in a command prompt. I'll need step by step directions.

---

### Post by ajgreeny on 2010-09-23
What makes you think it has two mountpoints?  Have you made a mount point for it manually?  It seems a little unlikely if you don't like the command line, but you never know.

Attach the player and then run ```
sudo fdisk -l
```that's a lower case L at the end, and report back here the output.  Also when it is mounted at just one of those mountpoints at a time, report the output of ```
mount
``` for both mountpoints, if you can.

---

### Post by Ka Fish on 2010-09-23
It was a manual install, some time ago. I believe it has 2 mount-points because when I boot, have 3 usb extensions listed, 1 generic mp3 & 2 philips.  I cant get it to mount to the other 1.                                                                                                     ka@ka-desktop:~$ sudo fdisk -l
[sudo] password for ka: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c3a90

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29838   239673703+  83  Linux
/dev/sda2           29839       30401     4522297+   5  Extended
/dev/sda5           29839       30401     4522266   82  Linux swap / Solaris
Note: sector size is 4096 (not 512)

Disk /dev/sdb: 3931 MB, 3931111424 bytes
163 heads, 46 sectors/track, 128 cylinders
Units = cylinders of 7498 * 4096 = 30711808 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         128     3838792    b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 46) logical=(0, 1, 1)
Partition 1 does not start on physical sector boundary.
ka@ka-desktop:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ka/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ka)
/dev/sdb1 on /media/Philips type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
ka@ka-desktop:~$

---

### Post by ajgreeny on 2010-09-24
Well, it looks from that, and assuming it was mounted at the "good" mount point that /media/Philips is the good one.

Just out of interest run ```
sudo blkid
``` with the player attached and mounted.  I suspect that the player partition is labeled "Philips" and that this is what will show in the blkid output.

If you have made a mount point for it manually other than /media/Philips, it may be worth deleting it with ```
sudo rmdir /bad/mount/point
```

---

### Post by Ka Fish on 2010-09-24
ka@ka-desktop:~$ sudo blkid
/dev/sda1: UUID="7766aec0-296d-4320-81c5-461ec2418cce" TYPE="ext4" 
/dev/sda5: UUID="81eefbf5-d535-408e-ac53-e9734c2a98e0" TYPE="swap" 
/dev/sdb1: UUID="58E2-0FDF" TYPE="vfat" 
/dev/sdc1: LABEL="Philips" UUID="5A23-C2D4" TYPE="vfat" 
ka@kadesktop:~$                                                                                                                                      A few months ago  I got it to tell me it had a problem with the volume control. after  installing the program to fix that, it no longer recognizes the mp3  player. I get a file error on the mp3 player itself. I used  the disk on a windows machine to reinstall & update it.

---

