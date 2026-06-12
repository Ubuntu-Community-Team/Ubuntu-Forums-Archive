---
title: "Weird ATi Crash Problem"
date: 2009-08-01
forum: Multimedia Software
---

### Post by constchar* on 2009-08-01
I've been doing some searching around and can't seem to find an answer to this weird problem I've been having.

First up my setup is Ubuntu 9.04 x86_64 (installed on an Ext4 partition) with an ATi Radeon 4870.
I installed the Catalyst 9.7 drivers and for the most part everything works as expected and it works just great with Compiz.. well for the most part.
Shortly afterward I started getting this weird problem where after 2 bootups the screen would remain black and the animated loading circle cursor would flicker and then the entire system would freeze and I would never see the login screen.
The only way to fix it is to uninstall the ATi driver and do a dpkg-reconfigure on xserver-xorg, reboot and then reinstall the ATi driver but then after 2 bootups the problem reappears.

Also on a side note whenever I start Totem or Wine the screen flickers heavily and the computer slows down until the screen finishes flickering.
This is sort of unrelated to the main topic (about the crash) but if you happen to know why it does this then I'd appreciate it if you could mention it.

Thanks for everything, and if you need any additional details then let me know.

---

