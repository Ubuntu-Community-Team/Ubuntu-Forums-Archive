---
title: "Failed to initialize DMA!"
date: 2005-11-19
forum: Multimedia &amp; Video
---

### Post by cabbage on 2005-11-19
Dear all,

I would like to get DRI working with my Breezy system running Gnome. Unfortunately  I'm getting the following error in Xorg.0.log:

    (EE) MGA(0): [drm] Failed to initialize DMA! (-1007)

The hardware is a Matrox G200 card running in an Asus P2B motherboard (intel chipset).

I get the following in messages:

> Linux agpgart interface v0.101 (c) Dave Jones
agpgart: Detected an Intel 440BX Chipset.
agpgart: AGP aperture is 64M @ 0xe4000000
[drm] Initialized drm 1.0.1 20051102
[drm] Initialized mga 3.2.1 20051102 on minor 0: Matrox Graphics, Inc. MGA G200 AGP
agpgart: Found an AGP 1.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode

I get this error using the drivers supplied with Breezy, and also using the latest ones from Matrox and dri.freedesktop.org.

I've attached the full Xorg.0.log for info.

Any help or advice would be gratefully appreciated.


Regards,

Paul.

---

### Post by cabbage on 2005-11-21
:) I got it working. Rather than using the latest snapshot from the dri web site, I went back through the archives until I got one that compiled OK. Ended up using 20050404 and DRI is enabled! (Also then didn't need to upgrade Xorg as recommended on the site.)

Hope this helps other out there...

---

