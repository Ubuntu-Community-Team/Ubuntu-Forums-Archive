---
title: "usb-modeswitch: missing /dev/gsmmodem symlink"
date: 2011-11-07
forum: Networking &amp; Wireless
---

### Post by monoab314 on 2011-11-07
Hi all

Since Maverick, the usb-modeswitch package created a symlink (/dev/gsmmodem) to the correct /dev/ttyUSB* device to allow easy comms with flip flop USB modems.  This no longer happens on my Oneiric install.  I am using identical hardware.

The package still does the "flipping" of the device correctly but it or udev fails to create the symlink.  Is anyone else experiencing this?

---

