---
title: "Xinerama error when starting XBMC"
date: 2008-08-05
forum: Multimedia Software
---

### Post by Ub_newb on 2008-08-05
I recently dusted off my old Ubuntu box to give the Linux port of XBMC a try. Before I get into my problem, here's some background. I'm using a Dell Dimension 8200 with a P4 and an Nvidia 6200 LE. I hadn't used it for a while, so it still had Feisty on it, and I upgraded to Hardy Heron by going through the update manager twice.

Anyway, after adding the appropriate repositories and installing XBMC through apt, I ran into a snag. When I try to start XBMC a screen pops up for a fraction of a second, and then disappears, and I am left with this error: 
> 
db@db-desktop:~$ xbmc
Xlib:  extension "XINERAMA" missing on display ":1.0".
The XBMC_HOME environment variable is not set.
The XBMC_HOME environment variable is not set.
Segmentation fault


I've searched around and couldn't find a thread where anyone had experienced something similar. My understanding is that "Xinerama" is something for dual monitors, however I'm only using one so I'm not sure why I'm getting this error. 

I'm using the restricted driver from the built-in Hardware Drivers function. Also, I have a feeling this will come into play, so here is what my xorg.conf looks like:

> 
Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation GeForce 6200 A-LE"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Q19wb"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation GeForce 6200 A-LE"
	Monitor		"Q19wb"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1440x1440"	"1280x1024"	"1280x960"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1440x1440"	"1280x1024"	"1280x960"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1440x1440"	"1280x1024"	"1280x960"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1440x1440"	"1280x1024"	"1280x960"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1440x1440"	"1280x1024"	"1280x960"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1440x1440"	"1280x1024"	"1280x960"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


Is there a problem with my display settings? Can someone shed any light on this? I would be really grateful for any help that anyone could provide.

Thanks in advance.

---

### Post by Ub_newb on 2008-08-07
I guess there aren't many people interested, but I've got a lot of help by searching these forums so I'll keep updating this post if I find a solution.

So far I tried using a more up to date video driver by installing through envy, and I've had the same problem.

Someone over at xbmc.org suggested that I try a newer version of xbmc. I'm at work now but I'll try that later tonight and post the results.

---

### Post by Ub_newb on 2008-08-08
I found a solution. Apparently the DISPLAY environment variable had to be set to 0.0 instead of 1.0. So, after updating XBMC to the latest svn build, I simply ran:
> export DISPLAY=:0.0


Everything seems to work fine now.

---

### Post by Trejep on 2008-09-19
Thanks that works if I set the environmental variable from a terminal and then run XBMC from the terminal...but how do I make it so that I can run XBMC from the application menu?  I tried editing my .bashrc and placing export DISPLAY=:0.0 but the problem still exists.
Thanks for any help.

---

