---
title: "[SOLVED] dual monitor set up with GeForce 7600 GS"
date: 2007-11-23
forum: Multimedia &amp; Video
---

### Post by enternalsoul on 2007-11-23
I have read the sticky and i got the driver working but i can not get both monitors working.

if any one has a working xorg.conf with this or simular card please post the relevant parts to it please.

thanks in advance.

:guitar:

:popcorn:

:KS

\\:D/\\:D/

---

### Post by helloimalemur on 2007-11-23
heres my xorg if sudo nvidia-settings didnt work..
[http://404serv.selfip.com/upload/xorg.conf]("http://404serv.selfip.com/upload/xorg.conf")

---

### Post by speedinbil on 2007-11-23
I also have an nvidia card on my workstation and the problem with it is that I can't figure out how to have two monitors with different resolution.  If you have the same size monitors it should work more easily. You can select the monitors under administration and activate the secondary screen and choose the options for how to configure them together.  I am running the 32 bit version of Ubuntu 7.10.  I can't remember the name of the card I have at work right now but was able to get it to run dual screens, only with the small monitor resolution for both (which didn't work out)  do you have two monitors the same size?

---

### Post by helloimalemur on 2007-11-23
lawl i have an lcd and crt both at 1280X1024

---

### Post by enternalsoul on 2007-11-23
Well it took a while and i had some permission change on a file in the X11 folder that caused me to be able to log in as root and it worked but not as me  but i got that fixed.

now i have both my LCD 19" displays at the right resolution and working perfectly  no distortion and looks even better than it did with my ATI card.

thanks big time for the help.

the nividia-settings   thing kinda helped but but mostlyhad to resort to looking at your xorg.conf and a few others to get mine to work right  so here is mine if any one else is having the same problem (just the monitor stuff)


Section "ServerLayout"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier	"Default Layout"
  screen 0 "Screen1" 0 0
  screen 1 "Screen0" rightof "Screen1"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

Section "ServerFlags"
	Option		"Xinerama"	"true"
EndSection



Section "Monitor"
	Identifier	"R911E"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
	Horizsync	31.5	-	64.0
	Vertrefresh	56.0	-	65.0
	Option		"dpms"
	Gamma	1
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
	Horizsync	31.5	-	64.0
	Vertrefresh	56.0	-	65.0
	Option		"dpms"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
   modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection

Section "Monitor"
	Identifier	"Monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
   modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Screen	0
EndSection

Section "Device"
	Identifier	"Videocard0"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	1
EndSection

Section "Device"
	Identifier	"Videocard1"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"R911E"
	Defaultdepth	24
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"TwinView"	"0"
	SubSection "Display"
		Virtual	1280	1024
		Depth	24
		Modes		"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Videocard0"
	Monitor		"Monitor0"
	Defaultdepth	24
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"TwinView"	"0"
	Option		"metamodes"	"CRT: 1024x768@60 +0+0; CRT: 800x600@60 +0+0; CRT: 800x600@56 +0+0; CRT: 640x480@60 +0+0"
	SubSection "Display"
		Depth	24
		Virtual	1280	1024	Modes		"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"Videocard1"
	Monitor		"Monitor1"
	Defaultdepth	24
	Option		"TwinView"	"0"
	Option		"metamodes"	"DFP: nvidia-auto-select +0+0"
	SubSection "Display"
		Depth	24
		Virtual	1280	1024
		Modes		"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

---

### Post by enternalsoul on 2007-11-23
that is strange one monitor is a CRT but it works!  best not change it :lolflag:

can i set this to solved?

---

### Post by helloimalemur on 2007-11-24
go ahead :]
if it helped you im sure others will benefit =D

---

