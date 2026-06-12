---
title: "different resultions with fglrx on laptop-lcd and external DVI-TFT"
date: 2006-02-25
forum: Multimedia &amp; Video
---

### Post by cage on 2006-02-25
Hello!

I've got the following problem:
I just bought a new 19"-DVI-TFT and would like to see the same content on this one as on the internal LCD - a cloned display. The laptop-lcd has a resolution of 1400x1050 and the external TFT 1280x1024. The driver is "fglrx", graphicscard is a mobility radeon 9000 (M10) inside a acer travelmate 8000 laptop.
Despite googling and trying for hours I can't get it working - only with the same resolution on both monitors (1400x1050 OR 1280x1024 on both of them).

But there are people who got it to work (e.g. [http://www.smop.co.uk/node/60](http://www.smop.co.uk/node/60), but here with the radeon-driver. doesn't work for me... stripes) 
fglrxconfig doens't help either, although there is the option "3.  Clone Mode    (2 screens - same content, allows for different refresh rates/resolutions)" the external TFT remains blank.

Here an example of xorg.conf resulting in the same resolutions on both monitors:
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
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	#Identifier	"ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
	Identifier	"ati_intern"
	Driver		"fglrx"
	#Driver		"radeon"	

	BusID		"PCI:1:0:0"
	Option		"VideoOverlay" 		"on"
	Option		"OpenGLOverlay"		"off"
        Option 		"AGPMode" "4"
        Option 		"AGPFastWrite" "true"
        Option 		"BusType" "PCIE"
        Option 		"MonitorLayout" 	"LVDS, AUTO"
	Option		"DesktopSetup"		"clone"
        Option "EnablePageFlip" "true"

	Option		"MetaModes"	"1400x1050-1280x1024"
	#Screen		0
EndSection

Section "Monitor"
	Identifier	"lcd_intern"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"screen_intern"
	Device		"ati_intern"
	Monitor		"lcd_intern"
	DefaultDepth	24

	SubSection "Display"
		Depth		24
		Modes		"1400x1050" "1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"screen_intern"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

And here a configuration which should result in two different resolutions - but the external monitor remains dark

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
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	#Identifier	"ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
	Identifier	"ati_intern"
	Driver		"fglrx"
	#Driver		"radeon"	

	BusID		"PCI:1:0:0"
	Option		"VideoOverlay" 		"on"
	Option		"OpenGLOverlay"		"off"
        Option 		"AGPMode" "4"
        Option 		"AGPFastWrite" "true"
        Option 		"BusType" "PCIE"
        Option 		"MonitorLayout" 	"LVDS, TMDS"
	Option		"DesktopSetup"		"clone"
        Option 		"EnablePageFlip" "true"

	Option		"MetaModes"	"1400x1050-1280x1024"
	Screen		0
EndSection

Section "Device"
	Identifier	"ati_extern"
	Driver		"fglrx"
	#Driver		"radeon"

	Screen		1
EndSection

Section "Monitor"
	Identifier	"lcd_intern"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"tft_extern"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"screen_intern"
	Device		"ati_intern"
	Monitor		"lcd_intern"
	DefaultDepth	24

	SubSection "Display"
		Depth		24
		#Modes		"1400x1050" "1280x1024"   #it works with this line, but then I get the same resolution on both monitors again
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"screen_extern"
	Device		"ati_extern"
	Monitor		"tft_extern"
	DefaultDepth	24

	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"screen_intern"
	Screen 		"screen_extern" RightOf "screen_intern"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

The corresponding Xorg.0.log doesn't get me further...

I hope someone can help me here, cause I really got stuck!
Thanks in advance and sorry for my poor english.
  
Carsten

---

