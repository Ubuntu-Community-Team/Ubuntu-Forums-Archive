---
title: "cd/dvd media not detected"
date: 2010-03-10
forum: Multimedia Software
---

### Post by tava0002 on 2010-03-10
Trying to burn an iso but blank cd/dvd media is not detected (most of the time).  If I open Brasero select the iso THEN put in the media it will detect about half the time but burning fails which may or may not be related.

When I put in an audio cd or movie dvd the drive light is going but nothing happens.

I have tried burning with Brasero, K3B, GnomeBaker, XFburn.  I also have Devede installed and it's related packages which works fine.

It's the old story of this used to work with Win XP but not with Karmic and I don't want to go back if I can help it.

Any help appreciated:

```
[    2.140539] ata4.01: ATAPI: BENQ    DVD DD DW1620, B7W9, max UDMA/33
[    2.140562] ata4: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0) ACPI=0x701f (900:60:0x14)
[    2.156501] ata4.01: configured for UDMA/33
[    2.159027] scsi 3:0:1:0: CD-ROM            BENQ     DVD DD DW1620    B7W9 PQ: 0 ANSI: 5
[    2.165833] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
```

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=4f4216c8-fbfb-412f-af8f-0a669c0cd2e2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=925e1da2-08bc-457a-8d1f-7c3d4d924df6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by tava0002 on 2010-03-11
I'm possibly barking up the wrong tree but this is what I get if I try to mount manually

desktop:~$ sudo mount /dev/scd0 /media/cdrom
mount: /dev/sr0: unknown device

I also tried

desktop:/dev$ sudo mount /dev/scd0 /media/cdrom -t udf
[sudo] password:
mount: no medium found on /dev/sr0

desktop:/$ ls /dev -l | grep dvd
lrwxrwxrwx  1 root root             3 2010-03-10 20:05 dvd -> sr0
lrwxrwxrwx  1 root root             3 2010-03-10 20:05 dvdrw -> sr0
drwxr-xr-x  2 root root            60 2010-03-10 20:04 pktcdvd

desktop:/$ ls /dev -l | grep cdrom
lrwxrwxrwx  1 root root             3 2010-03-10 20:05 cdrom -> sr0
crw-rw----  1 root cdrom      21,   1 2010-03-10 20:04 sg1
brw-rw----+ 1 root cdrom      11,   0 2010-03-10 20:04 sr0

---

### Post by tava0002 on 2010-03-12
For future reference this appears to be a known issue.  I have no idea when or if it has been fixed.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/397806]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/397806")

---

### Post by tava0002 on 2010-04-07
Although I'm the only one that has posted in this thread, I thought I'd share what happened with this just in case anyone else has a similar problem.  

I tried a different dvd a couple days later and the drive would not open and the drive light did not come on.

Long story short, the drive took a dump.

Tried a different drive and all was ok, cd's/dvd's recognized and I could burn.

---

