---
title: "Hardy Heron upgrade + Video Playback Problem"
date: 2008-05-01
forum: Multimedia Software
---

### Post by tenchu77491 on 2008-05-01
I updated from 7.10 to 8.04. Before the update everything was fine. 

Specs: 

7.10 --> Updated
Compaq V2000
ATIX200M Graphics Card
AMD64 Processor
Sound is working fine (I think, except the fact that XMMS will not work)


//////
// Problem One
//
Now my MPlayer can not play any videos (except .flvs and a few .avis), all MPEG files and big files will not play correctly because of huge lag spikes every few seconds. Here is my MPlayer config

# Specify default video driver (see -vo help for a list).
vo=xv

# Specify default audio codec (see -ac help for a list).
#ac=mad,

# Specify default audio driver (see -ao help for a list).
ao=alsa,

##################
# other settings #
##################

# Drop frames to preserve audio/video sync.
framedrop = yes

#Screensaver support (for non gmplayer)
stop-xscreensaver = "yes"

#Disable joystick support
nojoystick = yes

# Use this for a widescreen monitor, non-square pixels.
#monitoraspect=16:9
aspect=16:9

mc=0 # Time to correct, fix sync problem... maybe?
autosync=30 # fix sync problem... maybe?

# Change to a different videomode when going fullscreen.
vm=yes


//////
// Problem Two
//
It seems like my whole laptop is now working with very choppy graphics.... it doesn't claim there is any problem but I can feel the difference! I even get a lag when I scroll down a big Mozilla page.... here is some info

$ glxinfo | grep render
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect


# xorg.conf (xorg X Window System server configuration file)
#

Section "Files"
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
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
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
	Identifier	"ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)"
	Driver		"fglrx"
	Busid		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "ServerFlags"
    Option      "blank time" "0"
    Option      "standby time" "0"
    Option      "suspend time" "0"
    Option      "off time" "0"
EndSection
Section "Extensions"
	Option		"Composite"	"1"
EndSection

---

### Post by mc4man on 2008-05-01
ck. here
[http://ubuntuforums.org/showthread.php?t=765565](http://ubuntuforums.org/showthread.php?t=765565)

---

### Post by mrsteveman1 on 2008-05-01
Do you get these same problems if you boot the gutsy kernel? it should still be there

---

### Post by tenchu77491 on 2008-05-01
That link helped me fix the overall sluggish speed of my graphics. 


EDIT: 

I did all of the steps on that link and now my MPlayer works fine in fullscreen mode but in window it is just a blue box.... what the heck could the problem be?

- x11 output works in window mode and fullscreen mode = not changing resolution (not stretching)
- all other outputs work perfect in fullscreen and not in window

Errr, simple to fix with 

zoom="1" #Allow sofware scaling if I use x11 for vo
vo=x11

However I dont want to eat up CPU but it seems to run pretty normal...

---

