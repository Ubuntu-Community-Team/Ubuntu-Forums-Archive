---
title: "thinkpad T60 Ati X1400 dual monitor problem"
date: 2007-11-28
forum: Multimedia &amp; Video
---

### Post by mstfck on 2007-11-28
I have tried many tings but I could not get dual-monitor work with T60. 
Second monitor is a Dell 24" monitor. 

Here is my xorg.conf. When I start X, then I get login window. When I login, then it takes some time and then X restarts and I get back to login window.

Could someone check what is wrong with it?



Section "Device"


	Identifier	"ati0"

	Driver		"fglrx"

	BusID		"PCI:1:0:0"


	Screen		0

EndSection



Section "Device"


	Identifier	"ati1"

	Driver		"fglrx"

	#Driver		"radeon"

	BusID		"PCI:1:0:0"

	Screen		1

EndSection



Section "Monitor"

	Identifier	"ThinkPad"

	Option		"DPMS"

EndSection



Section "Monitor"

	Identifier	"Dell"

	Option		"DPMS"

EndSection



Section "Screen"


	Identifier	"screen0"


	Device		"ati0"

	Monitor		"ThinkPad"

	DefaultDepth	24

	SubSection "Display"

		Depth		24

		Modes		"1400x1050"

	EndSubSection

EndSection



Section "Screen"

	Identifier	"screen1"

	Device		"ati1"

	Monitor		"Dell"

	DefaultDepth	24

	SubSection "Display"

		Depth		24

		Modes		"1920x1200"

	EndSubSection

EndSection


Section "ServerLayout"

	Identifier	"Multihead"

	Screen		"screen0"

	Screen		"screen1" RightOf "screen0"

	InputDevice	"Generic Keyboard"

	InputDevice	"Configured Mouse"

	InputDevice     "stylus"	"SendCoreEvents"

	InputDevice     "cursor"	"SendCoreEvents"

	InputDevice     "eraser"	"SendCoreEvents"

	InputDevice	"Synaptics Touchpad"

	Option		"Xinerama"

EndSection



Section "DRI"

	Mode	0666

EndSection

---

