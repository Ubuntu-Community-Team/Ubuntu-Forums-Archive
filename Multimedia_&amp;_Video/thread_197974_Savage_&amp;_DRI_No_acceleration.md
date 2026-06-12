---
title: "Savage &amp; DRI: No acceleration"
date: 2006-06-16
forum: Multimedia &amp; Video
---

### Post by polynom on 2006-06-16
Hi!

I'm using a S3 ProSavageDDR on Kubuntu Dapper. While DRI is basically working (according to *glxinfo*), it looks like I get no 3D acceleration in OpenGL based applications. Ppracer (formerly tuxracer) runs at 0.3 FPS, Cube is even slower. 
Maybe somebody knows what's going wrong here? Thanks in advance!

My xorg.conf:
```

Section "Files"
    FontPath 	"/usr/share/X11/fonts/misc"
    FontPath 	"/usr/share/X11/fonts/100dpi:unscaled"
    FontPath 	"/usr/share/X11/fonts/75dpi:unscaled"
    FontPath 	"/usr/share/X11/fonts/Type1"
    FontPath 	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath 	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
    FontPath 	"/usr/local/share/fonts"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbVariant"	"nodeadkeys"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
	Driver		"savage"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
	Monitor		"LCD"
	DefaultDepth	16
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480" "320x240"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480" "320x240"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480" "320x240"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480" "320x240"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection


```

---

### Post by polynom on 2006-06-17
Hmm, nobody?
Is there someone who has got the same chip and **does** get 3d acceleration?

---

### Post by sean12345 on 2006-07-07
I have.

 "glxinfo | grep direct" says that I have direct rendering.  

Right now I am stuck at 640x480 resolution though.  When I try to start an xgl session it crashes with an error that says it "can't find the monitor".

I have a S3 Inc. 86C270-294 Savage/IX-MV video card.

Otherwise my xorg.conf is identical to yours.

---

### Post by hwert on 2006-07-08
Try setting:

Option "BusType" "PCI"

In your,

# /etc/X11/xorg.conf (xorg X Window System server configuration file)

Section "Device"
	Identifier	"S3 Inc. 86C270-294 Savage/IX-MV"
	Driver		"savage"
	BusID		"PCI:1:0:0"
	Option		"BusType"	"PCI"
	Option		"DmaMode"	"none"
EndSection

AGP hasn't worked reliably on thinkpads with savages in a while.

Hope this helps as it works well for me.

Harry Wert
Physicist

---

