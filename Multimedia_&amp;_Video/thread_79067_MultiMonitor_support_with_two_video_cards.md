---
title: "MultiMonitor support with two video cards"
date: 2005-10-19
forum: Multimedia &amp; Video
---

### Post by achaycock on 2005-10-19
I'm currently having a lot of trouble getting Ubuntu to support dual montiors. I've been trying to edit the xorg.conf file with the following result;

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
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
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
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"altwin:meta_win"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Screen		0
EndSection

Section "Device"
	Identifier	"Voodoo 3"
	Driver		"glide"
	BusID		"PCI:2:8:0"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Dell P1110-0"
	Option		"DPMS"
	HorizSync	30-121
	VertRefresh	48-160
EndSection

Section "Monitor"
	Identifier	"Dell P1110-1"
	Option		"DPMS"
	HorizSync	30-121
	VertRefresh	48-160
EndSection

Section "Screen"
	Identifier	"Primary Screen"
	Device		"NVIDIA Corporation NV40 [GeForce 6800 GT]"
	Monitor		"Dell P1110-0"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Secondary Screen"
	Device		"Voodoo 3"
	Monitor		"Dell P1110-1"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerFlags"
	Option 		"Xinerama" "ON"
EndSection

Section "ServerLayout"
	Identifier	"Dual Head Layout"
	 Screen 0 	"Primary Screen" 0 0
	Screen 1 	"Secondary Screen" RightOf "Primary Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection


At the moment nothing appears to be happening with the second monitor at all and I'm left simply exasperated. Can anyone see any obvious errors that I have made?

---

### Post by achaycock on 2005-10-19
I seem to have the answer now. This is my new xorg;

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

Section "Extensions"
	Option 	"Composite" "Enable"
	Option "RENDER" "Enable"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"altwin:meta_win"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option          "backingstore"              "true"
	Option 		"AllowGLXWithComposite" "1"
	Option 		"RenderAccel" "true"
EndSection

Section "Device"
	Identifier	"Voodoo 3"
	Driver		"vesa"
	BusID		"PCI:2:8:0"
EndSection

Section "Monitor"
	Identifier	"Dell P1110-0"
	Option		"DPMS"
	HorizSync	30-121
	VertRefresh	48-160
EndSection

Section "Monitor"
	Identifier	"Dell P1110-1"
	Option		"DPMS"
	HorizSync	30-121
	VertRefresh	48-160
	#Gamma 0.3 0.3 0.1
EndSection

Section "Screen"
	Identifier	"Primary Screen"
	Device		"NVIDIA Corporation NV40 [GeForce 6800 GT]"
	Monitor		"Dell P1110-0"
	DefaultDepth	24
		
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Secondary Screen"
	Device		"Voodoo 3"
	Monitor		"Dell P1110-1"
	DefaultDepth	24
				
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Dual Head Layout"
	Screen	 	"Primary Screen"
	Screen	 	"Secondary Screen" RightOf "Primary Screen"
	Option 		"Xinerama" 	"On"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection


changing the voodoo driver to vesa seems to have been the key change here, although defining the seperate modes for the monitors was also helpful.

---

### Post by eightysix on 2005-10-19
Hm, I have 3 monitors and 2 video cards, but so far I can only get the dual monitors to work. My cards are a Radeon 8500 on AGP and a Voodoo2 on PCI. Here's my xorg.conf:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
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
	Option		"XkbModel"	"pc101"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"dev0"
	Driver		"ati"
	BusID		"PCI:1:0:0"
        Screen          1
EndSection

Section "Device"
	Identifier	"dev1"
	Driver		"ati"
EndSection

Section "Device"
	Identifier	"dev2"
	Driver		"vesa"
        BusID           "PCI:2:7:0"
EndSection

Section "Monitor"
        Identifier "mon0"
        Option "DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Monitor"
        Identifier "mon1"  
        Option "DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Monitor"
        Identifier "mon2"
        Option "DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
        Identifier "screen0"
        Device "dev0"
        Monitor "mon0"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
        Identifier "screen1"
        Device "dev1"
        Monitor "mon1"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
        Identifier "screen2"
        Device "dev2"
        Monitor "mon2"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "832x624" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
        Identifier "Triple Monitor"
        Screen      0 "screen0"
        Screen      1 "screen1" LeftOf "screen0"
        Screen      2 "screen2" LeftOf "screen1"
        Option "Xinerama" "On"
	Option "Clone" "Off"
        InputDevice "Generic Keyboard"
        InputDevice "Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

``` 

Anyone got a fix for this?

---

### Post by ranf on 2005-10-20
> **achaycock]I seem to have the answer now. This is my new xorg said:**
> "
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option          "backingstore"              "true"
	Option 		"AllowGLXWithComposite" "1"
	Option 		"RenderAccel" "true"
EndSection

Section "Device"
	Identifier	"Voodoo 3"
	Driver		"vesa"
	BusID		"PCI:2:8:0"
EndSection

```
As I can see you removed the `screen X' from the 2 device sections, which is the way to go for 2 different graphics adapters as far as I understood `man xorg.conf'.

---

### Post by Leopard on 2005-10-27
[QUOTE=eightysix]Hm, I have 3 monitors and 2 video cards, but so far I can only get the dual monitors to work. My cards are a Radeon 8500 on AGP and a Voodoo2 on PCI. Here's my xorg.conf:
[snip]
Anyone got a fix for this?[/QUOTE]

The Voodoo 2 only produced 3D graphics (via a pass-through cable), it does not do 2D.  Are you sure it's a Voodoo2?   The Voodoo 3 would also do 2D.

---

