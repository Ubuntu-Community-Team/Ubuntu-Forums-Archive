---
title: "Multi Monitor Blues"
date: 2007-05-01
forum: Multimedia &amp; Video
---

### Post by lordjoe_com on 2007-05-01
The major barrier I find to converting my primary desktop from Windows XP to Fiesty Faun Ubuntu is support for multiple screens and monitors. 
I have 3 monitors - two on a Matrix G550 AGP card and one on an Nides GXForce 5500. All run at 1280x1024 on windows xp. 
On unbuntu (feisty faun) I can only get the single monitor attached to the NVidea running. If I force the screen size to 1280x1024, the display is too high for the screen and the lower toolbar does not show - as if the controller was not set to that resolution. Thus I have a single monitor working st a resolution of 1024x780. 
I am not sure what version of the drivers I am using - I think the ones in the Feisty Faun distro and am enough of a Newbie to be unsure how to updat them.

My xorg.conf file follows - any help wpuld be greatly appreciated

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
	Identifier	"nVidia Corporation NV34 [GeForce FX 5500]"
	Driver		"nv"
	BusID		"PCI:0:8:0"
 Screen      0
EndSection

Section "Device"
Identifier    "Matrox Graphics, Inc. MGA G550 AGP"
Driver        "mga"
 BusID        "PCI:1:00.0"
 Screen      1
EndSection


Section "Monitor"
	Identifier	"First Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Monitor"
	Identifier	"Second Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Monitor"
	Identifier	"Third Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5500]"
	Monitor		"First Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1024x768" 
	EndSubSection
EndSection

Section "Screen"
    Identifier    "Second Screen"
    Device        "Matrox Graphics, Inc. MGA G550 AGP"
    Monitor        "Second Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        24
        Modes        "1280x1024"
    EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
   	Screen        0   "Default Screen"
    	Screen       1   "Second Screen" RightOf "Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	Option "Xinerama" "true"
EndSection

Section "ServerFlags"
Option "Xinerama" "0"
EndSection


Section "DRI"
	Mode	0666
EndSection

---

