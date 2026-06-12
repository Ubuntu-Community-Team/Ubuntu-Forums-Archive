---
title: "External LG usb CD drive not recognized"
date: 2012-10-04
forum: Multimedia Software
---

### Post by semsaudade on 2012-10-04
Hi to everybody. I have Ubuntu 12.04.1 LTS and I am trying to use an external usb CD-DVD drive (manifacturer LG, model GP10NW20).
When I connect the drive tu USB it is correctly powered, but it isn't apparently mounted or recognized by Ubuntu (or I am unable to find it in \media or anywhere).

Anyone who can help me? I post here some trial I made...
Thanks a lot!!!!!!!

```

giancarlo@giancarlo-siComputer:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 05e3:0716 Genesys Logic, Inc. USB 2.0 
giancarlo@giancarlo-siComputer:~$ dmesg | grep CD-ROM
[  205.562669] scsi 7:0:0:0: CD-ROM            HL-DT-ST DVDRAM GP10NW20  1.01 PQ: 0 ANSI: 0
[  205.586142] cdrom: Uniform CD-ROM driver Revision: 3.20
[  205.586651] sr 7:0:0:0: Attached scsi CD-ROM sr0
giancarlo@giancarlo-siComputer:~$ cdrecord -scanbus
wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.
giancarlo@giancarlo-siComputer:~$ ls -l /media
totale 8
drwx------ 1 giancarlo giancarlo 4096 lug 23 20:21 01CC76C1E28C6840
drwx------ 1 giancarlo giancarlo 4096 lug 13 19:53 System
giancarlo@giancarlo-siComputer:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=6cc4f287-d533-461b-bbaa-9744b255ac31 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=57007b61-d446-4ec4-864c-e60eda9c3c22 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=bfb4c1b4-5096-4adb-b280-e8bce63d45d8 none            swap    sw              0       0

```

---

### Post by semsaudade on 2012-10-05
Solved! Just need to install Xfburn.

---

