---
title: "[SOLVED] Just purchased Nvidia card not seeing a big difference"
date: 2007-12-26
forum: Multimedia &amp; Video
---

### Post by highfructose327 on 2007-12-26
Just purchased Nvidia Geforce 8500 256mb, I was using a Ati Radeon X600 256mbcard not seeing a big difference. I am able to play games without switching form Compiz to Metacity thats nice. But  I am now having minor lag issues with effects in Compiz, I used loose bindings in the Fusion Icon that helped significantly but still a little lag. I feel like I am not taking advantage of something with the card but I am not sure what here is my Xorg.conf

```
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
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
	Identifier	"nVidia Corporation G80 [GeForce 8500 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option          "NoLogo"
EndSection

Section "Monitor"
	Identifier	"DELL E196FP"
	Option		"DPMS"
	HorizSync	31-80
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8500 GT]"
	Monitor		"DELL E196FP"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
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
EndSection
```

I put "nv" in  ```
/etc/default/linux-restricted-modules-common 
DISABLED_MODULES="nv"
```


Right now I am want to see if I can tweak the new card more  or if the gain is so small I should just return it. Any opinions, ideas tweaks would be great thanks!

---

### Post by mdpalow on 2007-12-26
Disappointing isn't it. I experienced the same thing a few weeks ago when I bought my new card.

I suspect you might not be a real power user (I'm not either) and for what you do on a day to day basis was probably handled fine with your old video card. I think perhaps any improvement might only be seen when running graphic intense applications (new games, large images, etc..).

---

### Post by highfructose327 on 2007-12-26
> I suspect you might not be a real power user (I'm not either) and for what you do on a day to day basis was probably handled fine with your old video card. I think perhaps any improvement might only be seen when running graphic intense applications (new games, large images, etc..).
 This what I thought may be the case, I guess it says as much about my use and  the maturity  of the open source drivers for the Radeon cards, that they can handle Compiz and my day to day use. When I started using Ubuntu that was not the case but in a years time there have definite improvements in Radeon support, I started in edgy and spent a good part of a day reading forums and such getting the card to even work. Then  I saw Beryl and went through the whole process again so I could get it running. But when I did a full install of Gusty I was running Compiz out of the box just added extra plugins and ccsm for Compiz that was pretty much it. I guess I thought I would notice some huge gain. I am interested to see what others have to say about it .  mdpalow thanks

---

### Post by mellowd on 2007-12-26
New games won't run too well on this card. The 8500 is quite low powered

---

