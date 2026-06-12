---
title: "Increase dual monitor screen resolution"
date: 2007-09-15
forum: Multimedia &amp; Video
---

### Post by keenlearner on 2007-09-15
Hello, I have look through many people's solution on increasing screen resolution but all couldn't solve my problem on Dual monitor resolution.

> 
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"0 Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
Screen      0
Option "DDCMode" "True"
Option "MonitorLayout" "CRT,LFP"
EndSection

Section "Device"
	Identifier	"1 Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
Screen      1
Option "DDCMode" "True"
Option "MonitorLayout" "CRT,LFP"
EndSection

Section "Monitor"
	Identifier	"0 Generic Monitor"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-76
EndSection

Section "Monitor"
	Identifier	"1 Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"0 Default Screen"
	Device		"0 Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"0 Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"1 Default Screen"
	Device		"1 Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"1 Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen	0	"0 Default Screen"
    Screen       1   "1 Default Screen" LeftOf "0 Default Screen"
Option "Xinerama" "true"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection


_0 Generic Monitor_
My LCD monitor
Samsung SyncMaster 173v
Maximum resolution 1280x1024
17 inch
Maximum Referesh rate 75hz
HorizSync	30-81
VertRefresh	56-76

_1 Generic Monitor_
My Acer notebook monitor
14.1 inch

I have my Acer Notebook Intel Graphic Media Accelerator 950 screen work fine in maximum resolution of 1280x800, but not for LCD when I set to 1280x1024 maximum resolution and then restart with CTRL+ ALT +BACKSPACE, my notebook screen work, but my LCD screen become all dark. But when I set the LCD Modes to 1280x1000 it work and both monitor shows up, but the max resolution of my LCD still like 1024x768 when I check from System > Preference > Screen resolution. I have spent for at least 3 hours for this, anybody's help will very very appreciated. Thank you.f

---

### Post by jis on 2007-09-17
Have you tried these tricks:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

