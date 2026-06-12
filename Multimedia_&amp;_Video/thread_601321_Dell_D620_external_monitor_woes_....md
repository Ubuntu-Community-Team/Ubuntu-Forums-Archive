---
title: "Dell D620 external monitor woes ..."
date: 2007-11-03
forum: Multimedia &amp; Video
---

### Post by kgish on 2007-11-03
I recently upgraded to Ubuntu 7.10 and since then I've been having problems with my external monitor. 

At work I have a docking station hooked up to my external monitor and everything works just fine.

When at home however my stand-alone laptop (without external monitor) crashes on startup with a segmentation fault and brings me to the command line.

If I delete move my xorg.conf and restart, it all works fine again.

Any ideas what might be going wrong?

--- xorg.conf ---

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
   Identifier      "Synaptics Touchpad"
   Driver          "synaptics"
   Option          "SendCoreEvents"        "true"
   Option          "Device"                "/dev/psaux"
   Option          "Protocol"              "auto-dev"
   Option          "Emulate3Buttons"       "on"
   Option          "SHMConfig"             "on"
   Option       "LeftEdge"              "130"
   Option       "RightEdge"             "840"
   Option       "TopEdge"               "130"
   Option       "BottomEdge"            "640"
   Option       "FingerLow"             "14"
   Option       "FingerHigh"            "15"
   Option       "MaxTapTime"            "180"
   Option       "MaxTapMove"            "110"
   Option       "ClickTime"             "0"
   Option       "MaxDoubleTapTime"      "100"
   Option       "EmulateMidButtonTime"  "75"
   Option       "VertScrollDelta"       "20"
   Option       "HorizScrollDelta"      "20"
   Option       "MinSpeed"              "0.60"
   Option       "MaxSpeed"              "1.10"
   Option       "AccelFactor"           "0.130"
   Option       "EdgeMotionMinSpeed"    "200"
   Option       "EdgeMotionMaxSpeed"    "200
   Option       "UpDownScrolling"       "1"
   Option       "CircularScrolling"     "1"
   Option       "CircScrollDelta"       "0.1"
   Option       "CircScrollTrigger"     "2"
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller 0"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Screen		0
	Option		"MonitorLayout" "DFP,LFP"
	Option		"DevicePresence" "yes"
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller 1"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Screen		1
	Option		"MonitorLayout" "DFP,LFP"
	Option		"DevicePresence" "yes"
EndSection

Section "Monitor"
	Identifier	"Laptop Monitor"
	Option		"DPMS"
#        Modeline "1440x900" 108.84 1440 1472 1880 1912 900 918 927 946
EndSection

Section "Monitor"
	Identifier	"External Monitor"
	ModelName       "Dell 1707FP"
	Option "DPMS"
EndSection

Section "Screen"
	Identifier	"Laptop Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller 0"
	Monitor		"Laptop Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"External Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller 1"
	Monitor		"External Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"Dual-Monitor Layout"
	Screen 0	"Laptop Screen" 0 0
	Screen 1	"External Screen" LeftOf "Laptop Screen"
	Option		"Xinerama" "On"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

