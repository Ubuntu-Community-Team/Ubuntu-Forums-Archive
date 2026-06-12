---
title: "Black frame problem with ATI X300 and Acer P191W"
date: 2008-09-04
forum: Multimedia Software
---

### Post by jkugler on 2008-09-04
I had a 24" Samsung working fine, but I'm trying to hook up a 19" Acer P191W to my laptop for a while.

This is Gutsy (7.10) on a Dell Latitude D610, and an ATI X300 video card using proprietary drivers.

Even configured at 1440x900, it kept trying to run the monitor at 1280x720.  I deleted everything except the references to 1440x900 from xorg.conf, and now the monitor tells me it's running at 1440x900, but there is a black frame all the way around the screen, and the visible area is only 1280x720.

It's not a video card memory issue, because it was running the Samsung 24" just fine.  Both were connected via DVI hooked up via a docking station, by the way.

Any ideas?

Here is my xorg.conf:

```
Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "microsoftpro"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc M22 [Mobility Radeon X300]"
        Boardname       "ati"
        Busid           "PCI:1:0:0"
        Driver          "fglrx"
        Screen  0
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel 1024x768"
        Horizsync       31.5-48.0
        Vertrefresh     56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc M22 [Mobility Radeon X300]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Modes           "1024x768@60"   "800x600@60"    "800x600@56"    "640x480@60"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
  screen 1 "screen1" leftof "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
        Inputdevice     "Synaptics Touchpad"
EndSection
Section "Module"
        Load            "glx"
        Load            "dbe"
        Load            "v4l"
EndSection
Section "Extensions"
        Option          "Composite"     "0"
EndSection
Section "device" #
        Identifier      "device1"
        Boardname       "ati"
        Busid           "PCI:1:0:0"
        Driver          "fglrx"
        Screen  1
        #Option "IgnoreEdid" "True"
EndSection
Section "screen" #
        Identifier      "screen1"
        Device          "device1"
        Defaultdepth    24
        Monitor         "monitor1"
        SubSection "Display"
                Depth   24
                #Modes          "1440x900@60"   "1280x800@60"   "1280x720@60"   "1280x768@60"   "800x600@60"    "800x600@56"
                Modes           "1440x900@60"
        EndSubSection
EndSection
Section "monitor" #
        Identifier      "monitor1"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel 1440x900"
        Horizsync       31.5-56.0
        Vertrefresh     56.0 - 65.0
        #modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
        #modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
        #modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
        #modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
        #modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
        modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 934 -hsync +vsync
        Gamma   1.0
        DisplaySize 1440 900
EndSection
Section "ServerFlags"
        Option          "Xinerama"      "true"
EndSection
```

---

