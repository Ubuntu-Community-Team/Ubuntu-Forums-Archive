---
title: "ATI Radeon Xpress 1270 and S-video"
date: 2010-02-18
forum: Multimedia Software
---

### Post by misfit815 on 2010-02-18
I've been at this for way too long. I have a Dell Latitude D531 with an ATI Radeon Xpress 1270. I'm running 9.10 (Karmic), with the open ATI driver installed. I cannot get the S-video out to a TV to work. Here is my xorg.conf:

> 
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen 0 "LCD"
	Screen 1 "TV" LeftOf "LCD"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option "DefaultServerLayout" "Default Layout"
	#Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier "LCD"
EndSection

Section "Monitor"
	Identifier "TV"
        HorizSync 30-50
	VertRefresh 60
EndSection

Section "Device"
	Identifier "LCD" # Radeon Xpress 1270
	Driver "ati"
	BusID "PCI:1:5:0"
	Screen 0
EndSection

Section "Device"
	Identifier "TV"
	Driver "ati"
	Option "MonitorLayout"	"TV,LFP"
	Option "TVStandard" "NTSC"
	Option "TVOutFormat" "SVIDEO"
	Option "ConnectedMonitor" "TV"
	BusID "PCI:1:5:0"
	Screen 1
EndSection

Section "Screen"
	Identifier "LCD"
	Device "LCD"
	Monitor "LCD"
	DefaultDepth 24
EndSection

Section "Screen"
	Identifier "TV"
	Device "TV"
	Monitor "TV"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "800x600"
	EndSubSection
EndSection


Running xrandr never shows the S-video out. Here's what I get:

> 
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       60.0*+
   1280x720       59.9  
   1152x768       59.8  
   1024x768       60.0     59.9  
   800x600        60.3     59.9  
   640x480        59.9     59.4  


I'm begging for help. I'm getting upstaged by my wife with an identical Dell with Windows XP. Thanks.

---

### Post by misfit815 on 2010-02-19
I got it. Here's my xorg.conf:

> 
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen 0 "LCD"
	Screen 1 "TV" LeftOf "LCD"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option "DefaultServerLayout" "Default Layout"
EndSection

Section "Monitor"
	Identifier "LCD"
EndSection

Section "Monitor"
	Identifier "TV"
        HorizSync 30-50
	VertRefresh 60
EndSection

Section "Device"
	Identifier "Radeon Xpress 1270"
	Driver "ati"
	BusID "PCI:1:5:0"
	Option "MonitorLayout"	"TV,LFP"
	Option "TVStandard" "NTSC"
	Option "TVOutFormat" "SVIDEO"
	Option "ConnectedMonitor" "TV"
	Option "ATOMTvOut" "true"
EndSection

Section "Screen"
	Identifier "LCD"
	Device "Radeon Xpress 1270"
	Monitor "LCD"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier "TV"
	Device "Radeon Xpress 1270"
	Monitor "TV"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1360x800"
	EndSubSection
EndSection


And to switch the S-video on and off, I use:

> 
xrandr --output S-video --auto


And:

> 
xrandr --output S-video --off


---

