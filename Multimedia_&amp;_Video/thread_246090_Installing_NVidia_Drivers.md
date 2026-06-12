---
title: "Installing NVidia Drivers"
date: 2006-08-28
forum: Multimedia &amp; Video
---

### Post by suprak on 2006-08-28
I'm new to linux (ubuntu) and wanted some help on how to install video drivers for my ASUS v9400-X (NVidia GForce MX 4000 powered) video card.

Right now everything lags alot even when I try to do something as simple as drag a window around...

I tried following someone elses instructions, but that just corrupted my xorg.conf and I had to revert to a backup.

Any tutorials up or anything? Because currently I don't have direct rending activated, and glxgears produces
> Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual


even though it did run before I attempted to install the NVidia drivers.

Perhaps of interest:
> suprak@suprak-linux:~$ lspci -v | grep VGA
0000:01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] (rev c1) (prog-if 00 [VGA])


**Edit**:

:KS [http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html) :KS solved my problems, thanks to Alberto!

---

