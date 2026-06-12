---
title: "Dual Monitors - Dell D820 w/docking station"
date: 2007-04-19
forum: Multimedia &amp; Video
---

### Post by abuthemagician on 2007-04-19
I have been working on getting a D820 with a docking station to do TwinView with an Nvidia Quadro NVS 120m video card and a dell D-Dock docking station. I think i have my xorg.conf setup right, but it keeps telling me it can't find any screens. It also complains about my modelines for the syncmaster, Could someone point me in the right direction? thanks in advance

here is my config:

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
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver "synaptics"
	Option "SendCoreEvents" "true"
	Option "Device" "/dev/psaux"
	Option "Protocol" "auto-dev"
	Option "Emulate3Buttons" "on"
	Option "SHMConfig" "on"
	Option "LeftEdge" "130"
	Option "RightEdge" "840"
	Option "TopEdge" "130"
	Option "BottomEdge" "640"
	Option "FingerLow" "14"
	Option "FingerHigh" "15"
	Option "MaxTapTime" "180"
	Option "MaxTapMove" "110"
	Option "ClickTime" "0"
	Option "MaxDoubleTapTime" "100"
	Option "EmulateMidButtonTime" "75"
	Option "VertScrollDelta" "20"
	Option "HorizScrollDelta" "20"
	Option "MinSpeed" "0.60"
	Option "MaxSpeed" "1.10"
	Option "AccelFactor" "0.130"
	Option "EdgeMotionMinSpeed" "200"
	Option "EdgeMotionMaxSpeed" "200
	Option "UpDownScrolling" "1"
	Option "CircularScrolling" "1"
	Option "CircScrollDelta" "0.1"
	Option "CircScrollTrigger" "2"
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
	Identifier	"NVIDIA Quadro NVS 120M"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option "TwinView" "True"
	Option "TwinViewOrientation" "RightOf"   
	Option "UseEdidFreqs" "True"
	Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
	Option "UseDisplayDevice" "VGA" #replace 'string' with either 'DFP' (Digital flat panel connected via DVI port), 'CRT' (any monitor that is connected via VGA ports), or 'TV'
EndSection

Section "Monitor"
	Identifier	"Laptop Panel"
	Option		"DPMS"
	HorizSync	31.5-90.0
	VertRefresh	60-60
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	ModelName 	“SyncMaster 740N”
	Option “DPMS”
	HorizSync 30-81
	VertRefresh 56-75
	# 1280×1024 @ 75.00 Hz (GTF) hsync: 80.17 kHz; pclk: 138.54 MHz
	Modeline “1280×1024_75.00&#8243; 138.54 1280 1368 1504 1728 1024 1025 1028 1069 -HSync +Vsync

	# 1280×1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
	Modeline “1280×1024_60.00&#8243; 108.88 1280 1360 1496 1712 1024 1025 1028 1060 -HSync +Vsync

	# 1024×768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 81.80 MHz
	Modeline “1024×768_75.00&#8243; 81.80 1024 1080 1192 1360 768 769 772 802 -HSync +Vsync

	# 800×600 @ 75.00 Hz (GTF) hsync: 47.02 kHz; pclk: 48.91 MHz
	Modeline “800×600_75.00&#8243; 48.91 800 840 920 1040 600 601 604 627 -HSync +Vsync
	
	# 640×480 @ 75.00 Hz (GTF) hsync: 37.65 kHz; pclk: 30.72 MHz
	Modeline “640×480_75.00&#8243; 30.72 640 664 728 816 480 481 484 502 -HSync +Vsync

	# TV fullscreen mode or DVD fullscreen output.
	# 768×576 @ 79 Hz, 50 kHz hsync
	ModeLine “768×576&#8243; 50.00 768 832 846 1000 576 590 595 630

	# 768×576 @ 100 Hz, 61.6 kHz hsync
	ModeLine “768×576&#8243; 63.07 768 800 960 1024 576 578 590 616
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Quadro NVS 120M"
	Monitor		"Laptop Panel"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"SyncMaster 740n"
	Device		"NVIDIA Quadro NVS 120M"
	Monitor		“SyncMaster”
	DefaultDepth 24
	SubSection “Display”
		Depth 1
		Modes “1280×1024 &#8243; “1152×864 &#8243; “1024×768 &#8243; “832×624 &#8243; “800×600 &#8243; “720×400 &#8243; “640×480 &#8243;
	EndSubSection
	SubSection “Display”
		Depth 4
		Modes “1280×1024 &#8243; “1152×864 &#8243; “1024×768 &#8243; “832×624 &#8243; “800×600 &#8243; “720×400 &#8243; “640×480 &#8243;
	EndSubSection
	SubSection “Display”
		Depth 8
		Modes “1280×1024 &#8243;
	EndSubSection
	SubSection “Display”
		Depth 15
		Modes “1280×1024 &#8243; “1152×864 &#8243; “1024×768 &#8243; “832×624 &#8243; “800×600 &#8243; “720×400 &#8243; “640×480 &#8243;
	EndSubSection
	SubSection “Display”
		Depth 16
		Modes “1280×1024 &#8243; “1152×864 &#8243; “1024×768 &#8243; “832×624 &#8243; “800×600 &#8243; “720×400 &#8243; “640×480 &#8243;
	EndSubSection
	SubSection “Display”
		Depth 24
		Modes “1280×1024 &#8243; “1152×864 &#8243; “1024×768 &#8243; “832×624 &#8243; “800×600 &#8243; “720×400 &#8243; “640×480 &#8243;
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Laptop Screen" 0 0
	Screen	 	"SyncMaster" RightOf "Laptop Screen"
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

### Post by sshetye on 2007-04-24
> **abuthemagician said:**
> I have been working on getting a D820 with a docking station to do TwinView with an Nvidia Quadro NVS 120m video card and a dell D-Dock docking station. I think i have my xorg.conf setup right, but it keeps telling me it can't find any screens. It also complains about my modelines for the syncmaster, Could someone point me in the right direction? thanks in advance

here is my config:


You may want to configure using nvidia-settings. Use **"sudo nvidia-settings" to use the "save xorg.conf" option to make the changes permanent**. This is an application similar to the windows nvidia display applet and REALLY simplifies dual-view etc. FYI, I'm on the same laptop model with the same nvidia chip :) - but it shouldn't matter, it should work with most nvidia chips.

The X driver I used were Feisty's "restricted" nvidia driver and I _think_ nvidia-settings comes with it when you install the restricted drivers. I cannot recollect if I had to install them on my own or they were preinstalled during OS installation. 

Start -> System -> Administration -> Synaptic Package manager / apt-get are your friends ! 

cheers
Siddharth

---

### Post by abuthemagician on 2007-04-24
I actually got it working with Nvidia Settings. Now my problem is that everything opens on the attached monitor by default instead of the laptop panel. Also, it spans my wall paper which i find annoying. It would be nice to have a feature like vista does where it will scale the background on each monitor to fit the wallpaper.

here is my config for future internet folks who need it or know how to fix my gripes:

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Mon Feb 26 23:39:38 PST 2007

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Mouse1"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load        "dbe"
    Load        "extmod"
    Load        "type1"
    Load        "freetype"
    Load        "glx"
    Load	"bitmap"
    Load	"ddc"
    Load	"dri"
    Load	"int10"
    Load        "vbe"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier	"Mouse1"
    Driver "synaptics"
    Option "SendCoreEvents" "true"
    Option "Device" "/dev/psaux"
    Option "Protocol" "auto-dev"
    Option "Emulate3Buttons" "on"
    Option "SHMConfig" "on"
    Option "LeftEdge" "130"
    Option "RightEdge" "840"
    Option "TopEdge" "130"
    Option "BottomEdge" "640"
    Option "FingerLow" "14"
    Option "FingerHigh" "15"
    Option "MaxTapTime" "180"
    Option "MaxTapMove" "110"
    Option "ClickTime" "0"
    Option "MaxDoubleTapTime" "100"
    Option "EmulateMidButtonTime" "75"
    Option "VertScrollDelta" "20"
    Option "HorizScrollDelta" "20"
    Option "MinSpeed" "0.60"
    Option "MaxSpeed" "1.10"
    Option "AccelFactor" "0.130"
    Option "EdgeMotionMinSpeed" "200"
    Option "EdgeMotionMaxSpeed" "200
    Option "UpDownScrolling" "1"
    Option "CircularScrolling" "1"
    Option "CircScrollDelta" "0.1"
    Option "CircScrollTrigger" "2"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Option		"DPMS"
	HorizSync	31.5-90.0
	VertRefresh	60-60
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7400"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: nvidia-auto-select +1680+0, DFP: 1680x1050 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection


```

---

### Post by abuthemagician on 2007-09-05
Anyone ?

---

### Post by porcorosso on 2007-09-08
Well, I've been watching your thread and waiting for someone to post something constructive for you.

I'm afraid that all I have for you is a little commiseration from a fellow sufferer. I don't think a great deal of thought has been given yet to folks like us who use docking stations / port replicators on this platform.

In my case I want something different. I used Envy to install the "new" drivers, and I use Twinview. I have my external LCD (1680x1050) and built-in LCD (1920x1200) set as clones. This means that, when I'm docked, I crank up the system and BOTH monitors come up with duplicate desktops (at the lower resolution). I actually have to open the lid on the notebook and hit Fn-F8 to switch all output to external DVI only. Then I close the lid and go about my business.

When I boot undocked, the built-in LCD comes up at 180x1050, and I have to use nvidia-settings to set it to 1920x1200.

I'm sure that metamodes has a solution. But I did a lot of experimention, including use of the NULL setting in various combinations, and finally decided that it wasn't worth the hassle for now. I'll just use the system as is.

Funny thing is that the original installation using the Open Source drivers did all of this automatically for me. But then it didn't give me 3D acceleration, either. It's workable the way it is.

The setup currently has some awkward limitations, like what you mentioned about how the background is displayed and how difficult it is, when not using cloned settings, to get apps to open where you want them. I'll be interested to see where GG takes us with the video subsystem.

Good luck! And I'm sorry I had nothing solid to offer.

Well, maybe I have a little something. Did you look through the FAQs/ReadMe section at the nvidia.com site? There is some fairly in-depth descriptive language about various features of these drivers and the settings for them in xorg.conf. But you can do a LOT of trial and error without doing much more than finding out how to recover your xserver functionality -- if you know what I mean.

:confused:

---

### Post by cpetterborg on 2008-01-23
Anyone try to get Gutsy working with a D820 and docking station with TWO external monitors? I can't get the second external monitor to ever work. It will only use one external and the notebook LCD.

Thanks!

---

### Post by abuthemagician on 2008-01-24
i'll boot into ubuntu later and get my config for you. It is very similar to the one i posted below. I am using a D820 with a docking station and 2 Acer AL2216W 22" widescreen monitors

---

### Post by abuthemagician on 2008-01-31
here is my xorg.conf file. I have the Left monitor plugged into the DVI port on the docking station, and the Right monitor plugged into the VGA port on the docking station.

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:30:30 PDT 2007


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" 1680 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Mouse1"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
    Load           "bitmap"
    Load           "ddc"
    Load           "dri"
    Load           "int10"
    Load           "vbe"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Mouse1"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "Emulate3Buttons" "on"
    Option         "SHMConfig" "on"
    Option         "LeftEdge" "130"
    Option         "RightEdge" "840"
    Option         "TopEdge" "130"
    Option         "BottomEdge" "640"
    Option         "FingerLow" "14"
    Option         "FingerHigh" "15"
    Option         "MaxTapTime" "180"
    Option         "MaxTapMove" "110"
    Option         "ClickTime" "0"
    Option         "MaxDoubleTapTime" "100"
    Option         "EmulateMidButtonTime" "75"
    Option         "VertScrollDelta" "20"
    Option         "HorizScrollDelta" "20"
    Option         "MinSpeed" "0.60"
    Option         "MaxSpeed" "1.10"
    Option         "AccelFactor" "0.130"
    Option         "EdgeMotionMinSpeed" "200"
    Option         "EdgeMotionMaxSpeed" "200"
    Option         "UpDownScrolling" "1"
    Option         "CircularScrolling" "1"
    Option         "CircScrollDelta" "0.1"
    Option         "CircScrollTrigger" "2"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer AL2216W"
    HorizSync       31.0 - 84.0
    VertRefresh     56.0 - 77.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Acer AL2216W"
    HorizSync       31.0 - 84.0
    VertRefresh     56.0 - 77.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7400"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7400"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: 1680x1050 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "DFP-1: 1680x1050 +0+0; CRT: nvidia-auto-select +0+0"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: 1680x1050 +0+0; CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by Cerin on 2008-05-08
I'm on Ubuntu 8.04 with a Dell Latitude 630 and docking station. With the  open source nvidia driver, I can access one of the docking station's monitors just fine, but the other one is completely ignored. With the proprietary driver, I can't even login while docked since the docking station's monitors completely blank out. This is strange since I see the boot up screen just prior to that, so I guess the proprietary driver isn't being used yet at that point.

Unfortunately, I can't even undock, login, and then re-dock, since Ubuntu becomes completely unresponsive in the process. Has anyone gotten dual monitors working from the docking station with the open source driver?

---

### Post by abuthemagician on 2008-05-08
I had this problem a few times. I use the Proprietary driver, and when i first set it up i had to have both monitors hooked up, but leave the notebook open as well. Then i ran nvidia-settings using sudo (you may have to install it) and got it setup from there by playing around with different stuff and disabling the laptop panel.

here is a link that might help:
[http://my.opera.com/sjosul/blog/ubuntu-8-04-dual-monitor-setup]("http://my.opera.com/sjosul/blog/ubuntu-8-04-dual-monitor-setup")

---

