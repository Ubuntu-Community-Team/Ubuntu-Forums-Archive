---
title: "Soft scrolling lines external monitor"
date: 2010-05-21
forum: Multimedia Software
---

### Post by Rackstar on 2010-05-21
Hey,

I have and external LCD monitor, connected through VGA on my ATI HD 5740.

Now I'm seeing horizontal scrolling lines from bottom to top, very visible on dark grey backgrounds.

I tried searching, and came up with setting my refresh rate. But the refresh rate is set to 60, which is what ATI detected and what shows up on the monitor menu (pressing those little buttons on the side of the monitor).

I tried different settings like 75, but it didn't change. 

I do think it is strange that the catalyst driver sees it as a CRT screen (name is CRT2 and icon in catalyst control center is a CRT), while it is an LCD. Maybe it has something to do with this?

Any ideas?

Thanks!

---

### Post by Rackstar on 2010-05-21
This is my xorg.conf if this is helpfull:

```

Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[2]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "0-LVDS"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1680 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
	Option	    "PreferredMode" "1366x768"
EndSection

Section "Monitor"
	Identifier   "0-CRT2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
	Option	    "PreferredMode" "1680x1050"
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "fglrx"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[2]-0"
	Driver      "fglrx"
	Option	    "Monitor-LVDS" "0-LVDS"
	Option	    "Monitor-CRT2" "0-CRT2"
	BusID       "PCI:2:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[2]-1"
	Driver      "fglrx"
	Option	    "Monitor-CRT2" "0-CRT2"
	BusID       "PCI:2:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
	SubSection "Display"
		Virtual   3046 1050
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[2]-0"
	Device     "amdcccle-Device[2]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   3046 3046
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[2]-1"
	Device     "amdcccle-Device[2]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


```

---

### Post by Rackstar on 2010-05-21
I appearantly has something to do with my electricity. When I unplug my laptop, the scanlines are less, they are also a little bit less when I use different sockets...

Very strange behaviour, can anyone explain or give a practical solution?

Thanks!

---

### Post by HousieMousie2 on 2010-08-28
I know this thread has gone cold... but just in case...

Try looking up ground loop... it's a guess from other search results I've seen.

---

