---
title: "Why are devices in Lusb not available to applications?"
date: 2011-11-18
forum: Multimedia Software
---

### Post by wickedpenguinbox on 2011-11-18
HI All,

I am fairly new to Ubuntu and am currently running 11.10.

I am having a few issues with getting some usb devices to work correctly. 

First off, my PS3 Eye camera was working in cheese webcam applications, but now only shows a black screen.

If I run lsusb, the device is listed there as below so I assume it should be ok.

Bus 002 Device 004: ID 1415:2000 Nam Tai E&E Products Ltd. or OmniVision Technologies, Inc. Sony Playstation Eye

I really dont know how to troubleshoot this and I was wondering if someone might be able to point me in the right direction?

Thanks,

---

### Post by dabl on 2011-11-18
I can't tell if this is identical to yours:  [http://oftw.wikidot.com/install-ps3-eye-camera-in-ubuntu](http://oftw.wikidot.com/install-ps3-eye-camera-in-ubuntu)

If the USB ID number is the same, then the patch information should be right.

---

### Post by wickedpenguinbox on 2011-11-18
> **dabl said:**
> I can't tell if this is identical to yours:  [http://oftw.wikidot.com/install-ps3-eye-camera-in-ubuntu](http://oftw.wikidot.com/install-ps3-eye-camera-in-ubuntu)

If the USB ID number is the same, then the patch information should be right.

Thanks, I must be doing something wrong, because i get this below error..

Any idea?

~$ sudo patch -p1 < ps3eyeMT-2.6.31-10-generic.patch
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -Naur linux-source-2.6.31/drivers/media/video/gspca/ov534.c linux-ps3eyeMT/drivers/media/video/gspca/ov534.c
|--- linux-source-2.6.31/drivers/media/video/gspca/ov534.c    2009-09-10 00:13:59.000000000 +0200
|+++ linux-ps3eyeMT/drivers/media/video/gspca/ov534.c    2009-09-21 19:10:40.000000000 +0200
--------------------------
File to patch:

---

