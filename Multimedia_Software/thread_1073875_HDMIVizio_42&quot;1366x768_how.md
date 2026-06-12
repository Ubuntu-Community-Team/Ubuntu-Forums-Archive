---
title: "HDMI/Vizio 42&quot;/1366x768: how?"
date: 2009-02-18
forum: Multimedia Software
---

### Post by ravenpi on 2009-02-18
Hi, all.  I recently upgraded my motherboard to an ECS board with an ATI Radeon HD 3200, with HDMI, on the motherboard.  I used to run -- just fine -- my Vizio 42" TV at 1366x768 via VGA, but when I tried to get HDMI going, no dice.  I've tried both adding modelines and config info from my old xorg.conf, as well as using xrandr to "fix" it retroactively.  Neither works.  Unfortunately, it still comes up in 1280x1024, which just looks lousy.  So:

1) How do I override probed values?
2) I assume that most anything I can do with VGA, I can do with HDMI.  No?

For reference, the xorg.conf that works with VGA is below.  (The simplest thing I've done thus-far was a simple s/nvidia/ati/;)

Thanks for any help/suggestions!

-Ken

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc101"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	Option		"NoDDCValue"	"True"
	Option "UseEdidDpi" "False"
	Option "PanelSize" "1366x768"
	Option "ModeValidation" "NoWidthAlignmentCheck"
EndSection

Section "Monitor"
	Identifier	"GV42L HDTV"
	Option		"DPMS"
#	ModeLine "1366x768" 85.86 1366 1440 1584 1800 768 769 772 795 -HSync +Vsync
	DisplaySize	345	195
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5200]"
	Monitor		"GV42L HDTV"
	Defaultdepth	24
	SubSection "Display"
	Modes		"1366x768"
#"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "ServerFlags"
   Option "blanktime" "0"
   Option "standbytime" "0"
   Option "suspendtime" "0"
   Option "offtime" "0"
EndSection

---

