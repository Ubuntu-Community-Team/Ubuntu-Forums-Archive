---
title: "DVD playback on Toshiba Portege 7020CT"
date: 2007-07-23
forum: Multimedia &amp; Video
---

### Post by serfcx on 2007-07-23
Managed to install Xubuntu Feisty on this old laptop with certain success after changing the xserver to 16 bit depth I can run at 1024 x 768.
The only outstanding problem I have is trying to get decent DVD playback through the dvd drive on the dock.
I have managed to get Xine to give me some form of playback using xshm as the video driver but cannot get it to be smooth - sound is OK.
I have searched the xine site and tried all listings of things to do when you have dropped frames.
Using xv as a driver just crashes xine with the error message below.

bill@tosh:~$ xine -V xv
This is xine (X11 gui) - a free video player v0.99.5cvs.
(c) 2000-2006 The xine Team.
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  2138
  Current serial number in output stream:  2139

Here is my xorg.conf for those with more knowledge than me.

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
	Option		"XkbLayout"	"gb"
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
	Identifier	"Neomagic Corporation NM2200 [MagicGraph 256AV]"
	Driver		"neomagic"
	BusID		"PCI:0:4:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Neomagic Corporation NM2200 [MagicGraph 256AV]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
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

I have also checked that the drive is set to DMA=1

Any "experts" out there ?

The laptop did apparently play DVD's under Win XP or so the guy who gave it to me said !

---

### Post by benx009 on 2007-07-23
do you have the following installed?:
[B]
libdvdcss2
libdvdnav4
libdvdplay0
libdvdread3
[/B]

also, xine never really worked for me here in ubuntu.  why don't you try mplayer instead?  it's the best dvd player imho, and, plus, it's available in the ubuntu repos.

---

### Post by serfcx on 2007-07-23
> **benx009 said:**
> do you have the following installed?:
[B]
libdvdcss2
libdvdnav4
libdvdplay0
libdvdread3
[/B]

also, xine never really worked for me here in ubuntu.  why don't you try mplayer instead?  it's the best dvd player imho, and, plus, it's available in the ubuntu repos.

Yes I have them all installed.

Previously tried mplayer when I had Zenwalk installed on the Toshiba and it crashed all the time so that was why I started with Xine on Xubuntu.

Mplayer works well now after Xubuntu installed and can watch DVD with x11 driver - xv still crashes.

Thanks for the hint to try mplayer again.

---

### Post by KCAir on 2007-07-23
I had the same problem with mplayer on my Toshiba.   I reloaded it and it now works just fine.  Thanks for the advice.

---

### Post by benx009 on 2007-07-23
no problem

---

