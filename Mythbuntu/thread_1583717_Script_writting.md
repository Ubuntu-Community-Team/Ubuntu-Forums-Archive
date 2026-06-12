---
title: "Script writting"
date: 2010-09-28
forum: Mythbuntu
---

### Post by jimp180 on 2010-09-28
I need to write a script to name my usb tuners to use in my udev rules but I have no idea how to write a script. According to ["Writing udev rules"]("http://www.reactivated.net/writing_udev_rules.html#external-naming") I can use an external program to name my devices so I would like to write a script that can use lsusb to name my wintv usb2 devices.

According to lsusb my usb tuners are:
```
Bus 001 Device 005: ID 2040:2900 Hauppauge
Bus 001 Device 003: ID 2040:2400 Hauppauge
``` I would like to use the ID numbers to name them.

---

### Post by ian dobson on 2010-09-28
Hi,

maybe have a look at this thread [http://ubuntuforums.org/showthread.php?t=753434&highlight=udev+static](http://ubuntuforums.org/showthread.php?t=753434&highlight=udev+static)

Regards
Ian Dobson

---

