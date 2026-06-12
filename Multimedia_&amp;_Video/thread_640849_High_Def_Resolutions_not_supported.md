---
title: "High Def Resolutions not supported?"
date: 2007-12-14
forum: Multimedia &amp; Video
---

### Post by azizzle on 2007-12-14
I am trying to install my 42" tv to be a clone of my computer desktop(1440x900) but the resolution I need(1280x720) can't be found when I try to configure it with nvidia-settings. Has anybody installed a TV with High Def resolution? I have been pouring through all of the tutorials all last night, and all day today looking for something similar to my situation, but I have found nothing. I am trying to basically clone my desktop(with a different resolution) so that I can watch movies on my tv. I think X randr might work, but when i ran Grandr it only recognized one of my diplays, even though both were plugged in. Is this the right direction I should be going?

---

### Post by azizzle on 2007-12-15
bump

---

### Post by williammanda on 2007-12-15
Please post more info: Xorg.conf, video card, using one or two monitors....etc
I have two computer setup with mythtv:

Hardware
CPU: Intel Core 2 Duo 6400
RAM: 2 GB
Video Card: Nvidia 7300 le 512 MB ram PCIe
Sound Card:: Onboard sound - ADI AD1986A
HD: 250 GB
Remote: Snapstream Firefly RF
Tuners: pcHDTV HD-5500
Monitor: Westinghouse W4207 42"

Hardware
CPU: AMD Dual Core 4200
RAM: 2 GB
Video Card: Nvidia 7300 gt 512 MB ram PCIe
Sound Card: Onboard sound - ADI AD1986A
HD: 250 GB
Remote: Snapstream Firefly RF
Tuners: DVico FusionHDTV5 Gold
Monitor: LG 42LC7D 42"

This is my Xorg.conf file:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "LIRC-Mouse"
        Driver      "mouse"
        Option      "Device" "/dev/lircm"
        Option      "Protocol" "IntelliMouse"
        Option      "SendCoreEvents"
        Option      "Buttons" "5"
        Option      "ZAxisMapping" "4 5"
EndSection

Section "Device"
	Identifier	"nVidia Corporation G70 [GeForce 7300 GT]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
	Option 		"UseEvents" 	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce 7300 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"LIRC-Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

---

