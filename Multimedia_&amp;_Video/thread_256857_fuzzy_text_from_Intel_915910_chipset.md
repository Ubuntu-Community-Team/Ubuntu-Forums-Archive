---
title: "fuzzy text from Intel 915/910 chipset"
date: 2006-09-13
forum: Multimedia &amp; Video
---

### Post by Alex.X.Zhang on 2006-09-13
(I posted this in the beginner's forum, later thought this might be a better place. sorry for double posting. )

Hi all,

I got this Dell Optiplex 210L at work and I installed Ubuntu on it. The text display is horrible. Text has no edge at all. everything is fuzzy.

here is my lspci output:
0000:00:00.0 Host bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Processor to I/O Controller (rev 04)
0000:00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller (rev 04)
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 04)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
0000:00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
0000:03:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 04)


Here is my xorg.conf:
Section "Device"
identifier "Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
boardname "Intel 915"
busid "PCI:0:2:0"
driver "i810"
screen 0
vendorname "Intel"
EndSection

Section "Monitor"
identifier "LCD1711"
vendorname "Generic"
modelname "1280x1024 @ 76 Hz"
HorizSync 31.5-82
VertRefresh 50-90
modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
modeline "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
modeline "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
modeline "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
modeline "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
modeline "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
modeline "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
modeline "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
modeline "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
modeline "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
modeline "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
modeline "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
modeline "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
modeline "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
modeline "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
modeline "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
modeline "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
modeline "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
modeline "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
modeline "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
modeline "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
modeline "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
gamma 0.97
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
Monitor "LCD1711"
DefaultDepth 24
SubSection "Display"
depth 24
modes "1280x1024@60" "1280x960@75" "1280x960@60" "1400x1050@60" "1280x1024@75" "1400x1050@75" "1280x854" "1600x1200@65" "1152x768@54" "1600x1200@60" "1152x864@75" "1024x768@43" "1024x768@60" "1024x768@70" "1024x768@75" "1024x768@85" "832x624@75" "800x600@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56" "640x480@85" "640x480@75" "640x480@72" "640x480@60"
EndSubSection
EndSection

Anybody has any ideas?

Thank you in advance.
Edit/Delete Message

---

### Post by wieman01 on 2006-09-13
I think your problem has to do with your screens' refresh rate. Not sure if you have configured them correctly. This is how my xorg.conf looks like:
[HTML]Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option       	"LeftEdge"        	"120"
    	Option       	"RightEdge"        	"830"
    	Option       	"TopEdge"        	"120"
   	Option      	"BottomEdge"        	"650"
  	Option     	"FingerLow"        	"14"
  	Option      	"FingerHigh"        	"15"
  	Option      	"MaxTapTime"        	"180"
  	Option  	"MaxTapMove"        	"110"
    	Option    	"EmulateMidButtonTime"  "75"
   	Option   	"VertScrollDelta"    	"20"
   	Option     	"HorizScrollDelta"    	"20"
  	# orig = 0.25
	Option    	"MinSpeed"        	"0.7"
	# orig = 0.75
  	Option    	"MaxSpeed"        	"0.9"
	# orig = 0.015
  	Option     	"AccelFactor"        	"0.035"
	# orig = 200
  	Option     	"EdgeMotionMinSpeed"    "350"
	# orig = 200
   	Option      	"EdgeMotionMaxSpeed"    "350"
  	Option    	"UpDownScrolling"    	"1"
  	Option    	"LeftRightScrolling"    "1"
   	Option     	"CircularScrolling"  	"1"
  	Option     	"CircScrollDelta"    	"0.1"
  	Option     	"CircScrollTrigger"    	"2"
EndSection

Section "Device"
	Identifier	"Internal Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"MonitorLayout"	"CRT,LFP"
	Screen 		0
EndSection

Section "Device"
        Identifier	"External Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"MonitorLayout" "CRT,LFP"
	Option		"TVOutFormat" "Composite" 
	Screen 		1
EndSection

Section "Monitor"
	Identifier	"Internal Monitor"
	HorizSync	30-60
	VertRefresh	50-75
	Option		"DPMS"
	Modeline    	"1280x768" 80.14 1280 1344 1480 1680 768 769 772 795
EndSection

Section "Monitor"
        Identifier      "External Monitor"
        Option  	"DPMS"
        HorizSync 	30 - 85
        VertRefresh 	56 - 76
EndSection

Section "Screen"
	Identifier	"Internal Screen"
	Device		"Internal Device"
	Monitor		"Internal Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x768"
	EndSubSection	
EndSection

Section "Screen"
        Identifier      "External Screen"
        Device          "External Device"
        Monitor         "External Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "800x600"
        EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Internal Screen"
	#Screen		"External Screen" RightOf "Internal Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option		"Xinerama" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection

#Section "Extensions"
#	Option  "Composite" "Enable"
#EndSection

Section "ServerFlags"
       Option		"Xinerama" "true"
EndSection
[/HTML]

---

