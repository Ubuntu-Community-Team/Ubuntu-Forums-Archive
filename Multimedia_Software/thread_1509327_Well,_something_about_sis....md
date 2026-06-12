---
title: "Well, something about sis..."
date: 2010-06-14
forum: Multimedia Software
---

### Post by skies457 on 2010-06-14
Using lucid on sis 760.
It seems that sis driver from [http://www.winischhofer.net/](http://www.winischhofer.net/) has integrated into lucid, for I can find direct rendering enabled in glxinfo. But what I would like to know is how to enable Hardware Acceleration in OpenGL instead of default Software Rasterizer.

Here is the result of glxinfo | grep render
```
direct rendering: Yes
OpenGL renderer string: Software Rasterizer
```

and the result of lspci | grep AGP
```
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
```

Any suggestions?

thx.

---

