---
title: "BCM4312 trouble in Meerkat!"
date: 2010-12-01
forum: Networking &amp; Wireless
---

### Post by SyphonX67 on 2010-12-01
Hi, I have a Broadcom BCM4312 on an HP Pavillion Dv2945se. I'm running 10.10 64 bit, and the wireless card used to work. Now it has just stopped working and it has not worked since. I installed Ubuntu 9.10, and the card worked fine. Then upgraded to 10.04, again successful. As soon as I update to 10.10 however, no luck. This is quite frustrating. I enable wireless, but the light on my wifi card is still red, meaning the card is not working. In the proprietary drivers area, it says that the STA (and B43) drivers are working fine, the light is green and that they are currently in use, when they clearly are not. If anyone has any suggestions to a noob like me, please.

---

### Post by uncaspi on 2010-12-02
Goto Broadcom home site and and download this file::

hybrid-portsrc_x86-32_v5.60.246.6.tar.gz


Unpack it and follow the instructions in the README.txt file.
This is the latest STA driver and  it should work. 
Type this command sudo depmod -a  after make install and before sudo modprobe wl

---

