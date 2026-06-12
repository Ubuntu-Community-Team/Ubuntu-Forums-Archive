---
title: "install this driver wifi"
date: 2010-09-29
forum: Networking &amp; Wireless
---

### Post by homa2142 on 2010-09-29
how can i install this driver wifi packeg

---

### Post by chili555 on 2010-09-29
Here is what I read in the included *readme*:> Description:
=============
This is a linux device driver for Ralink RT2500USB b/g WLAN Card.Also, please see:> Compatibility:
===================
Testing has been done with LinEX kernel 2.6.9, Fedora Core 3.
You may encounter some rough edges when working with recent other Linux kernels branch.Here is my translation: This driver is old, old and old. It may not work with a kernel built in the 21st century. Well, OK, you are right; it _won't_ work.

The driver rt2500usb has been included in recent Ubuntu kernels for some time. I suggest we troubleshoot your system to see why the built-in driver isn't working. First, let's do some diagnostics. Please open Applications > Accessories > Terminal and run these commands. Post the outcome and we'll have a better idea how to proceed:```
lsusb
lsmod | grep rt2
iwconfig
```Thanks.

---

