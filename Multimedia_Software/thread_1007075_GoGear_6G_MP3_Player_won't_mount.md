---
title: "GoGear 6G MP3 Player won't mount"
date: 2008-12-10
forum: Multimedia Software
---

### Post by AnLGP on 2008-12-10
Here are some outputs:

steve@gnu-linux:~$ lsusb
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 04fc:0003 Sunplus Technology Co., Ltd CM1092 Optical Scroller Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
steve@gnu-linux:~$ sudo fdisk -l

Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x52df0fb1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7476    60050938+  83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3647784d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14714   118190173+  83  Linux
/dev/sdb2           14715       30401   126005827+  83  Linux

~~~~~~~~~~~~~~~~~~~

I tried it with Amarok and VLC ..  and Gnomad2 but I've got nothin'.  Is this one of those things where I just might have to wait?

I can't quite remember if I had to install something for it on 'doze or not.  Thanks.

Philips GoGear Jukebox HDD1630 - Model.

---

### Post by andrewoftheelves on 2009-07-14
Hello, I have a philips gogear hdd1630 and I put rockbox on it.
The way that I get it to mount is by putting it in service mode.
to do this (when the player is already on) hold the power and plus volume switch to soft reset the device. When the device resets immediatly hold down the volume minus button. Hold it down until a screen depicting an mp3 player and a computer comes up. Now you can mount the device. Without rockbox on the device I doubt that you can just copy and paste music on it, but you should try [http://opengogear.sarovar.org/](http://opengogear.sarovar.org/)
good luck.

---

