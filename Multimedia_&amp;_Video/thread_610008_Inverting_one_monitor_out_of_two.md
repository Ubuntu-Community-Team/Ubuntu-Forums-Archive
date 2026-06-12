---
title: "Inverting one monitor out of two?"
date: 2007-11-11
forum: Multimedia &amp; Video
---

### Post by MattK358 on 2007-11-11
I'm running an nVidia 7600GS with the nVidia proprietary driver under a clean install of Ubuntu 7.10. The installation went fine, first boot it detected the card and I granted it permission to install the driver, all went perfect. In fact it all works fine, even the dual monitor support. Problem is, my second monitor is an NEC 1760V LCD, suspended upside down from a metal frame. The Windows version of the nVidia Control Panel allows me to vertically invert the monitor to compensate with no problems, however I cannot find a way to make this work in linux. I've enabled RandRRotation in xorg.conf, and xrandr works, but I can't find a way to confine its effects to only one of the screens, plus having to manually correct it all the time is irritating. Anybody have any ideas how I can make this setup work?

Thank,
Matt

---

### Post by Jovec on 2007-11-11
Might be out of luck:

[http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/README/chapter-17.html](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/README/chapter-17.html)

*TwinView and rotation can be used together, but rotation affects the entire desktop. This means that the same rotation setting will apply to both display devices in a TwinView pair. Note also that the TwinViewOrientation option applies before rotation does. For example, if you have two screens side-by-side and you want to rotate them, you should set TwinViewOrientation to Above or Below.*

You could try separate X screens instead of twinview, but 3d accel (and desktop effects) will be limited to only one monitor/screen.

---

