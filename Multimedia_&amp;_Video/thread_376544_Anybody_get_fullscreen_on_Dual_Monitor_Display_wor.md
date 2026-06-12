---
title: "Anybody get fullscreen on Dual Monitor Display working?"
date: 2007-03-05
forum: Multimedia &amp; Video
---

### Post by survient on 2007-03-05
has anybody found a way with twinview or a similar method, to get a fullscreen app to run on one monitor, and leave the other monitor at the desktop? I've added singular resolutions to the xorg.conf, but that shuts the other monitor off. Just wondering if anybody found a way, or was working on a way to do it.

---

### Post by mojoman on 2007-03-15
Yes, I have. I always use fullscreen mode when I watch movies (my second monitor is a projector) and I got the desktop visible on my first monitor. Using Xine, I got the control visible on that screen. I didn't do any special editing to get it this way though, it's sort of "default" I think (I believe there is a xinerama-option that can be used to turn on and off appz stretching across both screen but I got no idea why one shuts down. Anyway, here's the relevant parts of my xorg.conf.

```
Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:7:0:0"
	Option "TwinView" "True"
	Option "TwinViewOrientation" "RightOf"
	Option "MetaModes" "1024x768,1280x720"
EndSection

Section "Monitor"	#this section is from original xorg
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"	#this section is from projector xorg
	Identifier	"Projector"
	Option		"DPMS"
EndSection

Section "Screen"	#this section is from original xorg
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600"
    EndSubSection
EndSection

Section "Screen"	#this section is from projector xorg
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Projector"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x720" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x720" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x720" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x720" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x720" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x720" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection
```

/mojoman

---

