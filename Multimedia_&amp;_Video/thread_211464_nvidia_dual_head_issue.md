---
title: "nvidia dual head issue"
date: 2006-07-08
forum: Multimedia &amp; Video
---

### Post by wadoryu on 2006-07-08
i have two monitors connected to my geforce2 mx/mx 400 card.
when i run x i only get something on one monitor.  I have attached my xorg.conf for review.

if anyone can point out what i am doing wrong. thank you
```

Section "Device"
	Identifier  "AGP1"
	Driver      "nvidia"
	Option      "RenderAccel"      "True"
        Option      "NoLogo"           "True"
	BoardName   "NVIDIA GeForce2 MX/MX 400"
	BusID       "PCI:1:0:0"
	Option      "NvAGP"	       "1"
	Screen 0
	Option      "ConnectedMonitor" "DFP-0"
EndSection

Section "Device"
	Identifier  "AGP2"
	Driver      "nvidia"
        Option      "NoLogo"           "True"
	Option      "RenderAccel"      "True"
	BoardName   "NVIDIA GeForce2 MX/MX 400"
	BusID       "PCI:1:0:0"
	Option	    "NvAGP"		"1"
	Screen 1
	Option      "ConnectedMonitor" "CRT-1"
EndSection


Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Dell"
	Option		"DPMS"
EndSection


Section "Screen"
	Identifier "Left"
	Device     "AGP1"
	Monitor    "Dell"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Center"
	Device     "AGP2"
	Monitor    "SyncMaster"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0        "Center" 0 0
	Screen 1        "Left" LeftOf "Center"
	Option "Xinerama" "On"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection
```

---

