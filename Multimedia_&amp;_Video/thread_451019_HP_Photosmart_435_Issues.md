---
title: "HP Photosmart 435 Issues"
date: 2007-05-21
forum: Multimedia &amp; Video
---

### Post by dystrust on 2007-05-21
I've been trying to connect my friend's HP Photosmart 435 to my laptop and I haven't had any luck.  If I try to connect it as a mass storage device, the disk is empty; which I know to not be true.  If I try to connect it using PTP I get the following error message:

"An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device"

I have heard of others getting this camera to work on Ubuntu, so I doubt that this is a compatibility issue though it may be.  Can anyone offer any advice regarding what I could be doing differently or things I could check?

Thanks,
-Dave

---

### Post by mitch.c on 2007-05-22
> **dystrust said:**
> I've been trying to connect my friend's HP Photosmart 435 to my laptop and I haven't had any luck.  If I try to connect it as a mass storage device, the disk is empty; which I know to not be true.  If I try to connect it using PTP I get the following error message:

"An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device"
It could be a couple of things. I had a problem with a Photosmart 618 after I upgraded from Dapper to Edgy that manifested itself with the same error. I found this [bug report]("https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/103439"), and after changing /etc/udev/rules.d/45-libgphoto2.rules as described, the problem was resolved.
```
#BUS!="usb*", GOTO="libgphoto2_rules_end"
SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"
```
You also need to make sure a line exists for your camera where idVendor and idProduct match the output from lsusb:
```
SYSFS{idVendor}=="0553", SYSFS{idProduct}=="0202", MODE="0660", GROUP="plugdev"
```
It looks like this bug may affect Feisty as well.

Good Luck
-- 
Mitch

---

