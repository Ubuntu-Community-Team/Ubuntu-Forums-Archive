---
title: "Low Resolution Problem"
date: 2006-08-13
forum: Multimedia &amp; Video
---

### Post by Mach1US on 2006-08-13
I have toshiba 2180cdt with s3 Virge card and only resolution that i can select from System>Preferences>ScreenResolution is 640x480.
Windows used to display 1024x768.
I have tried  sudo dpkg-reconfigure xserver-xorg with no result.
I have added "modeline..." from command " gtf 800 600 60" hoping to get at least 600x800.
I have even lowered default depth to 16 just to get it higher but NOTHING.](*,) 
Can anybody look at my xorg and tell me where have i gone wrong?

Section "Device"
	Identifier	"S3 Inc. ViRGE/MX"
	Driver		"s3virge"
	BusID		"PCI:0:8:0"
	VideoRam	2000
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"LCD Monitor"
Modeline "800x600_60.00"  38.22  800 832 912 1024  600 601 604 622  -HSync +Vsync
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"S3 Inc. ViRGE/MX"
	Monitor		"LCD Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by foolsh on 2006-08-13
try changing your monitor section to this

Section "Monitor"
Identifier "LCD Monitor"
HorizSync 30-60
VertRefresh 60
Option "DPMS"
EndSection

---

### Post by Mach1US on 2006-08-13
It has worked as far as getting higher resolution but now i can only see left upper part of the screen.
Any idea why is that?

---

### Post by foolsh on 2006-08-13
try this in your device section


Section "Device"
Identifier "S3 Inc. ViRGE/MX"
Driver "s3virge"
#BusID "PCI:0:8:0"
#VideoRam 2000
#Option "UseFBDev" "true"
Option "ShadowFB" "true"
EndSection

---

### Post by Mach1US on 2006-08-13
I have figure it out! My card supports res up to 1024x768 while my screen can only handle 800x600 (i know it is old system) so upon editing out all instances of 1024x768 all got back to normal.
 Thanks FOOLSH , that made made my :D :D :D day=D>

---

