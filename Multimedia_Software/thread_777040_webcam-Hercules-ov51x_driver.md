---
title: "webcam-Hercules-ov51x driver"
date: 2008-05-01
forum: Multimedia Software
---

### Post by ubu-lemon on 2008-05-01
i bought an extern webcam, Hercules silver classic (i also have an intern one but there seems to be no driver available), found here on the forum a page with a list of webcams
([http://alpha.dyndns.org/ov511/cameras.html](http://alpha.dyndns.org/ov511/cameras.html))


found the driver suggested (ov51x), but i don't know what to do (being an enthousiastic but unskilled ubuntu user)

also it says that i should remove the ov511 driver's module before installing the ov51x
([http://alpha.dyndns.org/ov511/download.html#ov51x](http://alpha.dyndns.org/ov511/download.html#ov51x))

and there are three options on this page, which one should i choose (and why?)

thanks in advance !

---

### Post by qgfreire on 2008-05-02
I hava similar problem in ubuntu hardy.
I tried module-assistant (selected ov511) and when in build:
 
 Building OVCam drivers for 2.6 kernel.                                 &#8593;
 &#9474; /usr/bin/make -C /usr/src/linux SUBDIRS=/usr/src/modules/ov511 modules     &#9618;
 &#9474; make[3]: Entering directory `/usr/src/linux-headers-2.6.24-16-386'         &#9618;
 &#9474;   CC [M]  /usr/src/modules/ov511/ov511_core.o                              &#9618;
 &#9474; /usr/src/modules/ov511/ov511_core.c:29:26: error: linux/config.h: No       &#9618;
 &#9474; such file or directory                            


my webcam (usbview):
USB Camera
Manufacturer: OmniVision Technologies, Inc.
Speed: 12Mb/s (full)
USB Version:  1.10
Device Class: 00(>ifc )
Device Subclass: 00
Device Protocol: 00
Maximum Default Endpoint Size: 8
Number of Configurations: 1
Vendor Id: 05a9
Product Id: 0518
Revision Number:  1.01

Config Number: 1
	Number of Interfaces: 1


lsusb : Bus 004 Device 005: ID 05a9:0518 OmniVision Technologies, Inc. OV518 WebCam

uname -r :2.6.24-16-386



Thank you in advance

PS: Perhaps you can trie!

---

### Post by ubu-lemon on 2008-05-15
[-o<

---

