---
title: "flash videos blank"
date: 2008-12-11
forum: Multimedia Software
---

### Post by ulletal on 2008-12-11
After installing restricted ATI drivers for my 4670 512mb, i am no longer abalible to watch flash videos in webs like youtube, it is just blank in the video box. I have flash player nonfree installed and have tried with other browsers besides firefox (Epyphany, Konqueror). Note that before installing the drivers web videos played just fine. 

I have been looking for threads that solve this problem but i haven't found any so I decided to do my first post to this forums. I am pretty new in the linux world and have been doing lots of copy paste commands. My xorg.conf looks like this:


Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Option	    "AIGLX" "on"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "dbe"
	Load  "freetype"
	Load  "extmod"
	Load  "glx"
	Load  "dri"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "UseFastTLS" "1"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Group        "Video"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "RENDER" "Enable"
	Option	    "DAMAGE" "Enable"
	Option	 "Composite" "Enable"
EndSection




I thank you in advance for your help.

---

### Post by ulletal on 2008-12-11
should I have posted with a bold topic? I just realized everyone has...

---

