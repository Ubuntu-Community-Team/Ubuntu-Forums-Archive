---
title: "ATI Radeon 9000 TV-Out/Resolution strange problem"
date: 2007-07-01
forum: Multimedia &amp; Video
---

### Post by narandill on 2007-07-01
Hi, I have strange problem with TV-Out in radeon 9000 on ati driver. Direct rendering is ON just after i installed Ubutnu (ive also installed Compiz Fusion), TV-Out is working, but..... i can't change resolution on my Monitor (i have only 800x600). 

Monitor:
```
LCD AG Neovo F-419 on VGA
1280x1024 HS: 24-80 VS: 50-75
```
Plasma TV:
```
LG 42" on DVI-HDMI
852x480 50 i 60 Hz
```

Ofcorse if I add in Monitor section in xorg.conf:
```
Option "DDC" "False"
```
I can change my monitor resolution up to 1280x1024 but then i have no signal on my Plasma TV.

My xorg.conf (without DDC false):
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
	Option		"XkbLayout"	"pl"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
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
	Identifier	"ATI Technologies Inc Radeon RV250 If [Radeon 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"F-419"
	Option		"DPMS"
	HorizSync	24-80
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon RV250 If [Radeon 9000]"
	Monitor		"F-419"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
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

warnings and errors from xorg log:
```
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found

(WW) open /dev/fb0: No such file or directory
(WW) open /dev/fb1: No such file or directory
(WW) open /dev/fb2: No such file or directory
(WW) open /dev/fb3: No such file or directory
(WW) open /dev/fb4: No such file or directory
(WW) open /dev/fb5: No such file or directory
(WW) open /dev/fb6: No such file or directory
(WW) open /dev/fb7: No such file or directory

(EE) Unable to find a valid framebuffer device
(EE) RADEON(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
	(you may have to look at the server log to see warnings)
(WW) RADEON(0): fbdevHWInit failed, not using framebuffer device

(WW) RADEON(0): Mode 1280x1024 is out of range.
(WW) RADEON(0): Valid modes must be between 320x200-720x480
(WW) RADEON(0): Mode 1024x768 is out of range.
(WW) RADEON(0): Valid modes must be between 320x200-720x480
(WW) RADEON(0): Mode 800x600 is out of range.
(WW) RADEON(0): Valid modes must be between 320x200-720x480
```

---

### Post by narandill on 2007-07-01
*bump*

---

### Post by Hibbelharry on 2007-07-04
you don't have radeonfb loaded and used. Add a radeonfb line in /etc/initramfs-tools/modules, then rebuild your initrds with update-initramfs -u -k all. Then append video=radeonfb:xres*yres. This should remove your errors and will yield you a faster working  console. might also be a good idea to change usplash resolution after that to something appropiate in /etc/usplash.conf, which also requires rebuilding initrds.

Greetz
Hibbelharry

---

