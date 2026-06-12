---
title: "GeForce MX-440 and Sony CPD G220. How to configure it?"
date: 2009-07-28
forum: Multimedia Software
---

### Post by Young Druid on 2009-07-28
Hi. I have some problems with UI in Xubuntu.
First of all I can't set up 1024x768 with frequency 100Hz. Only 85Hz.
In XP I could easily set up 100 Hz. But in Xubuntu I can't. Please, help to solve this problem. My eyes are bleeding.
The second problem is responsiveness of UI. In XP everything was faster. Opera tabs, windows and even desktop were faster. In Xubuntu UI seems to be slower. 
glxgears shows:
> 6647 frames in 5.0 seconds = 1329.388 FPS
7696 frames in 5.0 seconds = 1539.150 FPS
7711 frames in 5.0 seconds = 1542.029 FPS
7735 frames in 5.0 seconds = 1546.958 FPS
7549 frames in 5.0 seconds = 1509.677 FPS
So it's not bad for my video card. Am I wrong? So may be xfce uses much UI tweaks by default. That's why my UI is so slow. Can anybody explain me, what wrong with my UI?
my xorg.conf
> Section "Monitor"
	Identifier     "CPD-G220"
	VendorName     "Sony"
	ModelName      "Sony CPD-G220"
	HorizSync       30 - 96
	VertRefresh     48 - 170
	Option         "DPMS"
EndSection

Section "Screen"
	Identifier     "Screen0"
	Device         "Device0"
	Monitor        "Monitor0"
	Option         "metamodes" "CRT: 1024x768_100 +0+0"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
	Option	"UseDisplayDevice"	"CRT"
	SubSection "Display"
		Depth       24
	EndSubSection
EndSection

Section "Module"
	Load           "dbe"
	Load           "extmod"
	Load           "type1"
	Load           "freetype"
	Load           "glx"
	Disable		"dri2"
EndSection

Section "InputDevice"
	Identifier     "Mouse0"
	Driver         "mouse"
	Option         "Protocol" "auto"
	Option         "Device" "/dev/psaux"
	Option         "Emulate3Buttons" "no"
	Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier     "Keyboard0"
	Driver         "kbd"
	# generated from default
EndSection

Section "ServerLayout"
	Identifier     "Layout0"
	Screen      0  "Screen0"
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Device"
	Identifier     "Device0"
	VendorName     "NVIDIA Corporation"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
	Option "RenderAccel" "0"
EndSection


---

### Post by Young Druid on 2009-07-29
I resolved my problem with display resolution.
I started Power Strip in Windows XP and looked up modeline for my monitor. It was > "1024x768" 113.303 1024 1112 1224 1392 768 769 772 814 -hsync +vsync
So now my xorg.conf looks like
> Section "Monitor"
	Identifier     "SonyCPDG220"
	VendorName     "Sony"
	ModelName      "Sony CPD-G220"
	HorizSync       30 - 96
	VertRefresh     48 - 170
	Option         "DPMS"
	Modeline "1024x768" 113.303 1024 1112 1224 1392 768 769 772 814 -hsync +vsync
EndSection

Section "Screen"
	Identifier     "Default Screen"
	Device         "GeForceMX440"
	Monitor        "SonyCPDG220"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
	Option	"UseDisplayDevice"	"CRT"
	SubSection "Display"
		Depth           24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "Module"
	Load           "dbe"
	Load           "extmod"
	Load           "type1"
	Load           "freetype"
	Load           "glx"
	Disable		"dri2"
EndSection

Section "InputDevice"
	Identifier     "Logitech"
	Driver         "mouse"
	Option         "Protocol" "auto"
	Option         "Device" "/dev/psaux"
	Option         "Emulate3Buttons" "no"
	Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier     "BTC"
	Driver         "kbd"
EndSection

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Default Screen"
	InputDevice    "BTC" "CoreKeyboard"
	InputDevice    "Logitech" "CorePointer"
EndSection

Section "Device"
	Identifier     "GeForceMX440"
	VendorName     "NVIDIA Corporation"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
	Option "RenderAccel" "0"
EndSection

But UI still seems to be slow. Does anybody know how to make UI faster?
Also I have a philosophical question for a community. Why does Windows determine monitor resolution and frequency well, but Linux not? And if I hadn't Windows XP and Power Strip I think I would never find right modeline for my monitor. All calculators gave wrong modeline for my display. 
So, please give me any suggestions about slow UI of my Xfce.

**Or please, suggest me any tool which can help to determine the reason of UI slowness.**

---

