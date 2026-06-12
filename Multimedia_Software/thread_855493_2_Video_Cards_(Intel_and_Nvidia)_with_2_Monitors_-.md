---
title: "2 Video Cards (Intel and Nvidia) with 2 Monitors - Help"
date: 2008-07-10
forum: Multimedia Software
---

### Post by pimpaulogy on 2008-07-10
I have been trying to accomplish a 2 video card, 2 monitor setup since Feisty (now running Hardy) but I just can't get it.

My video cards are:
NVIDIA GeForceMX4000
Intel Corporation 82945G/GZ Integrated Graphics Controller

My monitors are:
ViewSonic VP171b - plugged into the NVIDIA card
ViewSonic VP730 Series - plugged into the Intel integrated card

When the system initially boots, video is displayed from the Intel card.  Once X starts up, video (log in into Ubuntu) is displayed on the NVIDIA card, but I can mouse over to the Intel card (it's just a black screen)

What I currently have is:
X running on one screen, and X running on the other screen, but it's a different instance of X (I think, still learning about Linux).  So I have a desktop on each, but I can't drag from one screen to the other.  I have tried to use the "Xinerama" switch in my xorg.conf but when X restarts, it crashes and goes into Low Graphics mode.  I have tried just about ever combination that I can think of, or find on the internet, but I still can't achieve 1 instance of X spanned across both screens.

Here is my current xorg.conf, with some lines commented out to show so of the switches I have tried.

```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"NVIDIA GeForceMX4000"
	Boardname	"NVIDIA GeForce4 (generic)"
	Busid		"PCI:5:4:0"
	Driver		"nvidia"
	Screen 0	
	Vendorname	"NVIDIA"
#	Option "DDCMode" "True"
	Option "MonitorLayout" "ViewSonic VP171b"
	Option		"NoLogo"	"True"
EndSection

Section "Device"
	Identifier	"Intel Corporation 82945G/GZ Integrated Graphics Controller"
	Boardname	"intel"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen 0	
#	Option "DDCMode" "True"
	Option "MonitorLayout" "VP730 Series"
EndSection


Section "Monitor" 
	Identifier	"ViewSonic VP171b"
	Vendorname	"ViewSonic"
	Modelname	"ViewSonic VP171b"
	Option	"DPMS"
	Horizsync	30-82
	Vertrefresh	50-85
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
#  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection

Section "Monitor"
	Identifier	"VP730 Series"
	Modelname	"VP730 Series"
	Option	"DPMS"
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
#  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen" 
	Identifier	"LeftScreen"
	Device		"NVIDIA GeForceMX4000"
	Defaultdepth	24
	Monitor		"ViewSonic VP171b"
	SubSection "Display"
		Depth	24
#		Virtual	2560	1024
Modes		"1280x1024@75"	"1152x864@75"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"1024x768@85"	"832x624@75"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"
#"1280x1024@60"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"RightScreen"
	Device		"Intel Corporation 82945G/GZ Integrated Graphics Controller"
	Monitor		"VP730 Series"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
Modes		"1280x1024@75"	"1152x864@75"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"
#"1280x1024@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  	Screen "LeftScreen"
	Screen "RightScreen" RightOf "LeftScreen"
#	Option "xinerama" "true"
	Inputdevice	"Generic Keyboard" "CoreKeyboard"
	Inputdevice	"Configured Mouse" "CorePointer"
	
EndSection

```

As mentioned, I have found multiple posting in this forum about how to get it working, but each attempt always resulted in Low Graphics Mode and it always seemed that most situation were a laptop with external monitor, not desktop with one on board and one additional video card (PCI-X)

Any assistance would be greatly appreciated.  I feel that I am really close to getting this to work, but I am just missing that final switch or step.

---

### Post by pimpaulogy on 2008-07-14
**Bump**

---

