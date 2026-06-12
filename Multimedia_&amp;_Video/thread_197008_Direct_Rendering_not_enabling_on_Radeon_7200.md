---
title: "Direct Rendering not enabling on Radeon 7200"
date: 2006-06-15
forum: Multimedia &amp; Video
---

### Post by osomer on 2006-06-15
Here is a quick summary of my situation. I am a brand-new linux user that happened to choose Ubuntu and installed Breezy on the day before Dapper was released. I upgraded to Dapper and most problems went away, but in Breezy I had OpenGL rendering just fine. Now in Dapper it is gone.

My video card is the ATI Radeon 7200 (VIVO 64mb)

I perused around the forums and internet for a couple days haven't found any solutions thus far. I have a feeling the solution is going to something obvious that I should have figured out by now. Any help would be greatly appreciated.

Output of glxinfo | grep "direct"
> direct rendering: No
OpenGL renderer string: Mesa GLX Indirect


Relevant pieces of /etc/X11/xorg.conf
> Section "Module"
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
...
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon R100 QD [Radeon 7200]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
	Option          "RenderAccel"           "true"
EndSection
...
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon R100 QD [Radeon 7200]"
	Monitor		"DELL 1704FPV"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
...
Section "DRI"
	Mode	0666
EndSection

Oh and why not show some glxgears framerate?
> 812 frames in 5.8 seconds = 139.999 FPS
753 frames in 5.7 seconds = 131.514 FPS
753 frames in 5.6 seconds = 133.817 FPS


---

