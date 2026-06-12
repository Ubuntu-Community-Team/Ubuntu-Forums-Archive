---
title: "Radeon 9700 pro dual monitors"
date: 2007-11-04
forum: Multimedia &amp; Video
---

### Post by Inquisitr on 2007-11-04
HI, I recently redid my Ubuntu install to get a fresh copy of 7.10 

Only problem is I can't get dual monitors to work.  I've been trying to follo1 the guide at 
[http://ubuntuforums.org/showthread.php?t=301941&highlight=ATI+x800XL](http://ubuntuforums.org/showthread.php?t=301941&highlight=ATI+x800XL)

But whenever I enable the restricted drivers Ubuntu starts up in low graphics mode and I can't get the resolution to go past 800X 600 or get dual monitors working.

I've disabled the restricted drivers again, but I can't find a working way to get this going.  Here's the relevant sections from my xorg.conf

Any help would be awesome, I've loved Ubuntu so far but if I can't get dual monitors working there's really no point to keeping it as with my work I need every centimeter of desktop space I can get.

Thanks

```
Section "Device"
	Identifier	"ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro]"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:5:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection

Section "Monitor"
	Identifier	"L70B"
	Modelname	"Custom 1"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro]"
	Monitor		"L70B"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	1024
		Modes		"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:5:0"
	Driver		"ati"
	Screen	1
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

---

### Post by Inquisitr on 2007-11-04
Still messing with it, had to redo Ubuntu over again..

Here's my xorg.conf after a completely fresh install, all I've done is let Ubuntu download it's own updates.

Please, I really don't want top have to get rid of Ubuntu just because I can't get dual monitors working.

```
Section "Device"
	Identifier	"ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro]"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

---

### Post by Inquisitr on 2007-11-04
bump for great justice.

---

### Post by Inquisitr on 2007-11-05
So I've tried every Ziox guide, every guide that tries to get the propritary drivers working..nothing works

I've reinstalled Ubuntu bout 10 times now.

Freshly installed again now, I'm giving this topic one more day before I say this OS isn't worth the effort and go back to windows.

I don't care how many of you are going to tell me it's because I have an ATI card, an OS shouldn't require this much work from me for something as stupid and simple as dual monitors on a dual head video card.  

Can anyone help me out here?

---

### Post by criskat777 on 2007-11-08
I don't know if your still around or if u just quit. But u should try ( Envy ) it's a program that install the right drivers for your setup for u. it works i did it on my system that has a 9600 pro and it installed the latest ati propriety drivers with ati control panel. then i setup dual screen with the control panel. let use know if it worked for u

---

