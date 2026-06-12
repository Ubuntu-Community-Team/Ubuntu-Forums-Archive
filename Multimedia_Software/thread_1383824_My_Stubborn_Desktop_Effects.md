---
title: "My Stubborn Desktop Effects"
date: 2010-01-17
forum: Multimedia Software
---

### Post by utn on 2010-01-17
I have often had extreme difficulty with Ubuntu cooperating with 3D hardware acceleration and this scenario is of no exception.

My video card is an AGP Radeon 9500 Pro (the R300 chipset) and it is refusing to work with the compiz desktop effects. OpenGL and Direct Rendering are enabled and seemingly working. OpenArena runs with very acceptable frame rates (in excess of 50 fps) at 1280x1024. But every time I attempt to enable compiz it just says "Desktop effects could not be enabled".

When I go to the terminal and type 

glxinfo | grep render

I get,

direct rendering: Yes
OpenGL renderer string: Mesa DRI R300 (R300 4144) 20090101 AGP 8x x86/MMX+/3DNow!+/SSE2 TCL

glxgears is returning ~12,000 frames/5 Sec.

Any ideas?
Thanks.

Oh, and here's my xorg.conf too.

```

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Generic Monitor"
	Device	"Radeon 9500"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Virtual	2560 1024
	EndSubSection
EndSection

Section "Device"
	Identifier	"Radeon 9500"
	Driver	"radeon"
	BusID	"PCI:1:0:0"
	Option 	"XAANoOffscreenPixmaps"
	Option "AllowGLXWithComposite" "true"
	Option "AddARGBGLXVisuals" "true"
EndSection

Section "Module"
	Load	"dri"
	Load	"GLcore"
	Load	"dbe"
	Load	"dri2"
	Load	"extmod"
	load	"glx"
	Load	"record"
EndSection

Section "DRI"
	Mode 0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

```

---

### Post by sports.car.guy on 2010-01-17
That card is a little on the slower side to really be using composting. I would suggest that you just don't run it because it degrades performance on all other fronts, like video playback, etc.

---

