---
title: "[SOLVED] [gutsy] X always logout after a login with xinerama"
date: 2007-11-08
forum: Multimedia &amp; Video
---

### Post by iDo8p on 2007-11-08
Hello !
I've just migrate to ubuntu gutsy and, for the occasion, change my video card :)

I have now a Matrox P650 PCIe.

I install driver found at [http://tuxx-home.at/](http://tuxx-home.at/)
All is seems ok and so i configure my xorg.conf to use mtx driver.
For one screen it's ok !!

Great ! So, i try to add my second screen in the xorg.conf.
Now my xorg.conf looks like this :
```
Section "Files"
	RgbPath "/usr/X11R6/lib/X11/rgb"
	FontPath "/usr/X11R6/lib/X11/fonts/truetype/"
	FontPath "/usr/X11R6/lib/X11/fonts/URW/"
	FontPath "/usr/X11R6/lib/X11/fonts/uni/"
	FontPath "/usr/X11R6/lib/X11/fonts/misc/"
	FontPath "/usr/X11R6/lib/X11/fonts/Type1/"
	FontPath "/usr/X11R6/lib/X11/fonts/CID/"
	FontPath "/usr/X11R6/lib/X11/fonts/75dpi/"
	FontPath "/usr/X11R6/lib/X11/fonts/100dpi/"
	FontPath "/usr/X11R6/lib/X11/fonts/local/"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	#Load	"glx"
	Load	"int10"
	Load	"record"
	#Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"

	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
	Option		"XkbOptions"	"lv3:ralt_switch"
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

Section "Device"
	Identifier	"matrox1"
	Driver		"mtx"
	BusID		"PCI:2:00:0"
	Option		"HWcursor"		"on"
	Screen       0
	#Option "QID" "on"
	Option "OCC"
EndSection
Section "Device"
	Identifier	"matrox2"
	Driver		"mtx"
	BusID		"PCI:2:00:0"
	Option		"HWcursor"		"on"
	Screen       1
	#Option "QID" "on"
	Option "OCC"
EndSection


Section "Monitor"
	Identifier	"Philips1"
	VendorName      "PHL"
	Option		"DPMS"
	HorizSync    30.0 - 82.0
	VertRefresh  56.0 - 76.0
EndSection
Section "Monitor"
	Identifier	"Philips2"
	VendorName      "PHL"
	Option		"DPMS"
	HorizSync    30.0 - 82.0
	VertRefresh  56.0 - 76.0
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"matrox1"
	Monitor		"Philips1"
	DefaultDepth	24
	DefaultBpp	32
	SubSection "Display"
        	Depth        24
        	Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
Section "Screen"
	Identifier	"Screen2"
	Device		"matrox2"
	Monitor		"Philips2"
	DefaultDepth	24
	DefaultBpp	32
	SubSection "Display"
        	Depth        24
        	Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerFlags"
        Option "Xinerama" "0"
	Option "IgnoreABI" "True"
	Option "AllowMouseOpenFail"
	#Option "RandR" "on"
	Option "BlankTime" "0"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Screen		0 "Screen1"
	#Screen 		0 "Screen1" 0 0
	Screen          1 "Screen2" RightOf "Screen1"
	Option          "Xinerama" "true"
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection

Section "DRI"
    Mode    0666
EndSection

```

When i reboot, my two screen are ok, 
i see login on the left and maroon background on the right.
I login and....
x logout...

I see background about one second and i come back on login screen, like a CTRL+ALT+BACKSPACE does...

Thanks :)
iDo

PS : excuse my poor English, i do my best :(

---

### Post by iDo8p on 2007-11-09
It works !!!!
Wonderfull !
I post the solution, if it can help someone....
To get it work i have to disable xgl :
```

mkdir ~/.config/xserver-xgl
touch ~/.config/xserver-xgl/disable

```
and this is ma xorg.conf
```

Section "Files"
EndSection

Section "Module"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "dbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
	Option		"XkbOptions"	"lv3:ralt_switch"
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

Section "Device"
	Identifier	"matrox1"
	Driver		"mtx"
	BusID		"PCI:2:00:0"
	Option		"HWcursor"	"on"
	Option		"Busmastering"	"on"
	Screen       0
EndSection
Section "Device"
	Identifier	"matrox2"
	Driver		"mtx"
	BusID		"PCI:2:00:0"
	Option		"HWcursor"	"on"
	Option		"Busmastering"	"on"
	Screen       1
EndSection


Section "Monitor"
	Identifier	"Philips1"
	VendorName      "PHL"
	Option		"DPMS"
	HorizSync    30.0 - 82.0
	VertRefresh  56.0 - 76.0
EndSection
Section "Monitor"
	Identifier	"Philips2"
	VendorName      "PHL"
	Option		"DPMS"
	HorizSync    30.0 - 82.0
	VertRefresh  56.0 - 76.0
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"matrox1"
	Monitor		"Philips1"
	DefaultDepth	24
	DefaultBpp	32
	SubSection "Display"
        	Depth        24
        	Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
Section "Screen"
	Identifier	"Screen2"
	Device		"matrox2"
	Monitor		"Philips2"
	DefaultDepth	24
	DefaultBpp	32
	SubSection "Display"
        	Depth        24
        	Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerFlags"
        Option "Xinerama" "True"
	Option "IgnoreABI" "True"
	Option "AllowMouseOpenFail"
	Option "NoPM"
	Option "RandR" "off"
	Option "BlankTime" "0"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Screen		0 "Screen1"
	#Screen 		0 "Screen1" 0 0
	Screen          1 "Screen2" RightOf "Screen1"
	Option          "Xinerama" "true"
EndSection

Section "Extensions"
	Option	"Composite"	"false"
        Option	"RANDR" 	"disable"
EndSection

Section "DRI"
	Group 0
	Mode    0666
EndSection

```

Voila :)

---

