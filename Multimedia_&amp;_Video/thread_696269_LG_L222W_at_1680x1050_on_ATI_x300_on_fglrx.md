---
title: "LG L222W at 1680x1050 on ATI x300 on fglrx"
date: 2008-02-13
forum: Multimedia &amp; Video
---

### Post by RicRock on 2008-02-13
Hello Everyone. 

I almost feel guilty posting this, given the extent to which issues like this are posted/discussed/resolved - but I feel I'm at a last resort. This is my first post and I have spent countless hours editing xorg.conf, playing with aticonfig, enabling/disabling things, rebooting 000's of times, etc, with no avail. I have an LG monitor 19.6", which for the life of me can't get to run at 1680x1050 at 60hz - ATI card, Radeon x300, and I am using fglrx - and need some guidance!

At one point, I had it working, through editing the xorg, so I know this it IS possible - Needless to say, I was afraid to reboot. Rebooted, and agh.. back to 1280x1024. fglrx seems to like this resolution, very much. 

Here is the xorg.conf as it is today:

[PHP]Section "Device"
	Identifier	"ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"L222W"
	Vendorname	"LG"
	Modelname	"LG L222W (Digital)"
	Horizsync	28.0-83.0
	Vertrefresh	56.0-75.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
	Monitor		"L222W"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1792	1344
		Modes		"1280x1024@60"	"1280x960@75"	"1280x960@60"	"1400x1050@60"	"1280x1024@75"	"1400x1050@75"	"1152x864@75"	"1600x1200@65"	"1024x768@60"	"1600x1200@60"	"1024x768@70"	"1792x1344@60"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"dri"
	Load		"v4l"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection
Section "device" #   
	Identifier	"device1"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:1"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "screen" #   
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"	"640x480@72"	"640x480@75"	"800x600@56"	"800x600@72"	"800x600@75"	"800x600@60"	"832x624@75"	"1024x768@75"	"1024x768@70"	"1024x768@60"	"1152x864@75"	"1280x1024@75"	"1280x960@60"	"1280x1024@60"	"1280x960@75"	"1400x1050@60"	"1400x1050@75"	"1600x1200@65"	"1600x1200@60"	"1792x1344@60"
	EndSubSection
EndSection
Section "monitor" #   
	Identifier	"monitor1"
	Vendorname	"LG"
	Modelname	"LG L222W (Digital)"
	Horizsync	28.0-83.0
	Vertrefresh	56.0-75.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection[/PHP]

Any help would be GREATLY appreciated. 

Thanks everyone.

Ric

---

### Post by xzero1 on 2008-02-13
See this thread:
[http://ubuntuforums.org/showthread.php?t=695064]("http://ubuntuforums.org/showthread.php?t=695064")

---

### Post by pdub on 2008-02-13
Add the following to your modeline in the monitor section.

```
modeline  "1680x1050@60" 147.1 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
```

Change your screen section from this:

```
Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
    Monitor        "L222W"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Virtual    1792    1344
        Modes        "1280x1024@60"    "1280x960@75"    "1280x960@60"    "1400x1050@60"    "1280x1024@75"    "1400x1050@75"    "1152x864@75"    "1600x1200@65"    "1024x768@60"    "1600x1200@60"    "1024x768@70"    "1792x1344@60"    "1024x768@75"    "832x624@75"    "800x600@60"    "800x600@75"    "800x600@72"    "800x600@56"    "640x480@75"    "640x480@72"    "640x480@60"
    EndSubSection
EndSection 
```

To this:

```
Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
    Monitor        "L222W"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Virtual    **1680    1050**
        **Modes		"1680x1050@60"	"1600x1024@60"	"1440x900@60"	"1280x800@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@56"**
    EndSubSection
EndSection 
```

---

### Post by xzero1 on 2008-02-14
So how does one get these modelines?

---

### Post by pdub on 2008-02-14
To be honest, I found that modeline in a post a while ago when I was configuring my Dell D820, which has a 1680x1050 screen.

Did it work for you?

---

### Post by AceRimmer on 2008-02-14
Could incorrect modeline information cause potential damage to a monitor?

---

### Post by xzero1 on 2008-02-14
The modeline works for me. As for potential damage, good question! With old crt monitors I would not use an arbitrary modeline. Newer monitors seem to have a sync out of range indicator and might be ok.

---

### Post by pdub on 2008-02-14
Yes. 

I have used that modeline on my Dell notebook and my Samsung 22" wide screen lcd.

The computer that I am on right now has NO modelines and it works just fine. It only has this:

```
Modes        "1280x1024@60"    "1280x960@75"    "1280x960@60"    "1400x1050@60"    "1280x1024@75"    "1400x1050@75"    "1152x864@75"    "1600x1200@65"    "1024x768@60"    "1600x1200@60"    "1024x768@70"    "1792x1344@60"    "1024x768@75"    "832x624@75"    "800x600@60"    "800x600@75"    "800x600@72"    "800x600@56"    "640x480@75"    "640x480@72"    "640x480@60"
```

In the Display section.

---

### Post by xzero1 on 2008-02-14
> I have used that modeline on my Dell notebook and my Samsung 22" wide screen lcd.

The computer that I am on right now has NO modelines and it works just fine. It only has this:

But your Samsung 22" *needs* the modeline correct?

---

### Post by Giannis68 on 2008-02-14
download new drivers from ati
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-02-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-02-x86.x86_64.run)
read the this 
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

save your xorg.conf and edit it
remove or comment all modeline lines
my LG 226W monitor working fine without modelines
Section "Device"
    Identifier    "ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro]"
    Boardname    "ati"
    Busid        "PCI:1:0:0"
    Driver        "fglrx"
#    Driver        "ati"
    Option        "VideoOverlay"        "on"
    Option        "OpenGLOverlay"        "off"
    Screen    0
EndSection

Section "Monitor"
    Identifier    "L226W"
    Option        "DPMS"
#    Option        "DDC"    "false" 
    Vendorname    "LG"
    Modelname    "LG L226WTQ(Digital)"
    Horizsync    28.0-83.0
    Vertrefresh    56.0-75.0
# 1680x1050 @ 59.00 Hz (GTF) hsync: 64.07 kHz; pclk: 144.55 MHz
#  modeline "1680x1050@59"  144.55  1680 1784 1968 2256  1050 1051 1054 1086 
#  modeline  "1680x1050@59" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
#  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
#  modeline  "1680x1050@75" 188.07 1680 1800 1984 2288 1050 1051 1054 1096 -hsync +vsync
#  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
#
    Displaysize    444    277#1680x1050    96dpi
    # calc: (x|y)pixels * 25.4 / dpi
    #    DisplaySize    426    266    # 1680x1050 100dpi
    #    DisplaySize    355    222    # 1680x1050 120dpi
        DisplaySize    444    277    # 1680x1050 96dpi
    #    DisplaySize    338    254    # 1280x960 96dpi
    #    DisplaySize    338    270    # 1280x1024 96dpi
    #    DisplaySize    370    277    # 1400x1050 96dpi
    #    DisplaySize    423    370    # 1600x1400 96dpi
    #    DisplaySize    270       203    # 1024x768 96dpi
    Gamma    1.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro]"
    Monitor        "L226W"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
#        Virtual    1920    1200
Modes    "1680x1050"    "1680x1050@59"    "1440x1440"    "1280x1024"    "1280x960"    "1152x864"    "1024x768"    "800x600"    "720x400"    "640x480"
    EndSubSection
EndSection

---

### Post by AceRimmer on 2008-02-14
I'm using a LG 226WTQ 22" and I'm not having any luck.  Here is my xorg.conf and its a fresh 7.10 install.  Any help?

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"    "/dev/input/mice"
    Option        "Protocol"    "ImPS/2"
    Option        "ZAxisMapping"    "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "stylus"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "eraser"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "cursor"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "ATI Technologies Inc R430 [Radeon X800 (PCIE)]"
    Driver        "fglrx"
    Busid        "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    Horizsync    30-70
    Vertrefresh    50-160
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies Inc R430 [Radeon X800 (PCIE)]"
    Monitor        "Generic Monitor"
    Defaultdepth    24
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen "Default Screen"
    Inputdevice    "Generic Keyboard"
    Inputdevice    "Configured Mouse"
    
    # Uncomment if you have a wacom tablet
    #    InputDevice     "stylus"    "SendCoreEvents"
    #    InputDevice     "cursor"    "SendCoreEvents"
    #    InputDevice     "eraser"    "SendCoreEvents"
EndSection
Section "Module"
    Load        "glx"
EndSection
Section "Extensions"
    Option        "Composite"    "0"
EndSection
```

---

### Post by Giannis68 on 2008-02-15
try this...
> **AceRimmer said:**
> I'm using a LG 226WTQ 22" and I'm not having any luck.  Here is my xorg.conf and its a fresh 7.10 install.  Any help?

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"    "/dev/input/mice"
    Option        "Protocol"    "ImPS/2"
    Option        "ZAxisMapping"    "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "stylus"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "eraser"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "cursor"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "ATI Technologies Inc R430 [Radeon X800 (PCIE)]"
    Driver        "fglrx"
    Busid        "PCI:1:0:0"
    Option        "VideoOverlay"        "on"
    Option        "OpenGLOverlay"        "off"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    Horizsync    28.0-83.0
    Vertrefresh    56.0-75.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies Inc R430 [Radeon X800 (PCIE)]"
    Monitor        "Generic Monitor"
    Defaultdepth    24
Modes    "1680x1050"     "1440x1440"    "1280x1024"    "1280x960"    "1152x864"    "1024x768"    "800x600"    "720x400"    "640x480"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen "Default Screen"
    Inputdevice    "Generic Keyboard"
    Inputdevice    "Configured Mouse"
    
    # Uncomment if you have a wacom tablet
    #    InputDevice     "stylus"    "SendCoreEvents"
    #    InputDevice     "cursor"    "SendCoreEvents"
    #    InputDevice     "eraser"    "SendCoreEvents"
EndSection
Section "Module"
    Load        "glx"
    Load        "i2c"
    Load        "bitmap"
    Load        "ddc"
    Load        "extmod"
    Load        "freetype"
    Load        "int10"
    Load        "vbe"
    Load        "record"
    Load        "dbe"
    Load        "v4l"
EndSection
Section "DRI"
    Mode    0666
EndSection
Section "Extensions"
    Option        "Composite"    "0"
EndSection
```

---

### Post by xzero1 on 2008-02-15
Why does the Linux games dvd have no problem getting 1680x1050?

---

### Post by xzero1 on 2008-02-17
> So how does one get these modelines?
I think I found my answer:
[http://gentoo-wiki.com/TIP_Getting_modelines#Calculate_Using_gtf](http://gentoo-wiki.com/TIP_Getting_modelines#Calculate_Using_gtf)
Gtf is a ubuntu program that generates modelines given the resolution and vertical frequency.
Note: there are online modeline generators that give different results. Gtf seems more accurate.

---

### Post by AceRimmer on 2008-02-19
> **Giannis68 said:**
> try this...

I used that xorg.conf file and it just booted into safe graphics mode, it gets to the desktop but only at a 800*600 res.

---

### Post by Giannis68 on 2008-02-21
go System--->Administration--->Sceens and Graphics
Screen---Model--->Choose Screen
check Widescreen monitor (its important)
choose Add (inf files from monitor drivers CD)
or Detect

---

