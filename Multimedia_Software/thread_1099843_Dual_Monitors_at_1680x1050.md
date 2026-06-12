---
title: "Dual Monitors at 1680x1050 ?"
date: 2009-03-18
forum: Multimedia Software
---

### Post by LegoNerd on 2009-03-18
I tried following this a couple times over the last week: [http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)
I've got an ATI Radeon 4830, running the Catalyst Control Center, hooked up to both my 22" monitors.  Native resolution on them is 1680*1050.  I cannot get it to work!  Only thing big-desktop gives me is 3xxx*1080, which isn't even supposed to work. 
When I try to enter --add-pairmode=1680x1050+1680x1050 FGLRX spits out an error.  


Any insight is greatly appreciated!

---

### Post by drummingpariah on 2009-03-18
This could be a tough one.  Would it be too much trouble for you to post your xorg.conf settings?

---

### Post by markbuntu on 2009-03-18
Are the monitors identified correctly in Catalyst when you use detect monitors?

---

### Post by LegoNerd on 2009-03-18
> **drummingpariah said:**
> This could be a tough one.  Would it be too much trouble for you to post your xorg.conf settings?

Not at all.  This is what I got when using the aticonfig command in terminal:
```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "Default Screen" 0 0
	Screen         "aticonfig-Screen[0]-1" LeftOf "Default Screen"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "/etc/X11/xorg.conf" "off"
	Option	    "PairModes" "1920x1080+1920x1080,1680x1050+1680x1050"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-1"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-1"
	Device     "aticonfig-Device[0]-1"
	Monitor    "aticonfig-Monitor[0]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```


[QUOTE=markbuntu]Are the monitors identified correctly in Catalyst when you use detect monitors? [/QUOTE]
Yes, the both show up as Sceptre X22HG

Thanks!

---

### Post by markbuntu on 2009-03-18
Is that what aticonfig wrote or did you add some of those things yourself?

---

### Post by LegoNerd on 2009-03-18
> **markbuntu said:**
> Is that what aticonfig wrote or did you add some of those things yourself?

aticonfig wrote whatever isn't normally in the file.  I'm gonna try it again tonight from a clean slate.  See what happens.  
Good learning experience... hah

Thanks

---

### Post by markbuntu on 2009-03-18
Boot into recovery mode and use the xfix option. That will give you a clean xorg.conf using the VESA driver. Then resume and run aticonfig...that will give you a clean aticonfig xorg.conf. Then try catalyst before fooling around in xorg.conf again.

---

### Post by LegoNerd on 2009-03-29
OK, so I've got it part way working.  The problem now is that the only resolution it will bigdesktop is 2048x768.  Progress, at least.
New xorg.conf:
```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "DesktopSetup" "horizontal"
	Option	    "Capabilities" "0x00000800"
	Option	    "PairModes" "1440x900+1440x900,1680x1050+1680x1050"
	Option	    "ForceMonitors" "tmds1,tmds2i"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

```

I added the 1440x900 to see if I could even get it to do that.

---

### Post by markbuntu on 2009-03-29
Try the aticonfig --addpairmodes or something like that. Look in aticonfig --help for the exact setup.

---

