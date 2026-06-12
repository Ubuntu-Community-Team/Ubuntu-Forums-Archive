---
title: "TV out problems"
date: 2005-11-16
forum: Multimedia &amp; Video
---

### Post by Beau on 2005-11-16
Hello,

I followed the TV out guide, creating a second screen/device/monitor.
X starts up fine but the TV stays blank. 

Here is my xorg.conf file:

```


Section "Files"
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
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"be"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
        Option          "Buttons"               "9"
	Option		"Reslution"             "100"
	Option		"ZAxisMapping"		"8 9"
	Option 		"Emulate3buttons"	"false"
EndSection



Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Driver		"nvidia"
        Screen 0
	Option "NoLogo" "true"
	Option "RenderAccel" "true"
	BusID		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"TV"
	Driver "nvidia"
	Screen 1
	Option "TVOutFormat" "COMPOSITE"
	Option "TVStandard" "PAL-B"
	Option "ConnectedMonitor" "Television"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-130
	VertRefresh	50-160
EndSection

Section "Monitor"
	Identifier "Television"
	HorizSync 50
	VertRefresh 30-150
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device	"TV"
	Monitor "Television"
	DefaultDepth 24
	Subsection "Display"
		Depth 24
		Modes "640x480"
	EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"Basic Layout"
	Screen 0	"Screen0"
	Screen 1	"Screen1" rightof "Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection



```

Any ideas what could be wrong? 
Thanks,
Beau

---

