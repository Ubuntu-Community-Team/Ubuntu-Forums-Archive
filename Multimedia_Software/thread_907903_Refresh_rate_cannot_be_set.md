---
title: "Refresh rate cannot be set"
date: 2008-09-01
forum: Multimedia Software
---

### Post by Brian88 on 2008-09-01
I don't know which category can I post this,..

I have Samsung SyncMaster 551v. My monitor supports up to 1152x864 at 75Hz refresh rate. but Ubuntu only sets it at 1024x768 at 60Hz. On the Screen Resolution dialog box (GNOME) no higher refresh rate nor resolution can be selected.. where can I set this?

(on xrandr the highest possible is 1024x768 at 60hz but in Windows it can supports up to 1152x864 at 75Hz)

---

### Post by mc4man on 2008-09-02
Your exact model isn't listed but a SyncMaster 550v is. you may want to ck. if the specs are the same. (should be ok.

If so go 
```
 sudo displayconfig-gtk
```
use the screen section to pick it out.

**If you have a nvidia card **you **may** have to add  1 line to your new xorg and edit another.
```

section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"NVIDIA GeForce 7 Series"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
        [COLOR="Red"]Option "DynamicTwinView" "False"[/COLOR]
        [COLOR="SeaGreen"]Option		"AddARGBVisuals"	"True"
        Option		"AddARGBGLXVisuals"	"True"[/COLOR]
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Dell"
	Modelname	"Dell P991"
	Horizsync	30.0-107.0
	Vertrefresh	48.0-120.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.......................................................clipped
modeline  "2048x1536@60" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		[COLOR="Blue"]Virtual	1280	1024[/COLOR]
```

add the line in red (only needed if you don't get all your proper refresh rate choices
check the line in blue for too high a setting (affects login screen size
you may also want to add the lines in green

---

### Post by Brian88 on 2008-09-21
Thanks. I should try if I can run my Ubuntu well (my problem now is [http://ubuntuforums.org/showthread.php?p=5828069#post5828069](http://ubuntuforums.org/showthread.php?p=5828069#post5828069) )

---

