---
title: "MP3 Won't Detect"
date: 2008-08-31
forum: Multimedia Software
---

### Post by MeowMoo on 2008-08-31
Hi, so I finally went out and bought a cable to connect my Mp3 Player to my PC after losing it a while ago.

To my surprise, when I plugged in the device to my computer running Ubuntu 8.04, it did not detect it as usually Linux detects all my USB devices.

It's an MPIO MO100 and when it's plugged in, it starts recharging itself (the Mp3 screen shows) but Ubuntu will not detect it. This was not a problem on Windows however. It does not show up in the /media folder either.

Any advice? Thanks. :popcorn:

---

### Post by MeowMoo on 2008-08-31
Additionally: 


> tq@tq-desktop:~$  sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24136   193872388+  83  Linux
/dev/sda2           24137       24321     1486012+   5  Extended
/dev/sda5           24137       24321     1485981   82  Linux swap / Solaris


> tq@tq-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/tq/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tq)


> tq@tq-desktop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c001 Logitech, Inc. N48/M-BB48 [FirstMouse Plus]
Bus 001 Device 001: ID 0000:0000  


Sorry for the double post, just wanted to organize it a bit. :)

---

### Post by MeowMoo on 2008-08-31
Bump. If this is the wrong section, can a mod please move it to the appropriate one? I thought it may have something to do with multimedia. :)

---

