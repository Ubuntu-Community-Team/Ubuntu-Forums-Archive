---
title: "Matrox G450 Dual Head extended display"
date: 2007-07-09
forum: Multimedia &amp; Video
---

### Post by Roman78 on 2007-07-09
Hello everybody.

I just installed Ubuntu 7.04 on my machine after i updated it whit a Matrox Millenium G450 Dual Head video card. I also have 2 17" screens, but on both screen i see the same and not an extended (like i want to). How can i activate extended screen?

---

### Post by Roman78 on 2007-07-09
Now i downloaded the linux-driver from Matrox.com, but when i try to install it gives the following message:

```

[: 43: ==: unexpected operator
install.sh: 57: function: not found
install.sh: 69: function: not found
install.sh: 78: function: not found
install.sh: 95: function: not found
install.sh: 141: function: not found
[: 178: ==: unexpected operator
[: 178: ==: unexpected operator
[: 178: ==: unexpected operator
[: 178: ==: unexpected operator
[: 178: ==: unexpected operator
-e \E[31mERROR: The X server drivers included in this installation package
-e        do not support the current version of your X server.

```

in the readme.txt is written that i neex xFree86 4.3.0 and X.org versions 6.7.0, 
6.8.0, 6.8.1, 6.8.2, 6.9.0, 7.0.0. But what version is ubuntu 7.04?

---

### Post by Roman78 on 2007-07-09
Now i tried the MergedFB methode, but it still don't work.  Here's a dump from my xorg.conf:

```


Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

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

Section "Device"
	Identifier	"Matrox Graphics, Inc. MGA G400/G450"
	Driver		"mga"
	BusID		"PCI:1:0:0"
	Option		"OldDmaInit"		"True"
	Option "MergedFB" "true" #Enable MergedFB function
  	Option "MonitorLayout" "CRT,CRT" # LVDS = Laptop Screen, TMDS = DVI Port, CRT = VGA Port NOT MONITOR TYPE!
  	Option "CRT2Hsync" "30-65" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
  	Option "CRT2VRefresh" "50-75" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
  	Option "OverlayOnCRTC2" "true"
  	Option "CRT2Position" "RightOf" #Physical location of your secondary monitor in relationship to your primary monitor. Values can be: LeftOf, RightOf, Above, Below, and Clone.
  	Option "MetaModes" "1280x1024-1280x1024" #Monitor Resolutions for Primary-Secondary monitors 
#Option "MergedXineramaCRT2IsScreen0" "true" #determines which screen is going to be the primary screen; value can be "true" or "false"
EndSection

Section "Monitor"
	Identifier	"DELL E172FP"
	Option		"DPMS"
	Horizsync    28-64 #You may wish to change the values to fit your specific monitor
    	Vertrefresh    43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Matrox Graphics, Inc. MGA G400/G450"
	Monitor		"DELL E172FP"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

