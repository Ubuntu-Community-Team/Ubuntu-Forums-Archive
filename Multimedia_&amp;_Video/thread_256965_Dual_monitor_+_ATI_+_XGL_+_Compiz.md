---
title: "Dual monitor + ATI + XGL + Compiz"
date: 2006-09-13
forum: Multimedia &amp; Video
---

### Post by Duski on 2006-09-13
I was trying to get it running (different how to pages) but no luck.

My start point:
 - one card, 2 monitors (same resolution on both; 1680x1050)
 - binary drivers from reps
 - xgl & copiz running

I tried it first with aticonfig script & few check changes by hand (virtual row added) -> i count run the X but right after log in i got an error with DRI & no screens found.

Then i tried it with xinerama,  but when i got it running there was a problem with screens (i saw only cursor & all other was disorded like when there is a problem with resolution).

Then i tried only aticonfig & no changes inside xorg.conf, i was able to start x, primary device was working, 2nd was black & i was able to go there  with cursor but i could not move there any windows. The cursor was on 2nd device like if there was only default X.

After this i have tried out many "how to"s, IRC & friends but no success.

The sticky posts @ ubuntu r gr8 but handle only dual with normal X.

Now question: Can someone put here a fully functional xorg.conf (dual + ati + xgl + dri) and if possible a small how to if necessary?

I post here also 2 xorg.conf files (first one that should work with xinerama) and 2nd that i'm running currently:

```
Section "Files"
	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
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
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 84.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Driver      "fglrx"
	VideoRam    262144
	BusID       "PCI:1:0:0"
	Screen	    0
	Option "MonitorLayout" "LVDS, TMDS"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         0 "Default Screen"
	Screen         1 "aticonfig-Screen[1]" Above "Default Screen"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "ServerFlags"  
	Option "Xinerama" "true" 
EndSection

Section "DRI"
	Mode         0666
EndSection
```

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
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	VideoRam	262144
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-84
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
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

Thanks for any replies!

---

### Post by jackocleebrown on 2006-09-20
Hi Duski,

I'd also like to see if anyone has any solutions to this! I think that the only dual screen setups of Xgl that I've seen so far use driver functions like 'Twinview' (Nvidia) where the graphics card just behaves like one big screen over the two displays. I believe that there is an equavalent xorg option for the fglrx driver... can't remember it right now, anyone?

I think that the Xgl server does not yet support more than one display per session, this is why your second xorg will not work. Someone please tell me   if I'm wrong!

---

### Post by Duski on 2006-09-21
It can't be possible that only i have this problem or the whole world is running with nvidia? :)

---

### Post by sbfisher on 2006-11-09
Getting xorg.conf right was a pain for me, but the bigger pain was getting my fglrx drivers working which I detailed [here]("http://www.ubuntuforums.org/showthread.php?t=294670").  Once they were really stable and working, the rest took only a minor number of hours.

I'm not sure what mode I'm using.  I made a backup of my xorg.conf file and then replaced my xorg.conf with the contents of [this one]("http://forum.beryl-project.org/topic-6206-xgl-ati-bigdesktop-screens") from the Beryl forums (the first one down the page). I added my Wacom tablet stuff back into the appropriate sections and changed the resolution of the one monitor to 1280x1024.  When I booted in it actually ran ok (though a little slower with dual monitors that with one).

I'd try being sure you get one monitor working with XGL/Compiz/Beryl before jumping into two (if you haven't tried that already).

---

### Post by blinzler on 2007-01-17
Hi sbfisher,

Unfortunately, your link to the xorg.conf seems to be broken. Could you please post it here?

I'm trying to get a dual screen config (1600x1200 and 1280x1024) running on a ATI radeon 9600 pro SE, fresh install of Ubuntu 6.10. I have managed to get it working on gnome (metacity) with the fglrx provided by ATI.
Then I installed beryl folling [this tutorial]("http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html"). It worked just fine BUT only for one display. The second stays black, displays the cursor as an X and I cannot move any windows there.

The relevant stuff from my xorg.conf looks like this (I omitted the display modes with less than 24 bits):
```

Section "Device"
	Identifier "ATI Technologies, Inc. RV350 AQ [Radeon 9600 SE]"
	Driver "fglrx"
	BusID "PCI:1:0:0"
	Screen 0
EndSection

Section "Device"
	Identifier "ATI Technologies, Inc. RV350 AQ [Radeon 9600 SE] (Secondary)"
	Driver "fglrx"
	BusID "PCI:1:0:0"
	Screen 1
EndSection

Section "Monitor"
	Identifier "NEC MultiSync LCD 2080UX"
	HorizSync 31-91
	VertRefresh 50-85	
	Option "DPMS"
EndSection

Section "Monitor"
	Identifier "Belinea 10 18 20"
	HorizSync 30-81
	VertRefresh 56-75
EndSection

Section "Screen"
	Identifier "NEC"
	Device "ATI Technologies, Inc. RV350 AQ [Radeon 9600 SE]"
	Monitor "NEC MultiSync LCD 2080UX"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Belinea"
	Device "ATI Technologies, Inc. RV350 AQ [Radeon 9600 SE] (Secondary)"
	Monitor "Belinea 10 18 20"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier "Default Layout"
	Screen 0 "NEC"
         Screen 1 "Belinea" RightOf "NEC"
	InputDevice "Generic Keyboard"
	InputDevice "Configured Mouse"
	InputDevice "stylus" "SendCoreEvents"
	InputDevice "cursor" "SendCoreEvents"
	InputDevice "eraser" "SendCoreEvents"
EndSection

Section "ServerFlags"
	Option "AIGLX" "off"
EndSection

Section "Extensions"
	Option "Composite" "Disable"
EndSection

Section "DRI"
	Mode 0666
EndSection

```
Adding this to the first "device" section as suggested doesn't help:
```

Option	    "DesktopSetup" "horizontal"

```

Any ideas on how to get XGL and Compiz/Beryl working on the second screen are more than welcome. I'm also unsure whether my driver (fglrx provided by ATI) is the right choice. Perhaps the fglrx that come with ubuntu or the "ati" or "radeon" open-source driver would be better suited... but I'm hesitant to try all these options as I'm quite a newby with ubuntu.

Many thanks in advance for any help...

---

### Post by linkinpark342 on 2007-01-24
If i'm not much mistaken it is impossible to have an ATi card and multi-monitor support at larger resolutions than 1024x1024 on both monitors currently. ATI cards can't handle textures larger than 2048x2048 and currently Compiz/Beryl uses just one huge texture IIRC. (though if you find an answer I will be most interested since I've run into the same roadblock.)

---

### Post by zedstrange on 2007-01-25
> **linkinpark342 said:**
> If i'm not much mistaken it is impossible to have an ATi card and multi-monitor support at larger resolutions than 1024x1024 on both monitors currently

thank you,   this may well be the issue I am experiencing with my setup.
[http://ubuntuforums.org/showthread.php?t=344701](http://ubuntuforums.org/showthread.php?t=344701)

---

### Post by notromda on 2007-04-08
> **linkinpark342 said:**
> If i'm not much mistaken it is impossible to have an ATi card and multi-monitor support at larger resolutions than 1024x1024 on both monitors currently. ATI cards can't handle textures larger than 2048x2048 and currently Compiz/Beryl uses just one huge texture IIRC. (though if you find an answer I will be most interested since I've run into the same roadblock.)

This was the right answer for me.   I reduced my screen resolution to 1024x768 per monitor, and then the xgl stuff started to work.   It's not a limitation of beryl or xgl, but of the card it would seem.  Here's my xorg.conf.
```


Section "ServerLayout"

#       Screen         "aticonfig-Screen[1]" Above "aticonfig-Screen[0]"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
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
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "i2c"
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
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc104"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "DesktopSetup" "horizontal"
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

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "false"
EndSection

```

---

