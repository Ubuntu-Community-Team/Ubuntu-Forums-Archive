---
title: "Digital camera help"
date: 2007-03-24
forum: Multimedia &amp; Video
---

### Post by RDUBBALO on 2007-03-24
When I try to upload my pictures from my camera which is a Kodak easyshare c300 I turn it on and hit import then I get this error that says  An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device. I restarted the computer and I dont know what the program it is that is running. Any help or ideas?

---

### Post by rkathey on 2007-03-26
This worked for me

[https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250]("https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250")

From that URL

replace
BUS!="usb*", GOTO="libgphoto2_rules_end"

in
/etc/udev/rules.d/45-libgphoto2.rules

with
SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"

---

### Post by beefcurry on 2007-03-30
Great! That worked for me as well!

---

### Post by RDUBBALO on 2007-03-30
sudo /etc/udev/rules.d/45-libgphoto2.rules
sudo: /etc/udev/rules.d/45-libgphoto2.rules: command not found

I dont know it says command not found I reinstalled the package and it still is not working

---

### Post by yabbadabbadont on 2007-03-30
> **RDUBBALO said:**
> sudo /etc/udev/rules.d/45-libgphoto2.rules
sudo: /etc/udev/rules.d/45-libgphoto2.rules: command not found

I dont know it says command not found I reinstalled the package and it still is not working

sudo gedit /etc/udev/rules.d/45-libgphoto2.rules

---

### Post by RDUBBALO on 2007-03-31
oh how dumb i knew that. Thanks so much it worked perfect.

---

