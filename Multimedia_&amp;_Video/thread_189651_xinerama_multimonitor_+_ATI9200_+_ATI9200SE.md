---
title: "xinerama multimonitor + ATI9200 + ATI9200SE"
date: 2006-06-05
forum: Multimedia &amp; Video
---

### Post by Alpha1125 on 2006-06-05
Hello,

I can not seem to be able to get my third monitor running.](*,) 
With the current xorg.conf, posted below, X fails to start and a blank screen comes up.
I have tried with the "ATI Port2" section to use device "radeon", or "ati" and both fails.
Xinerama works fine with the left and right monitors, just not the middle (screen2).


Background info:
[LIST]
[*]All 3 monitors are the same make/model.
[*]The 9200se is AGP.
[*]The 9200 is PCI.
[/LIST]

Posting of my lspci
```
alpha@alpha-desktop:~$ lspci -v|grep "ATI"
0000:00:09.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200] (rev 01) (prog-if 00 [VGA])
0000:00:09.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200] (Secondary) (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01) (prog-if 00 [VGA])
0000:01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)

```

Posting of my xorg.conf file:
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
	Identifier	"ATI Port0"
	Driver		"radeon"
	Option          "SWcursor" "true"
	BusID		"PCI:0:9:0"
	Screen 0
EndSection

Section "Device"
	Identifier	"ATI Port1"
	Driver		"radeon"
	Option          "SWcursor" "true"
	BusID		"PCI:0:9:0"
	Screen 1
EndSection

Section "Device"
       Identifier      "ATI Port2"
       Driver          "ati"
#       Driver          "radeon"
       BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Mon0"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Mon1"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Mon2"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"ATI Port0"
	Monitor		"Mon0"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"ATI Port1"
	Monitor		"Mon1"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen2"
	Device		"ATI Port2"
	Monitor		"Mon2"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	Screen "Screen2"
	Screen "Screen0" LeftOf "Screen2"
	Screen "Screen1" RightOf "Screen2"
	Option		"Xinerama" "true"
EndSection
```

Any help with getting my third monitor to work would be appreciated.

Thanks.

---

### Post by Alpha1125 on 2006-06-05
I have done the follow to trouble shoot:

I removed the PCI card, to attempt to just use the AGP.  No problems, "dkpg-reconfigure xserver-xorg" made X work with the AGP card.

However, when I tried to merge the new xorg.conf with the old, it dies.  I believe that this is an issue with the drivers, causing the lock up.

So, I can get the card to work with either the PCI or the AGP, but not both.

I will attempt to use the official ATI drivers.  Hope that will solve the issues.

---

### Post by vh1 on 2006-06-06
I've tried to do this in dapper and couldn't manage to get it working, while it worked fine in Dapper. I think it's a problem with Xorg 7.0.

---

