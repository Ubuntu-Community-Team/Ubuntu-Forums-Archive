---
title: "[HELP] Screen Resolution"
date: 2006-07-25
forum: Multimedia &amp; Video
---

### Post by MarianoArg on 2006-07-25
Hello,
I have a problem, maybe you know the solution.

In my work I use a regular PC.I'm not sure of what's inside, but it seems that it has a motherboard with via P4M800CE chipset.

I would like to to install specific drivers for this chipset but i can't. I need to do this so i could use a 1280x1024 resolution. Right now i have the xorg.conf setted with "vesa" drivers (1024 x 768 max).
If I change it to "via", X doesn't work.

the log:
(II) VIA: driver for VIA chipsets: CLE266, KM400/KN400, K8M800,
PM800/PM880/CN400
(II) Primary Device is: PCI 01:00:0
(EE) No devices detected.

Fatal server error:
no screens found


Any ideas?
Tnx in advance

---

### Post by tseliot on 2006-07-25
Try this:
```
apt-get install xserver-xorg-driver-via
```
then
```
dpkg-reconfigure xserver-xorg
```
and select your Via card (and driver)

If that doesn't work you can set the driver to "vesa" and follow this guide to set the resolution you need:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)

---

