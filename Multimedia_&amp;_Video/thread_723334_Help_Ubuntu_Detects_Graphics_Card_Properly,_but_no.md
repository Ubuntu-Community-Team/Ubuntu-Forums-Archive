---
title: "Help: Ubuntu Detects Graphics Card Properly, but not Screens"
date: 2008-03-13
forum: Multimedia &amp; Video
---

### Post by aidave on 2008-03-13
I have three monitors and three graphics cards.  For web development - editor in center, browser preview in second, FTP in third.  ITs a great setup!  But I can only get the center monitor to work with Ubuntu.

Ubuntu has successfully detected that I have three graphics cards installed, plus an extra VESA one that I am assuming is a dual out port of the GeForce.  I never use that though cuz I dont like how it works.

NVIDIA GeForce4 (AGP)
ATI Radeon (PCI)
VESA Driver (probably dual out?)
Voodoo3 (PCI)

However, in the Screen tab, I get these options:

Screen 1 - o Default
Screen 2 - Default, Secondary, o Disabled
Screen 1 - Default, o Disabled
Screen 1 - Default, o Disabled
Screen 1 - Default, o Disabled

So there is no way to make the other three screens as Secondary because those are all greyed out and unable to select.  Just curious how do you get them to be Secondary?  I also do not know which Screens correspond to which Graphics Card.  I think that might be a good feature to add to future Ubuntu.  Why are there four "Screen 1"s?  Shouldnt it be 1-5.

Also, when I enable "screen 2" as Secondary, it only makes the center monitor work, but the desktop is "scrollable" and a little bit bigger than the resolution, so I have to scroll around with my mouse to click the menus.  Im not sure what it is trying to do.

cheers,
dave

---

### Post by aidave on 2008-03-13
Does anyone know of any tutorials/walkthroughs about this?

All I can find are ways to enable dual-output on one card.  I am trying to get multiple outputs on multiple cards...

cheers

---

### Post by aidave on 2008-03-14
I found this tutorial here: [http://gentoo-wiki.com/HOWTO_Dual_Monitors#Setting_up_Two_Graphi%20cs_Cards](http://gentoo-wiki.com/HOWTO_Dual_Monitors#Setting_up_Two_Graphi%20cs_Cards)

I made these changes to "xorg.conf":

```

Section "Monitor"
	Identifier	"CenterMonitor"
	Vendorname	"LG Electronics Inc."
	Modelname	"LG L1732TX (Analog)"
	Horizsync	30.0-83.0
	Vertrefresh	56.0-75.0
...
	Gamma	1.0
EndSection
Section "Monitor" #    
	Identifier	"RightMonitor"
	Vendorname	"LG Electronics Inc."
	Modelname	"LG L1750S"
	Horizsync	30.0-83.0
	Vertrefresh	56.0-75.0
...
	Gamma	1.0
EndSection
Section "Monitor" #    
	Identifier	"LeftMonitor"
	Vendorname	"LG Electronics Inc."
	Modelname	"LG L1750S"
	Horizsync	30.0-83.0
	Vertrefresh	56.0-75.0
...
	Gamma	1.0
EndSection

Section "Device"
	Identifier	"NVIDIAGeForce4"
	Boardname	"NVIDIA GeForce4 (generic)"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
EndSection
Section "Device" #    
	Identifier	"ATIRadeon"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:2:10:0"
	Driver		"ati"
	Screen	1
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "Device" #    
	Identifier	"Voodoo3"
	Boardname	"Voodoo3 (generic)"
	Busid		"PCI:2:12:0"
	Driver		"tdfx"
	Screen	2
EndSection

Section "Screen"
	Identifier	"CenterScreen"
	Monitor		"CenterMonitor"
	Device		"NVIDIAGeForce4"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1792	1344
		Modes		"1280x1024@75"	"1280x960@60"	"1152x864@75"	"1280x1024@60"	"1024x768@60"	"1280x960@75"	"1024x768@70"	"1400x1050@60"	"1024x768@75"	"1400x1050@75"	"832x624@75"	"1600x1200@65"	"800x600@60"	"1600x1200@60"	"800x600@75"	"1792x1344@60"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection
Section "Screen" #    
	Identifier	"RightScreen"
	Device		"ATIRadeon"
	Defaultdepth	24
	Monitor		"RightMonitor"
	SubSection "Display"
		Depth	24
		Modes		"1024x768@75"	"1024x768@70"	"832x624@75"	"1024x768@60"	"800x600@60"	"1152x864@75"	"800x600@75"	"1280x1024@75"	"800x600@72"	"1280x960@60"	"800x600@56"	"1280x1024@60"	"640x480@75"	"1280x960@75"	"640x480@72"	"1400x1050@60"	"640x480@60"	"1400x1050@75"	"1600x1200@65"	"1600x1200@60"	"1792x1344@60"
	EndSubSection
EndSection
Section "Screen" #    
	Identifier	"LeftScreen"
	Device		"Voodoo3"
	Defaultdepth	24
	Monitor		"LeftMonitor"
	SubSection "Display"
		Depth	24
		Modes		"1024x768@75"	"1024x768@70"	"832x624@75"	"1024x768@60"	"800x600@60"	"1152x864@75"	"800x600@75"	"1280x1024@75"	"800x600@72"	"1280x960@60"	"800x600@56"	"1280x1024@60"	"640x480@75"	"1280x960@75"	"640x480@72"	"1400x1050@60"	"640x480@60"	"1400x1050@75"	"1600x1200@65"	"1600x1200@60"	"1792x1344@60"
	EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"Triple Monitors"
	Screen 0 "CenterScreen" 0 0
	Screen 1 "RightScreen" RightOf "CenterScreen"
	Screen 2 "LeftScreen" LeftOf "CenterScreen"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
EndSection

```

While it doesn't crash, the other two monitors stay blank.  Any clues?

---

### Post by aidave on 2008-03-14
Are there any techs that would solve this?
dunno what else to do

---

### Post by aidave on 2008-03-16
going to try this xorg.conf that automagically detected and set up ALL THREE SCREENS!! holy crow.  im pasting this here cuz i dunno how else to copy it back and forth.

why dont ubuntu and mandriva work together??

```

# File generated by XFdrake (rev 230776)

Section "Extensions"
    Option "Composite"
EndSection
# **********************************************************************
# Refer to the xorg.conf man page for details about the format of
# this file.
# **********************************************************************

Section "ServerFlags"
    #DontZap # disable <Ctrl><Alt><BS> (server abort)
    AllowMouseOpenFail # allows the server to start up even if the mouse does not work
    #DontZoom # disable <Ctrl><Alt><KP_+>/<KP_-> (resolution switching)
EndSection

Section "Module"
    Load "dbe" # Double-Buffering Extension
    Load "v4l" # Video for Linux
    Load "extmod"
    Load "type1"
    Load "freetype"
    Load "glx" # 3D layer
EndSection

Section "InputDevice"
    Identifier "Keyboard1"
    Driver "kbd"
    Option "XkbModel" "pc105"
    Option "XkbLayout" "us"
    Option "XkbOptions" "compose:rwin"
EndSection

Section "InputDevice"
    Identifier "Mouse1"
    Driver "mouse"
    Option "Protocol" "ExplorerPS/2"
    Option "Device" "/dev/mouse"
EndSection

Section "InputDevice"
    Identifier "Mouse2"
    Driver "evdev"
    Option "bustype" "0x0003"
    Option "product" "0xc01e"
    Option "relBits" "+0+1+2"
    Option "HWheelRelativeAxisButtons" "7 6"
    Option "vendor" "0x046d"
EndSection

Section "Monitor"
    Identifier "monitor1"
    VendorName "Plug'n Play"
    ModelName "L1932TX "
    HorizSync 30-83
    VertRefresh 56-75
    
    # TV fullscreen mode or DVD fullscreen output.
    # 768x576 @ 79 Hz, 50 kHz hsync
    ModeLine "768x576"     50.00  768  832  846 1000   576  590  595  630
    
    # 768x576 @ 100 Hz, 61.6 kHz hsync
    ModeLine "768x576"     63.07  768  800  960 1024   576  578  590  616
EndSection

Section "Monitor"
    Identifier "monitor2"
    
    # TV fullscreen mode or DVD fullscreen output.
    # 768x576 @ 79 Hz, 50 kHz hsync
    ModeLine "768x576"     50.00  768  832  846 1000   576  590  595  630
    
    # 768x576 @ 100 Hz, 61.6 kHz hsync
    ModeLine "768x576"     63.07  768  800  960 1024   576  578  590  616
EndSection

Section "Monitor"
    Identifier "monitor3"
    
    # TV fullscreen mode or DVD fullscreen output.
    # 768x576 @ 79 Hz, 50 kHz hsync
    ModeLine "768x576"     50.00  768  832  846 1000   576  590  595  630
    
    # 768x576 @ 100 Hz, 61.6 kHz hsync
    ModeLine "768x576"     63.07  768  800  960 1024   576  578  590  616
EndSection

Section "Device"
    Identifier "device1"
    VendorName "nVidia Corporation"
    BoardName "NVIDIA GeForce FX - GeForce 8800"
    Driver "nvidia"
    Screen 0
    BusID "PCI:1:0:0"
    Option "DPMS"
    Option "RenderAccel" "false"
    Option "AddARGBGLXVisuals"
EndSection

Section "Device"
    Identifier "device2"
    VendorName "ATI Technologies Inc"
    BoardName "ATI Radeon 9250 and earlier"
    Driver "ati"
    Screen 0
    BusID "PCI:2:10:0"
    Option "DPMS"
    Option "XaaNoOffscreenPixmaps" "1"
EndSection

Section "Device"
    Identifier "device3"
    VendorName "3Dfx Interactive, Inc."
    BoardName "3DFX Voodoo 3 - 5 / Banshee / Rush"
    Driver "tdfx"
    Screen 0
    BusID "PCI:2:12:0"
    Option "DPMS"
EndSection

Section "Screen"
    Identifier "screen1"
    Device "device1"
    Monitor "monitor1"
    DefaultColorDepth 24
    
    Subsection "Display"
        Depth 8
        Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "640x480" "480x360" "320x240"
    EndSubsection
    
    Subsection "Display"
        Depth 15
        Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "640x480" "480x360" "320x240"
    EndSubsection
    
    Subsection "Display"
        Depth 16
        Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "640x480" "480x360" "320x240"
    EndSubsection
    
    Subsection "Display"
        Depth 24
        Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "640x480" "480x360" "320x240"
    EndSubsection
EndSection

Section "Screen"
    Identifier "screen2"
    Device "device2"
    Monitor "monitor2"
    DefaultColorDepth 24
    
    Subsection "Display"
        Depth 8
        Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "640x480" "480x360" "320x240"
    EndSubsection
    
    Subsection "Display"
        Depth 15
        Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "640x480" "480x360" "320x240"
    EndSubsection
    
    Subsection "Display"
        Depth 16
        Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "640x480" "480x360" "320x240"
    EndSubsection
    
    Subsection "Display"
        Depth 24
        Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "640x480" "480x360" "320x240"
    EndSubsection
EndSection

Section "Screen"
    Identifier "screen3"
    Device "device3"
    Monitor "monitor3"
    DefaultColorDepth 24
    
    Subsection "Display"
        Depth 8
        Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "640x480" "480x360" "320x240"
    EndSubsection
    
    Subsection "Display"
        Depth 15
        Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "640x480" "480x360" "320x240"
    EndSubsection
    
    Subsection "Display"
        Depth 16
        Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "640x480" "480x360" "320x240"
    EndSubsection
    
    Subsection "Display"
        Depth 24
        Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "640x480" "480x360" "320x240"
    EndSubsection
EndSection

Section "ServerLayout"
    Identifier "layout1"
    InputDevice "Keyboard1" "CoreKeyboard"
    InputDevice "Mouse1" "CorePointer"
    InputDevice "Mouse2" "SendCoreEvents"
    Screen "screen1"
    Screen "screen2" RightOf "screen1"
    Screen "screen3" RightOf "screen2"
    #Option "Xinerama"
EndSection
```

---

### Post by aidave on 2008-03-16
Ubuntu could not handle it.  It kept rebooting over and over!

---

