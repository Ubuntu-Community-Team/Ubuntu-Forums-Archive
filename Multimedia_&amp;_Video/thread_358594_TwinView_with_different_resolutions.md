---
title: "TwinView with different resolutions"
date: 2007-02-11
forum: Multimedia &amp; Video
---

### Post by martin_legion on 2007-02-11
Hello. Is there any way I can have different resolutions in the monitor and in the TV using twinview?
I would like to have 1152 on my monitor and 1024 on the TV.
Here's my xorg.conf. At this time I have 1152x864 in both screens, instead of having 1024x768 on the TV.
Thanks

Section "Device"
	Driver		"nvidia"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Option		"TVStandard" "PAL-NC"
	Option		"TVOutFormat" "SVIDEO"
	Option		"ConnectedMonitor" "CRT,TV"
	#BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Viewsonic"
	HorizSync 	30-65
	VertRefresh	50-160
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"Viewsonic"
	DefaultDepth	24
	Option		"TwinView" "on"
	Option		"TwinViewOrientation" "Clone"
	Option		"MetaModes" "1152x864,1024x768"  # **<-- !!!!!**
	Option		"SecondMonitorHorizSync" "30 - 96.0"
	Option		"SeconfMonitorVertRefresh" "50 - 120"
	SubSection "Display"
		Depth		16
		Modes		"1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0 "Screen0" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

---

