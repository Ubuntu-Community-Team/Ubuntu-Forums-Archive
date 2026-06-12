---
title: "Monitor issue"
date: 2006-07-31
forum: Multimedia &amp; Video
---

### Post by Snocrash on 2006-07-31
Help.....I need an X.org expert....or a new monitor....I think.

Power went out yesterday for a few hours...and when it came back on, my monitor that I have been running at 1600x1200 for 4 years seems to be stuck at 640x480.

My xorg.conf has the standard entries and looks like this:

--------------------------------------------
Section "Device"
	Identifier	"NVIDIA Corporation NV36.1 [GeForce FX 5700 Ultra]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"ULTRASCANP99"
	Option		"DPMS"
	
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV36.1 [GeForce FX 5700 Ultra]"
	Monitor		"ULTRASCANP99"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
EndSection
-------------------------------------------------

But the Xorg.0.log gives the following:

-------------------------------------------------
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(WW) NVIDIA(0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5700 Ultra at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.36.20.18.50
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5700 Ultra at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1600x1200"; removing.
(WW) NVIDIA(0): No valid modes for "1280x1024"; removing.
(WW) NVIDIA(0): No valid modes for "1024x768"; removing.
(WW) NVIDIA(0): No valid modes for "800x600"; removing.
(WW) NVIDIA(0): No valid modes for "720x400"; removing.
(WW) NVIDIA(0): No valid modes for "720x350"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
--------------------------------------------

It's an old Dell 19" monitor I got on ebay years ago and have no documentaion on. Can anyone help or do I need a new one???

Thanks,

Sno

---

### Post by Snocrash on 2006-07-31
Never mind....

An Nvidia reinstall (GLX and kernel) seems to have fixed it. Back to 1600x1200.

-Sno

---

