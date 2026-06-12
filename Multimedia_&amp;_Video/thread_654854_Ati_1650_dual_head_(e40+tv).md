---
title: "Ati 1650 dual head (e40+tv)"
date: 2007-12-31
forum: Multimedia &amp; Video
---

### Post by myradio on 2007-12-31
Hi everyone,
i'm having several problems setting my Ati/RADEON 1650, my ViewSonic E40, and my TV... every single guide I 've tried has failed.
(Ubuntu 7.10)

Once ubuntu installed in my machine, I couldn't set resolution heigher than 800*600. NOTE this happens before setting anything.

Then, I have installed ati drivers from [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

and i've edited the xorg.conf on this way:

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "aticonfig-Screen[1]" Above "aticonfig-Screen[0]"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "es"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

	    
Section "Monitor"
	Identifier   	"aticonfig-Monitor[0]"
	VendorName    	"ViewSonic"
	ModelName    	"E40"
	Option	    	"DPMS" "true"
	HorizSync	"30-50"
	VertRefresh	"50-90"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	     "VendorName" "ATI Proprietary Driver"
	Option	     "ModelName" "Generic Autodetecting Monitor"
	Option	     "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen	    0
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	Option	    "TVFormat" "NTSC"
	BusID       "PCI:1:0:0"
	Screen	    1
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	SubSection "Display"
		Viewport   0 0
	EndSubSection
EndSection
```

After that, when starting ubuntu, it shows me a message telling it's running in low resolution mode.

Currently, when trying to lauch ATI Catalyst from "applications>>ATI Catalyst CC", nothing happens.

I had made some tests I saw here in the forum, but I'm not sure what to do with them.

I entered:
```
user@domain:~$ fglrxinfo *and is the same for sudo fglrxinfo.
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

Segmentation fault (core dumped)
```


```
user@domain:~$ amdccle
bash: amdccle: command not found
```


So, first of all I want to know how to install ati drivers correctly, and how to make my monitor run under 1024 resolution. 
After that, I would make tv work properly, currently it just run as a clon from my 1 monitor.


i hope someone could give me a hand

thanks

---

