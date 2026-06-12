---
title: "TwinView with GeForce FX 5900XT"
date: 2005-10-13
forum: Multimedia &amp; Video
---

### Post by kiwifish on 2005-10-13
This question has been asked and answered before, but after hours with my xorg.conf file, I have still had no luck. I have a philips flatscreen and a dell crt, both plugged into my graphics card with VGA cables. I have installed the nvidia-glx driver using apt. Both monitors show ubuntu booting up, then the Nvidia logo appears on my main monitor when X starts, and my secondary monitor goes blank, and stays blank. Does anyone have an idea about what I'm doing wrong? :confused:  My xorg.conf file currently looks like:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
	# Load 	"dbe"

EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
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
	Identifier	"NVIDIA Corporation NV35 [GeForce FX 5900XT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"TwinView"
	Option		"ConnectedMonitor" "CRT, CRT"
	Option		"SecondMonitorHorizSync" "30-82"
	Option		"SecondMonitorVertRefresh" "56-76"
	Option		"MetaModes" "1280x1024;"
	Option		"TwinViewOrientation" "RightOf"
EndSection

Section "Monitor"
	Identifier	"Philips 170B4"
	Option		"DPMS"
	HorizSync 	30-82
	VertRefresh 	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV35 [GeForce FX 5900XT]"
	Monitor		"Philips 170B4"
	DefaultDepth	24
	Subsection "Display"
		Depth 24
		Modes "1280x1024"
	EndSubsection
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

Thanks!!!

---

### Post by kiwifish on 2005-10-13
Yay! I worked it out. After spending a week on this, 5 minutes after I post to the forum, I get it working. For anyone having the same trouble as me, my problem was in the "MetaModes" line, which is a set of modes that describe the resolutions of both screens, in my case i have one which displays both monitors at 1280x1024 and another which turns off the second monitor and keeps the first at 1280x1024. These metamodes must coincide with the "Modes" line in the display subsection, which tell X the total size of both screens. Here's my working config:

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
	# Load 	"dbe"

EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
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
	Identifier	"NVIDIA Corporation NV35 [GeForce FX 5900XT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"TwinView" "true"
	Option      	"RenderAccel" "true"
        Option      	"UseEdidFreqs" "true"
	Option		"ConnectedMonitor" "CRT-0, CRT-1"
	Option		"MetaModes" "1280x1024,1280x1024;1280x1024,NULL;"
	Option		"TwinViewOrientation" "RightOf"
EndSection

Section "Monitor"
	Identifier	"Philips 170B4"
	Option		"DPMS"
	HorizSync 	30-82
	VertRefresh 	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV35 [GeForce FX 5900XT]"
	Monitor		"Philips 170B4"
	DefaultDepth	24
	Subsection "Display"
		Depth 24
		Modes "2560x1024" "1280x1024"
	EndSubsection
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

### Post by mattsm8 on 2005-10-23
hey kiwifish, I also had some trouble with this, but found out that all you need is 4 simple steps for the entire installation, I wrote it down here: [http://www.glawing.com/forum/viewtopic.php?t=14]("http://www.glawing.com/forum/viewtopic.php?t=14")
cheers
/mattsm8

---

