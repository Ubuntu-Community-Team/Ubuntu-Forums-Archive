---
title: "Login Screen Resolution"
date: 2009-01-20
forum: Multimedia Software
---

### Post by macleodjd on 2009-01-20
My login screen only takes up about 3/4 of the actual display. I'm not sure where to make the changes so the resolution is 1360x768. Here's the contents of my xorg.conf:

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
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

---

### Post by lukjad on 2009-01-20
Well, one thing I found that could work is playing with the screen itself while you are at the login screen. Just resize your screen. Hope this helps!

---

### Post by lukjad on 2009-01-21
Just to clarify, try to adjust the horisontal and vertical size and positions so that they fit the screen better.

---

### Post by theozzlives on 2009-01-21
Could try startup manager, just type startup in the search of add/remove programs.

---

