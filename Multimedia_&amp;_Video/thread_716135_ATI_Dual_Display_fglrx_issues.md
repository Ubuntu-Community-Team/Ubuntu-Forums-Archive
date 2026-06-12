---
title: "ATI Dual Display fglrx issues"
date: 2008-03-05
forum: Multimedia &amp; Video
---

### Post by Eric B on 2008-03-05
I installed the fglrx driver, but I cannot get it to work correctly with my ViewSonic VG1930wm.

I did the dpkg-reconfigure xserver-xorg and it hangs when the external is plugged in directly, when I am in my docking station it doesn't find it at all. Should my xorg.conf list my laptop and my external after doing that?

aitconfig also wont even change my resolution 

sudo aticonfig --resolution=0,1400x1050
error at set screen resolution : screen0 does not exist
aticonfig: parsing the command-line failed.


Here is the pertinent part of my xorg.conf 

```

Section "Device"
	Identifier	"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1440x900" "1400x1050" "1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

```

---

### Post by Eric B on 2008-03-05
sudo aticonfig -f --initial=dual-head --screen-layout=left

that was all it took. why it took hours to find, that I do not know. the external lcd is auto adjusting though and things are a bit off.

---

