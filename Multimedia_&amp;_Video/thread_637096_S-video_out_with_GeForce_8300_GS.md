---
title: "S-video out with GeForce 8300 GS"
date: 2007-12-10
forum: Multimedia &amp; Video
---

### Post by redfrog on 2007-12-10
I'm running ubuntu version 7.10 and am trying to run my computer through my CRT TV to watch movies on but am having problems.

I've hooked the s-video lead and sound leads to the tv but nothing is happening.

my /etc/X11/xorg.conf  is as follows:-


Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL E771a"
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync +vsync interlace
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
EndSection

Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8300 GS]"
    Driver         "nvidia"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G80 [GeForce 8300 GS]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard0"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "640x480@60"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard1"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: 1024x768 +0+0; CRT: 320x175 +0+0"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Virtual     1400 1050
        Depth       24
        Modes      "1024x768@60" "1024x768@43" "1024x768@70" "1152x864@75" "1024x768@75" "1280x960@60" "1024x768@85" "1280x1024@60" "832x624@75" "1400x1050@60" "800x600@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56" "640x480@85" "640x480@75" "640x480@72" "640x480@60"
    EndSubSection
EndSection

any ideas?

---

### Post by njparton on 2007-12-10
Try rebooting with just the TV hooked up to see if that forces it's detection?

---

### Post by redfrog on 2007-12-10
> **njparton said:**
> Try rebooting with just the TV hooked up to see if that forces it's detection?

Ok, did that and it does seem to work.  However, the computer is through a wall so I can't use it without restarting it with the tv unplugged and the monitor plugged in - not exactly ideal.

---

### Post by njparton on 2007-12-10
Hmmm, sorry I'm out as I've never done this outside of windows :(

---

### Post by redfrog on 2007-12-11
Ok heres what has happened so far:-

I booted my computer with just the TV connected via s-video out cable.  This worked fine on start-up with my TV shwing the ubuntu logo and progress bar etc.  Then it gioes funny, eventuaklly displaying half a screen of gibberish and what seems to be an warning that says something along the lines of 'starting in low graphics mode'.

If i run 'sudo nvidia-settings' ,  plug my tv in then press 'detect displays then my computer finds the tv.  i can then select 'twin view' and 'save to X configuration file'.  However, when I restart X or restart the computer I get no out put from my monitor and a similar situation to above on my tv.

Anyone got any ideas?

---

### Post by redfrog on 2007-12-11
Sorry to keep bumping this thread.

I've just noticed that the s-cideo out lead has a connection with 4 pins, while te actual connection at the back of my 'pooter seems to take a cable with 8 or so pins - is this likely to be the problem?

---

### Post by redfrog on 2007-12-11
Right.  This thread is turning into more of a blog than anything else but there we go.

I have edited my /etc/X11/xorg.conf to this:-

> 
...

EndSection

Section "Device"
	Identifier	"Device[0]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
        screen 0
EndSection

Section "Device" 
        Driver          "nvidia" 
        Identifier      "Device[1]" 
        Screen 1 
        Option          "TVOutFormat" "SVIDEO" #or SVIDEO etc 
        Option          "TVStandard" "PAL-I" #or NTSC etc 
        Option          "ConnectedMonitor" "Monitor[1]" 
        BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection

Section "Monitor"
	Identifier	"Monitor[0]" #Primary monitor
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Monitor" 
        Identifier "Monitor[1]" #TV
        HorizSync 30-50
        VertRefresh 60
EndSection


Section "Screen"
	Identifier	"Screen[0]"
	Device		"Device[0]"
	Monitor		"Monitor[0]"
	Defaultdepth	24
EndSection

Section "Screen" 
        Device "Device[1]" 
        Identifier "Screen[1]" 
        Monitor "Monitor[1]" 
        DefaultDepth 24 
        SubSection "Display" 
               Depth 24 
               Modes "1024x768_60" 
        EndSubSection    
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
        Screen 0 "Screen[0]"
        Screen 1 "Screen[1]" RightOf "Screen[0]"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection


The result of this is that if I boot my computer with the s-video out connected then I get visual output to my TV with no apprent problems (the edges are cut off but that must be easy to fix, right?) but nothing at all on my monitor.  If I then reboot with the s-video disconnected my monitor works as normal.

Anone got any ideas?

---

