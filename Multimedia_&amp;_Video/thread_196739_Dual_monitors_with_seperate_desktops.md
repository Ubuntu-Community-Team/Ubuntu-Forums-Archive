---
title: "Dual monitors with seperate desktops"
date: 2006-06-14
forum: Multimedia &amp; Video
---

### Post by Malta Soron on 2006-06-14
Hi all, I haven't installed Ubuntu yet, but I'm planning to do so on the computer I'm building about within a month. I was reading about dual monitors and Twinview and I was wondering: is it possible to run a seperate desktop on each monitor, so I could run a full screen appplication on one monitor and still do stuff on the other? Would this require two instances of X.org? Thanks in advance.

---

### Post by gerbman on 2006-06-14
[QUOTE=Malta Soron]Hi all, I haven't installed Ubuntu yet, but I'm planning to do so on the computer I'm building about within a month. I was reading about dual monitors and Twinview and I was wondering: is it possible to run a seperate desktop on each monitor, so I could run a full screen appplication on one monitor and still do stuff on the other? Would this require two instances of X.org? Thanks in advance.[/QUOTE]Yes, it is possible, and with only one xorg file. It can be done different ways, depending on your video card. I think nvidia is better supported in Ubuntu, though dual screen works fine on my ATI 9500 Pro and X600 cards.

---

### Post by Malta Soron on 2006-06-15
I'm going to use an Nvidia card (the 7900GT or the 7600GT). Can you tell me how to do it, or do you know a guide?

---

### Post by RawMustard on 2006-06-15
I've got the 7800 GTX so it's not much different than yours.  Here's my xorg.conf file which should work for you too maybe with some slight changes.

```

# /etc/X11/xor# /etc/X11/xorg.conf (xorg X Window System server configuration file for nVidia TwinView)
#
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
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
        Load    "record"
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
        Option          "Device"           "/dev/input/mice"
        Option          "Protocol"         "ExplorerPS/2"
        Option          "Emulate3Buttons"  "false"
        Option          "Buttons"          "7"
        Option          "ZAxisMapping"     "4 5"
        Option          "ButtonMapping"    "1 2 3 6 7"
        Option          "Resolution"       "100"
EndSection

Section "Device"
        Identifier     "Card0"
        Driver         "nvidia"
        VendorName     "nVidia Corporation"
        BoardName      "GeForce 7800 GTX"
        BusID          "PCI:4:0:0"
        Option         "ConnectedMonitor"          "DFP, DFP"
        Option         "TwinView"                  "1"
        Option         "TwinViewOrientation"       "LeftOf"
        Option         "RenderAccel"               "1"
        Option         "HWcursor"                  "1"
        Option         "CursorShadow"              "1"
        Option         "CursorShadowAlpha"         "64"
        Option         "CursorShadowXOffset"       "4"
        Option         "CursorShadowYOffset"       "2"
        Option         "Coolbits"                  "1"
#       Option         "AllowGLXWithComposite"     "1"
        Option         "NoLogo"                    "1"
        Option         "MetaModes"                 "1280x1024,1280x1024; 1024x768,1024x768; 800x600,800x600; 1280x1024,NULL; 1024x768,NULL"
        Option         "UseEdidFreqs"              "1"
        Option         "SecondMonitorHorizSync"    "30-83"
        Option         "SecondMonitorVertRefresh"  "56-76"
EndSection

Section "Monitor"
        Identifier     "Philips 190B"
	Option         "DPMS"
        HorizSync       30-83
        VertRefresh     56-76
EndSection

Section "Screen"
        Identifier     "Screen0"
        Device         "Card0"
        Monitor        "Philips 190B"
	DefaultDepth    24
	SubSection "Display"
	       Depth    24
               Modes   "1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerFlags"
        Option          "Xinerama" "off"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen    0     "Screen0" 0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection


```

---

### Post by Malta Soron on 2006-06-15
Thanks. I think I'll be OK with that.

---

### Post by Malta Soron on 2006-06-15
Am I correct in thinking that the thread [[desktop] General 6.06 - Xgl + Dual Monitor](http://ubuntuforums.org/showthread.php?t=189977) deals with the same that I mean? Do I need to use Xinerama of TwinView? (It's confusing me a bit :( )

---

### Post by RawMustard on 2006-06-15
You need to use twinview.
The config I gave you works perfectly fine with xgl-compiz, I'm using it right now.
I used this [url=http://www.compiz.net/viewtopic.php?id=652
]guide[/url] to get it all working if that's what you want to do.

---

### Post by Malta Soron on 2006-06-15
So I should use [this guide](http://ubuntuforums.org/showthread.php?t=133427) to get xgl+compiz running (I understand it's not necessary for dual monitors, but apparently everybody really wants it) and then use [this one](http://www.ublug.org/howtos/ubuntu/twinview/twinview-howto-breezy.html) and your config to set up TwinView?

Btw, do you have one virtual desktop spanned across both monitors or a seperate virtual desktop on each?

---

