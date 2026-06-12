---
title: "Sansa Clip stop auto mounting after upgrade to Jaunty"
date: 2009-05-05
forum: Multimedia Software
---

### Post by Kreuger on 2009-05-05
Hey people. I have a 4gb Sansa Clip that used to work fine in Intrepid but ever since upgrading to Jaunty the device does not auto mount. In fact, I can't get it to mount at all. It shows up when I use lsusb:

> kreuger@kreuger-desktop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 013: ID 054c:0268 Sony Corp. Batoh Device
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 001 Device 003: ID 13b1:0020 Linksys WUSB54GC 802.11g Adapter [ralink rt73]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 004: ID 0781:7432 SanDisk Corp. Sansa Clip (mtp)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

But not if I run fdisk -l

> kreuger@kreuger-desktop:~$ sudo fdisk -l
[sudo] password for kreuger: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000db906

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30024   241167748+  83  Linux
/dev/sda2           30025       30401     3028252+   5  Extended
/dev/sda5           30025       30401     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6dd88bbf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14945   120045681   83  Linux
 Sda is my internal and Sdb is my external. The Sansa has Fat32 (I believe) file system. 

It shows up no problem in the [Gnome Device Manager]("http://img56.imageshack.us/my.php?image=mp3gnomedevices.png"), as well as [Hard Info]("http://img518.imageshack.us/my.php?image=mp3hardinfoq.png").

---

### Post by Kreuger on 2009-05-13
Anyone?

---

### Post by morpheus.pv on 2009-05-15
hi, i have same problem with my rockboxed sansa e270 and SDHCcard inside...
last dmesg message was: *usb-storage: waiting for device to settle before scanning*

there are some various bugs in newest libgphoto (jaunty) deb package

look for a solution on launchpad or try a patch which work for my sansa e200 series
[http://ubuntuforums.org/showpost.php?p=7269614&postcount=211](http://ubuntuforums.org/showpost.php?p=7269614&postcount=211)

---

### Post by morpheus.pv on 2009-05-15
[http://ubuntuforums.org/showpost.php?p=7204940&postcount=4](http://ubuntuforums.org/showpost.php?p=7204940&postcount=4)

---

### Post by Kreuger on 2009-05-21
Neither solution helped. I already have the latest gphoto2 and the other method did nothing.

---

### Post by Chronon on 2009-05-22
I edited /usr/share/hal/fdi/preprobe/10osvendor/20-libgphoto2.fdi to remove all references to my DAPs.  It's a dirty hack, I know, but I only use MSC mode with my devices.

I got the idea from here: [https://bugs.launchpad.net/ubuntu/+bug/345916](https://bugs.launchpad.net/ubuntu/+bug/345916)

It has worked on a Sansa e280 and a Gigabeat F40, neither would mount previously (though I had no such issues with Intrepid).

---

### Post by Kreuger on 2009-06-03
Thanks but it made no difference.

---

### Post by rdmike on 2009-06-03
Neither the patch nor suggested edit worked for me either (sansa e240).

---

### Post by Kreuger on 2009-06-17
Well mine has randomly started working again. I plugged it in a few days ago just to charge it, and I saw it come up on the screen.

---

### Post by icheyne on 2009-06-20
I put some Sansa Clip instructions up [here]("https://help.ubuntu.com/community/SansaClip")

---

### Post by Kreuger on 2009-06-23
> **icheyne said:**
> I put some Sansa Clip instructions up [here]("https://help.ubuntu.com/community/SansaClip")

Well as far as I can remember, mine worked out of the box but thanks anyways

---

### Post by Michael Schmidt on 2009-07-02
Mr. Cheyne, thanks for the helpful instructions.  I note the current firmware is 01.01.32a and it is supposed to have improved .ogg support.  Just ran the firmware update (on my wife's Windows machine), set USB to MSC, and uploaded some .ogg files.  Sound great!  btw, another advantage of MSC mode is that some shelf stereo systems have a USB port now but only recognize MSC mode (need .wma or .mp3 file format, though).

---

