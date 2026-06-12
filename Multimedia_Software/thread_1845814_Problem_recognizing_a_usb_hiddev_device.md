---
title: "Problem recognizing a usb hiddev device"
date: 2011-09-17
forum: Multimedia Software
---

### Post by jpmh on 2011-09-17
I have a planar 2230 touch screen monitor - lshal and lsusb show it as there.  It appears to be device 0408 and 3001.  I have created a file:/etc/udev/init.d/99-local-rules with the entry:
SUBSYSTEM=="usb", ATTRS{idVendor}=="0408",  ATTRS{idProduct}=="3001", SYMLINK+="Planar"


when I re-boot and look at /dev/usb I still only see  hiddev0, hiddev1 and hiddev2 .  If I unplug the monitor usb cable then I do not have hiddev2 so I know it is being seen. 

What am I missing here, what else do I need to set to cause this symlink t be set

---

