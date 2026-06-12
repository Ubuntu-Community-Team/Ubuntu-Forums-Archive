---
title: "Radeon 9250 Dual Head/Monitor on One Card not working"
date: 2005-10-24
forum: Multimedia &amp; Video
---

### Post by camj on 2005-10-24
Im having heaps of issues with my Radeon 9250 using Dual Head with two monitors..

Everything I try I get "cloned" monitors and not a desktop spanned accross two monitors..

Im using two CRT monitors connected to a powercolor 9250, one via a normal vga connector, one via a normal vga connector to a vga to dvi connector.

Im using Ubuntu 5.10, and my X.org conf file follows..

```

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	Option	    "dpms"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	Option	    "dpms"
EndSection

Section "Device"
	Identifier  "Videocard0"
	Driver      "radeon"
	BusID       "PCI:1:0:0"
	Screen 0
EndSection

Section "Device"
	Identifier  "Videocard1"
	Driver      "radeon"
	BusID       "PCI:1:0:1"
	Screen      1
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Videocard0"
	Monitor		"Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection


Section "Screen"
	Identifier	"Screen1"
	Device		"Videocard1"
	Monitor		"Monitor1"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Group        0
	Mode         0666
EndSection

Section "ServerLayout"
	Identifier     "Multihead layout"
	Screen      0  "Screen0" LeftOf "Screen1"
	Screen      1  "Screen1" 0 0
	InputDevice    "Configured Mouse" "CorePointer"
	InputDevice    "Generic Keyboard" "CoreKeyboard"
	Option	    "Xinerama" "on"
	Option	    "Clone" "off"
EndSection

```

Thanks!!

---

### Post by gherikill on 2005-10-24
I would also like to know this.  I had it working with SUSE before and linux uses a different desktop for each display rather than spanning.

---

### Post by camj on 2005-10-24
[QUOTE=gherikill]I would also like to know this.  I had it working with SUSE before and linux uses a different desktop for each display rather than spanning.[/QUOTE]

Im pretty sure Xinerama is what your looking for, but unfortunately, its not supported by fglrx so you'll either have to sacrifice 3D support and go with the opensource drivers or choose to use seperate desktops instead of spanning :(

Guys/Gals, I still havent fixed my problem and its driving me bonkers.

Should I just rule out that dual displays in Ubuntu doesnt work, or is incredibly hard to accomplish?

---

### Post by camj on 2005-10-25
I gave up and installed Fedora Core 4 which worked perfectly

---

### Post by Leopard on 2005-10-27
[QUOTE=camj]Im pretty sure Xinerama is what your looking for, but unfortunately, its not supported by fglrx so you'll either have to sacrifice 3D support and go with the opensource drivers or choose to use seperate desktops instead of spanning :(

Guys/Gals, I still havent fixed my problem and its driving me bonkers.

Should I just rule out that dual displays in Ubuntu doesnt work, or is incredibly hard to accomplish?[/QUOTE]
It's certainly one of those things that windows makes easy.  Some of my xorg.conf is in here:

[http://www.ubuntuforums.org/showthread.php?p=447036&posted=1#post447036](http://www.ubuntuforums.org/showthread.php?p=447036&posted=1#post447036)

note this is with the default drivers that came with Ubuntu.  Upgrading those is my next job, along with installing codecs.

Edit:  I made mine easier to troubleshoot by giving the monitors and screens the same names.  Then it was all the ServerLayout section that needed tweaking.

---

### Post by pauljwells on 2005-11-09
I got twin monitors to work quite easily with the fglrx xorg driver in the breezy multiverse repository. (Unlike in Hoary, for which I had to download the driver direct from ATI). Best results are with the 'OneBigDesktop' arrangement - actually having two separate X sessions tended to cause a lot of gnome panel crashes.

here's my xorg.conf. Note that you DON'T want to call xinerama as it's incompatible with the ATI driver.

For BigDesktop - Note that instead of the 'LeftOf..' screen layout there is an option called 'DesktopSetup' - if you get the monitors on the wrong side change this to "0x00000000" 

```
Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	SubSection "extmod"
		Option "omit xfree86-dga"
	EndSubSection
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
	Load	"GLcore"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X600 (RV370)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"UseInternalAGPGART"	"no"
	Option		"no_accel"		"no"
	Option		"no_dri"		"no"
	Option		"mtrr"			"off"
	Option		"DesktopSetup"	"0x00000200"
	Option		"MonitorLayout"	"AUTO, AUTO"
	Option		"IgnoreEDID"		"off"
	Option		"NoTV"			"no"
	Option		"TVStandard"		"PAL-I"
	Option		"TVHSizeAdj"		"0"
	Option		"BlockSignalsOnLock"	"on"
	Option		"VideoOverlay"		"on"
	Option		"OpenGLOverlay"		"off"
	Screen 		0
EndSection

Section "Monitor"
	Identifier	"HP vs17-0"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"HP vs17-1"
	Option		"DPMS"
EndSection


Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon X600 (RV370)"
	Monitor		"HP vs17-0"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

and for dual monitor
```
Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	SubSection "extmod"
		Option "omit xfree86-dga"
	EndSubSection
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
	Load	"GLcore"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X600 (RV370)0"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"UseInternalAGPGART"	"no"
	Option		"no_accel"		"no"
	Option		"no_dri"		"no"
	Option		"mtrr"			"off"
	Option		"DesktopSetup"	"0x00000200"
	Option		"MonitorLayout"	"AUTO, AUTO"
	Option		"IgnoreEDID"		"off"
	Option		"NoTV"			"no"
	Option		"TVStandard"		"PAL-I"
	Option		"TVHSizeAdj"		"0"
	Option		"BlockSignalsOnLock"	"on"
	Option		"VideoOverlay"		"on"
	Option		"OpenGLOverlay"		"off"
	Screen 		0
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X600 (RV370)1"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Screen 		1
EndSection


Section "Monitor"
	Identifier	"HP vs17-0"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"HP vs17-1"
	Option		"DPMS"
EndSection


Section "Screen"
	Identifier	"Screen0"
	Device		"ATI Technologies, Inc. Radeon X600 (RV370)0"
	Monitor		"HP vs17-0"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"ATI Technologies, Inc. Radeon X600 (RV370)1"
	Monitor		"HP vs17-1"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen0"
	Screen		"Screen1" RightOf "Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
 
```

---

### Post by pvonk on 2005-11-19
pauljwells, thanks to you it was a breeze to setup. =D> :KS 

Here's my driver info (9600 XT) and xorg.conf for BigDesktop setup if anyone else runs into trouble:

```
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)
```

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
  	SubSection "extmod"
    	    Option "omit xfree86-dga"
  	EndSubSection
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9600 XT (RV350 AR)"
	Driver		"fglrx"
	BusID		"PCI:2:0:0"
	Option		"UseInternalAGPGART"	"no"
	Option		"no_accel"		"no"
	Option		"no_dri"		"no"
	Option		"mtrr"			"off"
	Option		"DesktopSetup"	"0x00000200"
	Option		"MonitorLayout"	"AUTO, AUTO"
	Option		"IgnoreEDID"		"off"
	Option		"NoTV"			"yes"
	Option		"TVStandard"		"PAL-B"
	Option		"TVHSizeAdj"		"0"
	Option		"BlockSignalsOnLock"	"on"
	Option		"VideoOverlay"		"on"
	Option		"OpenGLOverlay"		"off"
	Screen 		0
EndSection

Section "Monitor"
	Identifier	"VG712b-0"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Monitor"
	Identifier	"VG712b-1"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9600 XT (RV350 AR)"
	Monitor		"VG712b-0"
	DefaultDepth	24

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
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by cyber pete on 2007-05-22
I'm pulling my hair out here. Can anyone tell me what my xorg.conf should look like to support dual monitors? i REALLY  want to get off of Windows but I need my dual monitors to do it! 
Here is my setup configuration. 


DELL OPTIPLEX GX620
ATI RADEON X600
MONITOR1: DELL 1907FP
MONITOR2: DELL 1704FP

Here is what my current xorg.conf looks like.

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Identifier	"ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
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

### Post by cyber pete on 2007-05-22
Woohoo! Sorry I  searched and got it working with this thread: [http://ubuntuforums.org/showthread.php?t=301941&highlight=dual+ati+600](http://ubuntuforums.org/showthread.php?t=301941&highlight=dual+ati+600)

---

