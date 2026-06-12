---
title: "External monitor with laptop, can't set it as primary"
date: 2006-12-06
forum: Multimedia &amp; Video
---

### Post by tehmatticus on 2006-12-06
Hey guys, 

I've got a Sager 4880 laptop with a VGA out connector.  I'd like to be able to get my 20 inch Dell 2007WFP monitor to become my primary monitor while i'm at home, and have it get its native resolution of 1680x1050.  However, the best i'm currently able to do is have it clone my laptop's display at the laptop's native res of 1400x1050.

I'm completely at a loss for how to get X to turn my internal laptop LCD off and switch to the external monitor.  I've done extensive forum searching over the past few days, and all I can seem to find are people wishing to stretch their display over several monitors.  I just want the external one on, with its native res.

xorg.conf:
```
Section "ServerLayout"

	Identifier     "Default Layout"
	Screen      0  "External Setup" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "Monitor"
	Identifier   "Laptop LCD"
	HorizSync    28.0 - 70.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "External LCD"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "card0"
	Driver      "fglrx"
	Option	    "XAANoOffscreenPixmaps"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "card1"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option		"MonitorLayout" "crt,none"
	BusID		"PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Internal Setup"
	Device     "card0"
	Monitor    "Laptop LCD"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "External Setup"
	Device     "card1"
	Monitor    "External LCD"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1680x1050" "1200x800" "1024x758"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection
```

---

### Post by tehmatticus on 2006-12-06
Any ideas?  I'd really like to take full advantage of my expensive monitor.  Any help would be really appreciated.  

Thanks again,
Matt

---

### Post by tyyp88 on 2007-11-07
Hello,

I have IBM X41 with Intel 915GM graphics card and i have also similar problem.

I'am using Ubuntu 7.10 and intel driver (i think it is experimental).

Recently i bought Samsung Syncmaster 932GW monitor and tryed to use it as a primary monitor. By default Intel 915GM VGABIOS doesn't support 1440x900 resolutin, so i was forced to use VGA BIOS hack program 915resolution witch did worked correctly. 

But, the problem is when I try to use only one monitor (Samsung 932GW) then I'am getting xorg error what forces me to change video settings in startup. Maybe i need to reconfigure my xorg somehow...

In clone mode it works well (not well), but in both sides in my secondary monitor about 5cm there is a black area. I don't now what is the problem. Maybe Samsung monitor driver is buged, witch came with the monitor or intel driver...

Iam pretty exhausted becouse I want to use my monitor, and i dont want to go back into Windows...

If someone got a good idea what to try then i would be very happy to try it.

_______________________________________

But, I think that there is problem in your's xorg.conf... 

> **tehmatticus said:**
> 

```

Section "Device"
	Identifier  "card0"
	Driver      "fglrx"
	Option	    "XAANoOffscreenPixmaps"
**	BusID       "PCI:1:0:0"**
EndSection

Section "Device"
	Identifier  "card1"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option		"MonitorLayout" "crt,none"
**	BusID		"PCI:1:0:0"**
EndSection

```

The xorg manual pages say's about BusID
> 
BusID "bus-id"
This specifies the bus location of the graphics card. For PCI/AGP cards, the bus-id string has the form PCI:bus:device:function (e.g., "PCI:1:0:0" might be appropriate for an AGP card). This field is usually optional in single-head configurations when using the primary graphics card. In multi-head configurations, or when using a secondary graphics card in a single-head configuration, this entry is mandatory. Its main purpose is to make an unambiguous connection between the device section and the hardware it is representing. This information can usually be found by running the Xorg server with the -scanpci command line option.

Im not sure, but i think the BusID should be different...

In my case when i scanpci i get:

```

root@sander-laptop:~# scanpci 

pci bus 0x0000 cardnum 0x02 function 0x00: vendor 0x8086 device 0x2592 Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller

pci bus 0x0000 cardnum 0x02 function 0x01: vendor 0x8086 device 0x2792 Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller
```

So, first one (Internal Laptop Display) is BusID "PCI:0:2:0"
And, second one (VGA-output) is BusID "PCI:0:2:1"

Also, there is a little mistake in your's xorg.conf SubSection "Display" > Modes

1024x758 must be 1024x7[COLOR="Red"]6[/COLOR]8

> **tehmatticus said:**
> 
```

Section "Screen"
	Identifier "External Setup"
	Device     "card1"
	Monitor    "External LCD"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1680x1050" "1200x800" "1024x758"
	EndSubSection
EndSection
```

---

### Post by d1ss0nant on 2007-11-13
Hello - I'm using a compaq r3000z and I have a similar problem...let me explain:

I like to use my laptop on my couch...when i bring it back into my bedroom, i plug it into the monitor (nothing happens).  I try to hit my "projector select" shortcut keys (fn+F4 on my laptop i think) - nothing happens.  If I switch to a full screen terminal with cntrl+alt+F1, then switch back to GUI with cntrl+alt+F7, it SOMETIMES works.  Basically all I want is the functionality of my fn+F4 (monitor select) to work without having to restart (that works).  Does anyone have any ideas?  Thanks.

---

