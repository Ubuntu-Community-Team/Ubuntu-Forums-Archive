---
title: "Twinview nVidia problems, dual flat panels"
date: 2008-12-07
forum: Multimedia Software
---

### Post by tsnax4 on 2008-12-07
Hi,

I have researched this endlessly and tried countless xorg configurations but I still cant get my dual monitor set up to work properly (i dont want cloned screens). I have the nVidia Corporation NV20 [GeForce3 Ti 200] video card, and i have read that this may not be able to support 2 monitors but i have video on both my samsung tv that i have connected throught the PC-in and my AOC flat panel monitor.

The samsung is connected through the DVI port via vga-dvi adapter, and the AOC is connected to the vga. The display manager for ibex doesnt recognize the samsung yet it still displays video while the nVidia settings manager recognises both but wont allow me to apply twinview (error: TwinView cannot be enabled with this combination of display devices).

So I guess I am just asking if anyone can help me with this, or has had similar problems and found an issue. I read the twinview tutorial and just couldnt get it to work.

Xorg.conf - 
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
EndSection
Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

---

