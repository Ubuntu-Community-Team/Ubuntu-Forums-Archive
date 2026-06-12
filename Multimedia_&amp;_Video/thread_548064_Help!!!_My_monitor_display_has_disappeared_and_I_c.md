---
title: "Help!!! My monitor display has disappeared and I can't see anything!!!"
date: 2007-09-10
forum: Multimedia &amp; Video
---

### Post by teejay17 on 2007-09-10
I use Kubuntu 7.04, and I went to "detect monitor" under "Monitor & Display" settings to see if I could get a better resolution. Now that I've rebooted, I am no longer in range and my screen is blank. 
I can't even see anything to get back to my old setting. 
Is there a "safe graphics" mode or something? How do I get my display back?
I won't be able to use my computer again until this problem is fixed.

---

### Post by grimmson on 2007-09-10
This may be hitting a nail with a sledge hammer but you may try dpkg-reconfigure xserver.xorg when booting into recovery mode (study reconfigure xserver.xorg if necessary). Not sure of your experiance level but sounds like a glitch where no monitor resolutions were saved because no monitor was found. be for you try dpkg , type "sudo nano /etc/X11/xorg.conf" . Hopefully you've played with xorg.conf. If not page down in the file **Section "Screen"** portion. Notice color depth and resolutions. Only possible combinations will be listed here. Here is a copy of my xorg for refrance. Good luck and post again if necessary.

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
	Load	"bitmap"
	Load	"ddc"
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
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Identifier	"Generic Video Card"
	Driver	"fglrx"
	Option	"VideoOverlay" "on"
	Option	"OpenGLOverlay" "off"
	BusID		"PCI:3:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x800" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x800" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x800" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x800" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x800" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x800" "1152x768" "1024x768" "800x600" "640x480"
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





Section "Extensions"
	Option "Composite" "Disable"
EndSection
```

---

### Post by teejay17 on 2007-09-11
I have never worked with  xserver.xorg before. It looks pretty overwhelming. 
Isn't there a way to just revert back to my setup that I had before? Something like a safe graphics mode, so that I can make out what I'm doing and fix the problem graphically?

---

### Post by teejay17 on 2007-09-11
bump

---

### Post by grimmson on 2007-09-17
Sorry for not getting back sooner (Im a truck driver.)  No revert that I'm aware of. I'm afraid a look at /etc/X11/xorg.conf is a good first step if you havent reinstalled already. If dual booting or using a seperate pc just print a copy of my posted xorg and compare it with yours to start. anything looks fishy post results and we (I'll) get back with you asap. Sorry again for the delay. 
p.s. xorg looks busy but it's a rather simple and logical configuration file. Lets say its like the BIOS for Gnome windows manager. A entry level understanding of this file ( and how to fix it) is very helpful to us new linux users. Good luck and plow in.

---

### Post by ezeze5000 on 2007-09-18
I only have one problem with Ubuntu 7.04, Feisty Fawn.

If my PC is idle for extended periods, the screen goes dark and the screen resolution
goes way out of range of my monitor.

The only way I can recover is to shut down by pushing and holding the on/off button in until
it shuts down. Then I reboot and all is fine.

Might there be a fix for this?


Thanks.

---

