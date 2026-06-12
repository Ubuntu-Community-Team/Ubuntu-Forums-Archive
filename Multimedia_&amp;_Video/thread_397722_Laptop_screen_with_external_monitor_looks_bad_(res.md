---
title: "Laptop screen with external monitor looks bad (resolution or fonts problem)"
date: 2007-03-31
forum: Multimedia &amp; Video
---

### Post by orengolan on 2007-03-31
I installed Ubuntu 6.10, dual boot, on my tablet-pc (Fujitsu Lifebook P1015D).
Everything look ok when I use the built-in screen, but when I connect my tablet to external monitor the fonts looks awful, almost unreadable. I don't think that it's a fonts issue, i think it's something with the resolution, but i am not sure. (I tried different fonts, but it didn't help).
The max resolution for my internal monitor is 1024*600 (i don't know about the color depth, where can i find it?).
The max resolution for external monitor is 1600*1200 (24-bit colors).
When i open the screen resolution page I see 1024*600, 60HZ (and I can't choose anything else).

In Windows the external monitor look great - I can choose anything between 800*600 - 1600*1200 but the best fit for my external monitor is 1024*768.

Here is a snapshot, i hope that you will be able to see the problem-
[http://ubuntuforums.org/g/index.php?n=220](http://ubuntuforums.org/g/index.php?n=220)

here is some info:

oren@oren-laptop:~$ lshw

```
       *-display:0
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 04
             size: 256MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             resources: iomemory:b0080000-b00fffff ioport:1400-1407 iomemory:c0000000-cfffffff

```

oren@oren-laptop:~$ lspci
```

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
```

here is my /etc/X11/xorg.conf file:

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
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
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x600"
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

---

### Post by mrmonday on 2007-03-31
Are you trying to use both monitors at once? If so, you need to [enable multi-monitor support using this.]("http://www.ubuntuforums.org/showthread.php?t=221174"). Hope this helps. Let me know how it goes.

---

### Post by orengolan on 2007-03-31
no, I am trying to use only the external one.

---

### Post by mrmonday on 2007-04-01
You could try the above anyway... It will allow you to have seperate settings for each monitor.

---

### Post by Luca Dod3 on 2007-05-19
hy!
I managed, after a lot of time, to set up a dual monitor configuration, using the help of a thread of this same forum. the only problem I finally get is a damaged image, particularly with the fonts.
They told me to look in the forum for this problem, but i can't find anything (and I didn't want to create a new thread only 'cause I'm not able to searh good). so I'm using this one to ask:
is there any thread about this problem or someway we could now try to solve it?

Intel graphic card, 1440 x 900 external monitor (19"), problem with both xinerama on or off.

---

