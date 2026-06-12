---
title: "EPIA-M VIA Unichrome Graphics"
date: 2005-11-20
forum: Multimedia &amp; Video
---

### Post by samokk on 2005-11-20
I tried to install Linux on a EPIA-M 10000 MotherBoard. This board has a CLE266 graphics chipset (Unichrome). 

The installer automatically configured Xorg to use the "via" driver, which is what it's supposed to detect :

[INDENT] This driver for the X.Org X server (see xserver-xorg for a further description)
 provides support for Via/S3 CLE266/KM400/K8M800/UniChrome cards, which are
 frequently found in low-form-factor Via motherboards, and in some laptops[/INDENT].

However, the screen turns black when Xorg starts. I tried several resolutions, with no success.
The only way I got Xorg to work is by using the "vesa" driver, which is, of course, unaccelerated.

**So, is this board supposed to work ? If it is, should I report a bug ?**

Another thing that does not work is the framebuffer. I had to disable it during setup. Mandriva setup works fine with framebuffer, so I guess there is some kernel patch available somewhere to fix this issue. Should I bug report about this too ?
Thanks,
Sami Dalouche

---

