---
title: "ATI video card - cpu runs about 100%  with basic games"
date: 2008-07-31
forum: Multimedia Software
---

### Post by erfahren on 2008-07-31
Ubuntu 8.04

I have an ATI video card (listed in my signature) and am using the fglrx driver available from the repos - no desktop effects enabled

when running a basic opengl game (such as Scorched3D) in a 800x600 window my cpu runs at about 100% and gets to the point of overheating

I think there are some additional settings that could be put in my xorg.conf but am unsure what to try (Load "dri" perhaps?)

here's the relevent sections of my xorg.conf (I just left out keyboard, mouse, and touchpad sections)
```

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
        Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection

```
I inserted the "Option "VideoOverlay" "on" & Option "OpenGLOverlay" "off" - options from the [Unofficial Wiki for the ATI Linux Driver]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide") guide but I didn't notice any difference.

I really didn't have this problem (so much) with Feisty (the last Ubuntu version that worked really well for me) so I would think I'd be able to make it a little better,

anyone have any ideas? - thanks

---

