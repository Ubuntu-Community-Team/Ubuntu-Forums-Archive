---
title: "Problem with intel 855 tv-out"
date: 2007-02-12
forum: Multimedia &amp; Video
---

### Post by haltman on 2007-02-12
Hi,
Are several days that I'm trying to use tv-out of my notebook *Acer Travelmate 660* with integrated an Intel 855 GM video card. I have two partition one with Ubuntu 6.10 and another with windows XP. 
In windows I can use without problem tv-out (s-video connector) to 800x600 and higher. The best resolution that I can obtain is 640x480 centered, there is no way to fit signal to full screen.
I have tried several configuration of xorg.conf with the following result:
-using only the tv-out I get image on my tv 640x480
-xinerama: 800x600 on my notebook and 640x480 on tv
-dual-head: the same of above.

Here follow all configuration I tested only video part:

Original:
```

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Monitor Generico"
	Option		"DPMS"
	HorizSync	28-70
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Monitor Generico"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Only tv-out:
```


Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option "MonitorLayout" "NONE,TV"
EndSection

Section "Monitor"
	Identifier	"Monitor TV"
	Option		"DPMS"
	ModeLine "800x600" 50.00 800 800 800 800 600 600 600 600
#Modeline "720x540PAL" 15.101 720 770 842 968 540 565 570 624 Composite Interlace
EndSection

Section "Screen"
	Identifier	"Screen TV"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Monitor TV"
	DefaultDepth	24
	SubSection "Display"
		Depth 24
		Modes "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen TV"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Version with Xinerama and dual-head to switch form one to the other I simply comment one or the other voice from the section *ServerFlags*
```

ection "Device"
    Identifier  "Default Card"
    Driver      "i810"
    BusID       "PCI:0:2:0"
EnDSection

Section "Device"
    Identifier  "Card-LCD"
    Driver      "i810"
    BusID       "PCI:0:2:0"
    Screen      0
    Option      "MonitorLayout" "TV,LFP"
    Option      "DisplayInfo" "disabled" 
EndSection

Section "Device"
    Identifier  "Card-TV"
    Driver      "i810"
    BusID       "PCI:0:2:0"
    Screen      1
#    Option      "MonitorLayout" "TV,LFP"
    Option      "DisplayInfo" "disabled" 
    Option     "DevicePresence" "true"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
	HorizSync	28-70
	VertRefresh	43-60
EndSection

Section "Monitor"
        Identifier      "TV"
	Option		"DPMS"
#     Modeline "800x600"   50.00   800  800  800  800   600  600  600  600
        Modeline "720x540PAL" 15.101 720 770 842 968 540 565 570 624 Composite Interlace
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Default Card"
        Monitor         "LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"LCD Screen"
	Device		"Card-LCD"
	Monitor		"LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "Screen"
    Identifier  "TV Screen"
    Device      "Card-TV"
    Monitor     "TV"
    DefaultDepth    24
    SubSection "Display"
        Depth       24
        Modes       "800x600"
        Viewport   0 0
    EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Layout LCD Singolo"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

#Section "ServerLayout"
#	Identifier	"Layout TV"
#	Screen		"TV Screen"
#	InputDevice	"Generic Keyboard"
#	InputDevice	"Configured Mouse"
#	InputDevice     "stylus" "SendCoreEvents"
#	InputDevice     "cursor" "SendCoreEvents"
#	InputDevice     "eraser" "SendCoreEvents"
#	InputDevice	"Synaptics Touchpad"
#EndSection

Section "ServerLayout"
        Identifier      "Dualhead"
#        Screen  "LCD Screen" LeftOf "TV Screen"
#        Screen          "TV Screen"
        Screen 0        "LCD Screen" 0 0
        Screen 1        "TV Screen" 0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
        Option          "Clone" "true"
EndSection

Section "ServerLayout"
        Identifier      "Xine"
	Screen 0 "LCD Screen" 0 0
        Screen 1 "TV Screen" RightOf "LCD Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
        Option          "Xinerama" "true"
EndSection


Section "DRI"
	Mode	0666
EndSection

Section "ServerFlags"
Option "DontVTSwitch" "true"
#Option "DefaultServerLayout" "Dualhead"
Option "DefaultServerLayout" "Xine"
#Option "DefaultServerLayout" "layout LCD Singolo"
#Option "DefaultServerLayout" "layout CRT"
Option "RandR" "on"
EndSection

Section "Extensions"
#Option "Composite" "true"
EndSection

```

So the question is how can I get a resolution of 800x600 on my TV?? Or at least how can fit the resolution 640x480 to full screen??

Thanks in advance!
ciao
h.

---

### Post by teknorah on 2007-04-08
I have not have great success with using Modeline.  I would suggesting you find out the Vertical and Horizontal sync ranges from the manufacturer of your TV and enter the following lines into your Montor Section for the TV:

```
    HorizSync    24-80
    VertRefresh    30-80
```

---

