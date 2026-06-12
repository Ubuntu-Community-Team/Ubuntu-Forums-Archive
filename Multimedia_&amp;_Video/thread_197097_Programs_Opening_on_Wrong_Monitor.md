---
title: "Programs Opening on Wrong Monitor"
date: 2006-06-15
forum: Multimedia &amp; Video
---

### Post by TheMono on 2006-06-15
Downloaded Breezy as my very first entry into linuxland - didn't work for wireless, so didn't bother fiddling with xorg.conf - returned to XP.

Downloaded Dapper a few days ago - installed Network Manager - Wireless works great. Happy camper. Finally put the effort into redoing my xorg.conf. Day later finally works - result below. Feel free to copy if you have a Dell Inspiron 1150 with good old Intel Extreme Graphics...

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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
	Identifier	"IntSrc"
	Driver		"i810"
	BusID		"PCI:0:2:0"
        Option          "MonitorLayout" "CRT,LFP"
        Screen          0
EndSection

Section "Device"
	Identifier	"ExtSrc"
	Driver		"i810"
	BusID		"PCI:0:2:0"
        Screen          1
EndSection

Section "Monitor"
	Identifier	"IntLCD"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Monitor"
	Identifier	"ExtCRT"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	45-80
EndSection

Section "Screen"
	Identifier	"IntScr"
	Device		"IntSrc"
	Monitor		"IntLCD"
	DefaultDepth	16
        {Blah, blah, blah}
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "Screen"
        Identifier      "ExtScr"
        Device          "ExtSrc"
        Monitor         "ExtCRT"
        DefaultDepth    16
        SubSection "Display"
                Depth           16
                Modes           "800x600"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "800x600"
        EndSubSection
EndSection

#Section "ServerLayout"
#	Identifier	"Default Layout"
#	Screen		"IntScr"
#	InputDevice	"Generic Keyboard"
#	InputDevice	"Configured Mouse"
#	InputDevice     "stylus" "SendCoreEvents"
#	InputDevice     "cursor" "SendCoreEvents"
#	InputDevice     "eraser" "SendCoreEvents"
#	InputDevice	"Synaptics Touchpad"
#EndSection

Section "ServerLayout"
        Identifier      "Dualhead"
        Screen          "IntScr"
        Screen          "ExtScr" LeftOf "IntScr" 
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
        Option          "Xinerama"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "ServerFlags"
       Option          "Xinerama"      "true"
EndSection
```

But onto the actual question. When I open a new program it always opens on my external monitor instead of my laptop panel... Any way to change this so my default screen is the internal?

Thanks in advance.

---

### Post by Anduu on 2006-06-15
```
Section "Device"
	Identifier	"IntSrc"
	Driver		"i810"
	BusID		"PCI:0:2:0"
        Option          "MonitorLayout" "CRT,LFP"
        Screen          0
EndSection

```

I notice here your CRT is *before* your LFP...maybe switch the two...

---

### Post by TheMono on 2006-06-15
When in doubt - hack and slash lol.

I figured that X just plain didn't like the primary monitor being on the right - so I rearranged my desk and stuck my CRT on the right instead, and switched LeftOf to RightOf. It's not ideal, but works for now until anyone can figure out how to do that.

---

### Post by RawMustard on 2006-06-16
It's a limitation of metacity, and drives dual screen users to the point of sticking forks in their eyes.  For some reason, metacity's dev's think it's better to throw windows where ever they damn well like than in some sensible fashion, like where it was when you closed it.  I don't see why when I delete a file from a nautilus window on my right monitor, I get the confirmation window opening up 9 feet away on my left monitor, surely it would be better to open the dialog under the mouse?  That's just one example of its stupid behaviour.

---

### Post by TheMono on 2006-06-16
Forks in eyes you say.... Shall do when I find right sized forks. 

Ah well, at least I know it can't be done now. Thanks.

---

### Post by BitWitty on 2006-06-16
Actually, I think it opens up windows rather intelligently... most of the time. I believe the default behavior is to open a new window on the screen that does not have the currently active one. In other words, if I have XChat open on the left screen and I click on the Firefox icon, it will open it up on the right, which makes sense. I want to be able to see both at the same time. Unfortunately, it also seems to do that with small dialog boxes as well. It took me a while to get used to it but I like this arrangement a lot better than how Windows handles things IMO.

---

