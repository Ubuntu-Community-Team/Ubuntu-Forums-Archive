---
title: "Dual Monitor Issues"
date: 2007-07-26
forum: Multimedia &amp; Video
---

### Post by hntd187 on 2007-07-26
Hi, I am using a Dell 1907FP and a Dell 1908FP (I have no idea if they are any different) and a Radeon X800XL for the life of me I can't get my second monitor to show up. It can mouse over to the second monitor and some programs even launch to the second monitor! but I can't get any display on it. The video card is a dual head DVI. Here is my xorg.conf file...

```

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
	Identifier	"0 ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen		0 
	Option 		"DCCMode" "True"
	Option		"MonitorLayout" "TMDS"
EndSection

Section "Device"
	Identifier	"1 ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen		1
	Option		"DCCMode" "True"
	Option		"MonitorLayout" "TMDS"
EndSection

Section "Monitor"
	Identifier	"0 DELL 1907FP"
	Option		"DPMS"
	#Screen		0
EndSection
Section "Monitor"
	Identifier	"1 DELL 1908FP"
	Option		"DPMS"
	#Screen		1
EndSection
Section "Screen"
	Identifier	"Main Screen"
	Device		"0 ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Monitor		"0 DELL 1907FP"
	DefaultDepth	24
	#Screen		0
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Second Screen"
	Device		"1 ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Monitor		"1 DELL 1908FP"
	DefaultDepth	24
	#Screen		1
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0 "Main Screen"
	Screen		1 "Second Screen" RightOf "Main Screen"
	Option "Xinerama" "true"
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

### Post by hedgefighter on 2007-07-27
I didn't see anything wrong with your configuration (though there could be), but I had the same problem with my Radeon. I could not get dual head to work despite my best effort. I just decided to give up and buy an nVidia. The nVidia drivers actually work in 3d (so you can have Beryl, Compiz, etc.) and come with a nice configuration program to setup things like dual monitors. Good luck with that though, hopefully you can succeed where I couldn't.

---

