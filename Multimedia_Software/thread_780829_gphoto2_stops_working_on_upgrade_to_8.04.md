---
title: "gphoto2 stops working on upgrade to 8.04"
date: 2008-05-03
forum: Multimedia Software
---

### Post by notmyidea on 2008-05-03
Everything was working fine before I upgraded to 8.04

I was using gtkam and gphoto2.

Now I get:

An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

in gtkam.

dmesg has a ton of these messages:
[25701.981734] usb 8-1: usbfs: USBDEVFS_CONTROL failed cmd gtkam rqt 64 rq 4 len 115 ret -110

lsusb reports the camera correctly:
Bus 008 Device 007: ID 04a9:30ee Canon, Inc. EOS 350D

My camera is an Canon EOS350D

Any suggestions as to what changed in 8.04??

Thanks, Jason

---

### Post by heen on 2008-05-18
I have the same problem after update :(

It's some permissions mess I guess. As workaround I execute gphoto2 as super user and it works.

---

