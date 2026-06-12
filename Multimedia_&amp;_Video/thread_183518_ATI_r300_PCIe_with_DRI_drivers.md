---
title: "ATI r300 PCIe with DRI drivers"
date: 2006-05-28
forum: Multimedia &amp; Video
---

### Post by mym on 2006-05-28
Is there anybody who manages to make DRI working with a r300 (or greater) ATI PCIe (PCI express) card ?
I have a X700 mobility on my ACER Aspire 1694WLMI and I can't get the r300 OpenSource drivers working.
On [the official website](http://r300.sourceforge.net/R300.php), they say PCIe doesn't work currently, however this page seems outdated.
I've tried [the last snapshots](http://dri.freedesktop.org/snapshots/) by getting the common and r300 packages, doing a "sh install.sh" and specifying good Xorg directories, but when I launched Xorg, it freezed my system (I have Ubuntu Dapper).

I don't want to use source/CVS DRI version as I don't want to compile Mesa and Xorg by hand.

Please help.

---

### Post by mym on 2006-06-06
Using the XGL repository ([http://xgl.compiz.info)](http://xgl.compiz.info)), I have more recent mesa/dri drivers which provide a partial 3D rendering.
I had to remove xorg-driver-fglrx package to make 3D working (maybe cause of the /usr/lib/libGL/so.1.2 shared file...).

Perfs are far worse than with fglrx drivers.
As example, with Neverball, I have around 160 FPS with fglrx but 40 with libre drivers... but as they said, the drivers are very experimental.

---

