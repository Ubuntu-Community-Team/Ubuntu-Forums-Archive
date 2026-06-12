---
title: "Generic Allwinner A31s tablet android 4.04 - can't get usb debugging (adb)"
date: 2015-02-27
forum: Mobile Technology Discussions (CLOSED)
---

### Post by aspidistra on 2015-02-27
lsusb gives me :

Bus 002 Device 003: ID 1f3a:1000  

so I update /etc/udev/rules.d/51-android.rules    to be

why or what is that file specifically "51-android-rules" - some sites say '99-android-rules'

SUBSYSTEM=="usb", ATTR{idVendor}=="1f3a", ATTR{idProduct}=="1000", MODE="0600", OWNER="dan"



then I update

.android/adb_usb.ini


to contain
0x1f3a

as instructed

adb devices  (command)
List of devices attached 

blank - nothing

could there be other requirements apart from adb

---

