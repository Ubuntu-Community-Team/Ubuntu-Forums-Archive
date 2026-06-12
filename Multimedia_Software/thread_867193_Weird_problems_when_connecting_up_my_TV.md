---
title: "Weird problems when connecting up my TV"
date: 2008-07-22
forum: Multimedia Software
---

### Post by svivian on 2008-07-22
I'm trying to connect up my TV to my computer in order to watch videos (stored on my PC) on the TV. I'm using Hardy.

I followed the thread on Xinerama and it kinda works - the TV displays the computer desktop or video etc, except whenever I move my mouse the whole PC screen moves... in other words, the mouse stays static at the top left and when I move down the display moves up instead of the mouse moving!!

On my graphics card - "ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]" - there are two connections, one for my monitor and a DVI which I connect to the TV with a DVI->HDMI cable.

Here's the relevant section of xorg.conf:
```
Section "Device"
	Identifier  "0 Generic Video Card"
	Driver      "fglrx"
	Option	    "EnableMonitor" "tmds1,crt2"
	BusID       "PCI:2:0:0"
	Screen      0
	Option		"DDCMode" "True"
	Option		"MonitorLayout" "TMDS,TV"
EndSection

Section "Device"
	Identifier  "1 Generic Video Card"
	Driver      "fglrx"
	Option	    "EnableMonitor" "tmds1,crt2"
	BusID       "PCI:2:0:0"
	Screen      1
	Option		"DDCMode" "True"
	Option		"MonitorLayout" "TMDS,TV"
EndSection


Section "Monitor"
	Identifier   "0 Generic Monitor"
	HorizSync    30.0 - 81.0
	VertRefresh  56.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "1 Generic Monitor"
	HorizSync    30.0 - 81.0
	VertRefresh  56.0 - 75.0
	Option	    "DPMS"
EndSection


Section "Screen"
	Identifier "0 Default Screen"
	Device     "0 Generic Video Card"
	Monitor    "0 Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

Section "Screen"
	Identifier "1 Default Screen"
	Device     "1 Generic Video Card"
	Monitor    "1 Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection


Section "ServerLayout"
	Identifier     "Default Layout"
	Screen 0       "0 Default Screen"
	Screen 1       "1 Default Screen" RightOf "0 Default Screen"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	Option         "Xinerama" "true"
EndSection
```

I've tried several combinations in the *"MonitorLayout" "TMDS,TV"* part, this one is the only one that works at all.

In Windows it's a simple case of opening the display settings and turning the other monitor "on". Is there some similar tool available for Ubuntu?

---

