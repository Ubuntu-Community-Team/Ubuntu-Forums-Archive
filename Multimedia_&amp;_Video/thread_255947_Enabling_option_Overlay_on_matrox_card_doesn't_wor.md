---
title: "Enabling option Overlay on matrox card doesn't work"
date: 2006-09-12
forum: Multimedia &amp; Video
---

### Post by thierry_therealone on 2006-09-12
I have Ubuntu 6.06 running on a box with a Matrox G450 graphic card.

If I try to enable the Overlay option (no dual screen) of the mga driver:

Option "Overlay" "8,24"

X doesn't start and I get the following error in Xorg.0.log:

(II) Loading sub module "xf8_32bpp"
(II) LoadModule: "xf8_32bpp"
(II) Loading /usr/lib/xorg/modules/libxf8_32bpp.so
dlopen: /usr/lib/xorg/modules/libxf8_32bpp.so: undefined symbol: mfbUnrealizeFont
(EE) Failed to load /usr/lib/xorg/modules/libxf8_32bpp.so
(II) UnloadModule: "xf8_32bpp"
(EE) MGA: Failed to load module "xf8_32bpp" (loader failed, 7)


I tried also the beta release of Ubuntu 6.10, but got the same result. Any ideas?

Attached is my Xorg.0.log file

---

