---
title: "Samsung S3 MP3 player in Ubuntu"
date: 2009-02-10
forum: Multimedia Software
---

### Post by tomcat2007 on 2009-02-10
I recently purchased a Samsung S3 as a gift for my wife and after a day of googling was able to get it working on an XP partition, now I'm trying to get it working in Ubuntu.  I have identified the drivers used by XP, they are part of WMP11; \windows\system32\drivers\spdusb.sys & \windows\system32\drivers\wudfrd.sys. 

lsusb -v indicates that the Ubuntu sees it ->

Bus 001 Device 002: ID 04e8:5091 Samsung Electronics Co., Ltd 

But I don't know how to use the drivers to get Ubuntu to treat it like a USB drive.  Can NDISWRAPPER be used with these drivers and if so, how would I "wrap" them?

Any assistance is greatly appreciated.

Laptop 1:  HP Pavilion dv9000z running Ubuntu Hardy
Laptop 2:  Acer Aspire 3680 running Ubuntu Intrepid

---

### Post by whaevr on 2009-02-10
So are you not able to mount the device? If Ubuntu detects it, it should mount it..

Are you trying to add music to it through a media player?

run "sudo fdisk -l" if you can't mount it and paste the output here.

---

### Post by tomcat2007 on 2009-02-10
> **whaevr said:**
> So are you not able to mount the device? If Ubuntu detects it, it should mount it..No, it does not mount, apparently this is a problem that has plagued a number of people who have purchased this model.

> Are you trying to add music to it through a media player?No, I'm wanting to access it like a USB storage device, that is how my wife will be adding music to it; dragging and dropping MP3 files into the appropriate folder on the S3.

> run "sudo fdisk -l" if you can't mount it and paste the output here.

[i]tomcat@tomcat1:~$ sudo fdisk -l
[sudo] password for tomcat: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001e450

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1020     8193118+   7  HPFS/NTFS
/dev/sda2            1021        3060    16386300   83  Linux
/dev/sda3            4973       19457   116350762+  83  Linux
/dev/sda4            3061        4972    15358140   83  Linux

Partition table entries are not in disk order[/i]

The four partitions above represent an XP partition, a non-gaming Ubuntu partition, a gaming Ubuntu partition, and a data partition. 

Is there anything else I can do to provide more useful information?

---

### Post by whaevr on 2009-02-10
Hmm I'm assuming you had the device plugged in when you ran the command..?

---

### Post by tomcat2007 on 2009-02-10
> **whaevr said:**
> Hmm I'm assuming you had the device plugged in when you ran the command..?Yep :-)

---

### Post by whaevr on 2009-02-10
Alright well...it appears someone got it to work in this [thread](http://www.anythingbutipod.com/forum/showthread.php?t=24737)

Install those packages from synaptic, because there are probably newer versions out by now.

See if that works.

Or check out this [thread](http://ubuntuforums.org/showthread.php?t=877862)

---

### Post by impulse101 on 2009-09-11
I know it may seem a bit late to post this, but I was just trying to get it working myself, and could find nothing to help me on the net.

I use exaile, and i was able to find a plugin through exaile called** MTP device manager**.
Unfortunately, when I try and use it I get an error saying *"Couldn't connect to the MTP device, wait a few seconds or reconnect the device, then try again."* 

Not sure if this will help anyone.. but it might be worth looking into :)

Depends: 
libmtp: [http://libmtp.sourceforge.net/](http://libmtp.sourceforge.net/) 
pymtp: [http://nick125.com/projects/pymtp/](http://nick125.com/projects/pymtp/)

---

