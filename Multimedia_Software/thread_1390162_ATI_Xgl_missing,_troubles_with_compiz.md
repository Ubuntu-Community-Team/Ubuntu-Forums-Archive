---
title: "ATI Xgl missing, troubles with compiz"
date: 2010-01-25
forum: Multimedia Software
---

### Post by hwttdz on 2010-01-25
I get the following output when I run compiz:
```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (2960x1050) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
```

After this it quits out and reverts to metacity. Running

SKIP_CHECKS="yes" compiz --replace

seems to get me compiz running fine.  There is no xserver-xgl in the repo.  

01:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]

and 

```
Section "Monitor"
	Identifier   "0-CRT1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1280x1024"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1280 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-CRT2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1280x1024"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
	SubSection "Display"
		Virtual	2960 1050
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Virtual	2960 1050
	EndSubSection
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "fglrx"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-CRT1" "0-CRT1"
	Option	    "Monitor-CRT2" "0-CRT2"
	BusID       "PCI:1:0:0"
EndSection
```

and fglrx seems to be 2.8.660 (installed from repo).  This is a minimal install and I've found ubuntu seems to be sloppy with dependencies, so it's possible I'm missing something basic that is usually hidden because it's in the ubuntu-desktop package.

---

### Post by Yellow Pasque on 2010-01-25
You don't want/need XGL. Make sure you have the compiz-gnome package.

---

### Post by hwttdz on 2010-01-25
Already had it.

---

### Post by Yellow Pasque on 2010-01-25
Ok. Maybe try adding this to your xorg.conf and logging out (to restart X):
```
Section "Extensions"
        Option        "Composite"        "On"
EndSection

Section "ServerFlags"
        Option        "AIGLX"            "On"
EndSection
```

---

### Post by shawnisalk on 2010-02-04
I am having this exact issue, too. Unfortunately, adding that bit to xorg.conf did not change anything.

Anyone else have any suggestions?

Thanks,
Shawn

---

