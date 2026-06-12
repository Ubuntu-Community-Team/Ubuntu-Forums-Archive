---
title: "8600 GTS video playback issues"
date: 2009-03-08
forum: Multimedia Software
---

### Post by guitarj1d on 2009-03-08
I just recently put together a new system.  I've been having trouble with the config of my 8600 gts graphics card.  The main problem I've noticed is video playback.  Playing back any quality of video results in refresh lines when there is any motion on the screen. 

I let Intrepid install the driver(177) and all of the settings look correct in NVIDIA X Server Settings(1920x1080@60), but in System>Preferences>Screen Resolution, it shows a refresh rate of 50.

So, two questions
What is the true refresh rate?
Does this problem seem to be a refresh issue or a driver issue?

I've pasted the output of /etc/X11/xorg.conf below(it's not very verbose)

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

---

