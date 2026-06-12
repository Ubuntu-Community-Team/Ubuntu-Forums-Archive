---
title: "roommate's samsung yp-t9j won't work"
date: 2007-03-10
forum: Multimedia &amp; Video
---

### Post by lunaz on 2007-03-10
hi, how can i get her mp3 player working? it doesn't mount on desktop like mine does, but i do see it in lsusb:

```
gail@gail-oldpos:~$ lsusb
Bus 002 Device 003: ID 04e8:507f Samsung Electronics Co., Ltd 
Bus 002 Device 002: ID 050d:705c Belkin Components 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
gail@gail-oldpos:~$
```

---

### Post by chewearn on 2007-03-11
Is it a USB mass storage class?

You can try this, and see if it shows up:
```
fdisk -l
```

---

### Post by lunaz on 2007-03-11
```

gail@gail-oldpos:~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9541    76638051   83  Linux
/dev/hda2            9542        9729     1510110    5  Extended
/dev/hda5            9542        9729     1510078+  82  Linux swap / Solaris
gail@gail-oldpos:~$

```

edit:
woohoo! [this](http://www.yepp.co.kr/support/support_file_down.jsp?pds_num=1658&seq_num=1) helped & now i can run it on ubuntu. :D

---

### Post by Alexthebest on 2007-03-25
> **lunaz said:**
> 
edit:
woohoo! [this](http://www.yepp.co.kr/support/support_file_down.jsp?pds_num=1658&seq_num=1) helped & now i can run it on ubuntu. :D

Hi, can you explain me how to use that file?
I've the same problem, I've got a Samsung Yp-T9J and I don't know how to configure it to use on Ubuntu.

Thank you ;)

---

### Post by Alexthebest on 2007-03-25
ok, now it works also with me :) 
I connected the yp-t9 to win-xp and I copied the 2 files of the firmware 1.60 in the root folder of the mp3 player. I disconnected it and switched on. It done a firmware upgrade during the boot, and now it works with ubuntu and also with windows 2k.

remember: use firmware 1.60 and NOT the newest 1.67, because 1.60 uses UMS as transfer protocol instead of MTP, and UMS works fine with Ubuntu.

bye!

---

### Post by lunaz on 2007-03-25
i'm glad it got fixed. i was gone all weekend :) if u need more help tho just let me know.

---

### Post by elektronaut on 2007-06-01
Look here for newer firmware versions: [http://www.anythingbutipod.com/forum/showthread.php?t=13486](http://www.anythingbutipod.com/forum/showthread.php?t=13486)

---

### Post by muadib on 2007-06-29
I wanted to add to this thread.

I'm using Ubuntu Feisty with default Ubuntu kernel version 2.6.15-26-386. I also tried connecting to the device using kernel version 2.6.15-26-386

The device version is Samsung YP-T9JBQB. My problem is that I don't have a working Windows  install to upgrade the firmware. Furthermore, I prefer not upgrading the firmware because it voids my warrantee.

I also tried using libmpt to connect to the device, but this was also unsuccessful. mtp-detect reported no devices:

# mtp-detect
No MTP devices.
No devices.

My libmtp version:

apt-cache show libmtp5
Package: libmtp5
Priority: optional
Section: libs
Installed-Size: 312
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Brandon Holtsclaw <imbrandon@kubuntu.org>
Architecture: i386
Source: libmtp
Version: 0.1.3-0ubuntu2
Replaces: libmtp-dev (<< 0.1.3-0ubuntu1)
Depends: udev, libc6 (>= 2.5-0ubuntu1), libusb-0.1-4 (>= 2:0.1.12)
Conflicts: libmtp-dev (<< 0.1.3-0ubuntu1), libmtp2
Filename: pool/main/libm/libmtp/libmtp5_0.1.3-0ubuntu2_i386.deb
Size: 92718
MD5sum: 298192cd3a55d52d8bc2dd1fe4f4e239
SHA1: e856047fc3d63677069d3bb1f93d718341263f1c
SHA256: 5b08f4f2d5a5225d1ecada6d704955d2bdf487da061cca78d055b19c12ec60a9
Description: Implementation of Microsoft's MTP
 libmtp is a implementation of Microsoft's Media Transfer Protocol (MTP)
 in the form of a library suitable primarily for POSIX compliant operating
 systems. We implement MTP Basic, the stuff proposed for standardization.
 .
 Homepage: [http://libmtp.sourceforge.net/](http://libmtp.sourceforge.net/)
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: kubuntu-desktop

When I typed lsusb as root, there was no indication that a Samsung Device was detected.

I checked dmesg and no usb mass storage device was detected, probably because the device uses the latest firmware that I read uses MTP and not UMS to connect.

The firmware on the device was version 1.67.

I'm bringing the unit back to the retailer as it doesn't work with my setup.

---

### Post by muadib on 2007-06-29
I am writing again to say that I have gotten some files onto this device but that I had to upgrade the mtplib version to 1.5.

I'm considering the firmware downgrade to go back to UMS.

---

### Post by muadib on 2007-06-29
Hello again,

Thank you to all of those that had contributed to this post. I was able to upgrade to firmware version 1.8 without any problems and now have my yp-t9 recognized by ubuntu as a mass storage device and it plays my ogg files perfectly.

I used the instructions found here:
[http://www.anythingbutipod.com/forum/showthread.php?t=13486](http://www.anythingbutipod.com/forum/showthread.php?t=13486)
and here:
[http://www.tty1.net/blog/2007-04-06-samsung-yp-t9_en.html](http://www.tty1.net/blog/2007-04-06-samsung-yp-t9_en.html)

The trick was to upgrade to libmtp version 1.5 to get the firmware files onto the device.

Thanks again,

Mathieu

---

