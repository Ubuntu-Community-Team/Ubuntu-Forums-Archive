---
title: "Intel Core Processor Integrated Graphics Controller on Dell Latitude e5510"
date: 2010-08-12
forum: Multimedia Software
---

### Post by meglioilmarco on 2010-08-12
Hi all

I have some trouble with my new laptop. The video card does not works very good. I am not able to enable intel driver so video card works only with vesa driver and 3d acceleration doesn't working.

Some information:

**lspci**
```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
```

**cat /etc/X11/xorg.conf**
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device" 
EndSection
```

**glxinfo | grep render**
```
direct rendering: Yes
OpenGL renderer string: Software Rasterizer
```

Command **glxgears** its ok but if I try to play with SuperTuxKart for example I cant cause its jerky.

Any ideas??

---

### Post by fidlej on 2010-11-24
Have you found a solution?
My situation is exactly the same. I also have Dell E5510.

Is there a bug report for it?

---

