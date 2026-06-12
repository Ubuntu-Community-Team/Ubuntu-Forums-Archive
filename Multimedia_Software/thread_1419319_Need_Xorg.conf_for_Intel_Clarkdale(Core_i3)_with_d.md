---
title: "Need Xorg.conf for Intel Clarkdale(Core i3) with dual monitor"
date: 2010-03-01
forum: Multimedia Software
---

### Post by ceh-photo.de on 2010-03-01
Hey,
i need a example of a working xorg.conf with Intel Clarkdale (Core i3) graphic device and dual monitor. I don`t know how to write it correct. My main problem is, who I specify for which output the device/monitor section is.

My first monitor should have a resolution of 1680x1050 and the second (right of them) 1280x1024. I want to have an extend desktop.

 My current try:

[PHP]

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "de"
Option "XkbVariant" "nodeadkeys"
EndSection
 
Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
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
Identifier "intel hd"
Driver "intel"
Option "XAANoOffscreenPixmaps" "true"
Option "DRI" "true"
Option     "monitor-VGA-1"  "ge"
Option     "monitor-HDMI-1" "samsung"
EndSection

Section "Monitor"
        Identifier      "samsung"
        # specifies a mode to be marked as the preferred initial mode of the monitor
        Option "PreferredMode"  "1680x1050"
        # This optional entry specifies the position of the monitor within the X screen. 
        #Option        "Position" "1024 0"
        #This optional entry specifies that the monitor should be ignored
        #     entirely, and not reported through RandR.  This is useful if the
        #     hardware reports  the  presence  of  outputs  that do not exist.
        #Option "Ignore"  "true"
EndSection

 

Section "Monitor"
        Identifier      "ge"
        #Options LeftOf, RightOf, Above, Below specify monitors' relative position
        Option "RightOf"  "samsung"
        # This optional entry specifies  whether  the  monitor  should  be
        #     turned  on  at  startup.  By default, the server will attempt to
        #     enable all connected monitors.
        #Option "Enable"  "true"        
        #This optional entry specifies the initial rotation of the given monitor.
        #     Valid values for rotation are "normal", "left", "right", and "inverted".
        # Option "Rotate"  "left"
EndSection

 
Section "Screen"
        Identifier      "samsungscreen"
        Device        "intel hd"
        Monitor       "samsung"
        DefaultDepth  24
        SubSection "Display"
                Depth          24
                Modes         "1680x1050"  "1024x768"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "ge Screen"
        Device        "intel hd"
        Monitor       "ge"
        DefaultDepth  24
        SubSection "Display"
                Depth          24
                Modes         "1280x1024"  "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 		"samsungscreen"
	Screen 		"ge Screen" RightOf "samsungscreen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "Module"
Load "dri"
Load "glx"
Load "dbe"
EndSection
 
Section "ServerFlags"
Option "AIGLX" "true"
EndSection
 
Section "DRI"
Group "video"
Mode 0660
EndSection
 
Section "Extensions"
Option "Composite" "Enable"
EndSection


[/PHP]

---

### Post by iskarion on 2010-03-02
I can't speak from own experience, as I have a single monitor setup. But did you already have a look at the official Intel driver website?
There is a quite detailed description how to setup dual head operation, including a xorg.conf example.
[http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html)

---

### Post by ceh-photo.de on 2010-03-02
yes i tried it in this way, but this is for a notebook chipset and I don`t know how to specify my output ports. because it ist hdmi1 and vga1.

regards
chris

---

### Post by ddeletic on 2011-03-14
Hi,

you could try shifting your 'Monitor' sections above the 'Device' section. Also, have a look at /var/log/Xorg.0.log file. 

Video outputs from my integrated Intel graphics card are called VGA1 and HDMI1 (not VGA-1 and HDMI-1). You can get these names by running 'xrandr -q'. You need to use these names in your device-option-monitor lines. I suspect these lines need to be changed to: 

    Option        "monitor-VGA1"  "ge"
    Option        "monitor-HDMI1" "samsung"

In addition, you may need to define a virtual screen big enough to hold your larger display twice. For this you need one Screen section, and you need to add:

        Virtual        3360 1050

line to SubSection "Display".

---

