---
title: "[SOLVED] Need a new xorg for 8.10 with custom EDID?"
date: 2008-12-21
forum: Multimedia Software
---

### Post by matthekc on 2008-12-21
I have a geforce 440 go and a custom EDID this is my old xorg device section.

Section "Device"
    Identifier  "Videocard0"
    Driver      "nvidia"
    Option      "AddARGBGLXVisuals" "true"
    Option      "UseDisplayDevice" "DFP-0"
    Option      "CustomEDID" "DFP-0:/etc/X11/nvnew.raw"
EndSection

How do I make this work with the new xorg?

---

### Post by matthekc on 2008-12-21
This works!

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

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
	Option      "UseDisplayDevice" "DFP-0"
  	Option      "CustomEDID" "DFP-0:/etc/X11/nvnew.raw"
EndSection

---

### Post by hooby3dfx on 2008-12-30
i thought 8.10 doesnt support the nvidia binary driver and < geforce4.  how does this work?
i am in a similar situation.
thanks!

---

### Post by matthekc on 2009-01-09
uh when I get back to my sisters computer I'll look at it more glxinfo and gears showed rendering of 3d.

---

### Post by matthekc on 2009-01-17
I have a GeForce4 440 Go I'm using Nvidia driver version 96.  I Installed it through the restricted drivers manager.

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

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
	Option      "UseDisplayDevice" "DFP-0"
  	Option      "CustomEDID" "DFP-0:/etc/X11/nvnew.raw"
EndSection

Here is my xorg ignoring the custom edid which most people won't need.

---

