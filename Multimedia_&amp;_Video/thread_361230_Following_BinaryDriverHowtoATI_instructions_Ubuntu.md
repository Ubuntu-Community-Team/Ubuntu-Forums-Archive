---
title: "Following BinaryDriverHowto/ATI instructions Ubuntu wont start"
date: 2007-02-14
forum: Multimedia &amp; Video
---

### Post by paulLeeds on 2007-02-14
I am trying to configure my graphics card an ASUS EAX1950Pro. I've tried installing both the fglrx drivers and the open source drivers using the guides on this site. But in both cases after I edit the xorg.conf file and change Driver to fglrx or to ati the system hangs at boot up.

This is what the relevant section of my xorg.conf file looks like and the problem occurs when I change "vesa" for something else.

Section "Device"
Identifier   "ATI Technologies, Inc. ATI Default Card"
Driver       "vesa"
BusID       "PCI:1:0:0"
EndSection


Any help with this is much appreciated.

---

