---
title: "No Video playback w/dual-head(xrandr) Radeon Mobility 9000"
date: 2007-11-22
forum: Multimedia &amp; Video
---

### Post by Scothiam on 2007-11-22
Hello everyone!
I've just succesfully got dual-head working on my Dell 600m laptop with ATI radeon mobility 9000 (64mb) by following the instructions here [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)
However,  no I have lost video play back.  Video appz return an error ala "could not open file" or simple crash/go-away.  

Dual display is more important than video playback, but would be nice to have both.
Cheers,

note: I'm using a bash session/script to run a xrandr command to get the second display working the way I want, 
> #!/bin/sh

xrandr  --output VGA-0 --mode 1280x1024 --pos 1024x0

My xorg file is as follows (removed input devices...) 
> 
Section "Device"
	Identifier	"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
		# ADD A VIRTUAL LINE TO PROVIDE FOR THE LARGEST SCREENS YOU WILL HOTPLUG 
           	Virtual              2304 2048
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection


---

