---
title: "Wacom and Twinview"
date: 2008-11-28
forum: Multimedia Software
---

### Post by tikitika999 on 2008-11-28
I've checked the How-to links and all that stuff, honestly. But either I'm not getting where to put what, or somethings wrong...

Anyway I need to isolate my wacom tablet to only a single screen, as I use twinview for dual monitors. I've tried a lot of things and none seem to work at all.

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
        InputDevice    "stylus"    "SendCoreEvents"
        InputDevice    "eraser"    "SendCoreEvents"
        InputDevice    "cursor"    "SendCoreEvents"    #For non-LCD tablets only
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
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
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  #Option        "Device"        "/dev/ttyS0"          #SERIAL ONLY
  Option        "Device"        "/dev/input/wacom"   #USB ONLY
  Option        "Type"          "stylus"
  Option        "USB"           "on"                  #USB ONLY
  #Option        "ForceDevice"   "ISDV4"               #Tablet PC ONLY
   Option "PressCurve" "50,0,100,50"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  #Option        "Device"        "/dev/ttyS0"          #SERIAL ONLY
  Option        "Device"        "/dev/input/wacom"   #USB ONLY
  Option        "Type"          "eraser"
  Option        "USB"           "on"                  #USB ONLY
  #Option        "ForceDevice"   "ISDV4"               #Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  #Option        "Device"        "/dev/ttyS0"          #SERIAL ONLY
  Option        "Device"        "/dev/input/wacom"   #USB ONLY
  Option        "Type"          "cursor"
  Option        "Mode"          "relative"
  Option        "USB"           "on"                  #USB ONLY
  #Option        "ForceDevice"   "ISDV4"               #Tablet PC ONLY
  Option        "Twinview" "horizontal"
  Option        "ScreenNo" "0" 
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HSD AG191"
    HorizSync       30.0 - 83.0
    VertRefresh     55.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6600"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "CRT: nvidia-auto-select +1680+0, DFP: nvidia-auto-select +0+0"   
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

I probably sound like the biggest idiot and that stuff makes it all look horrendously stupid, eh?

---

### Post by fraterm on 2008-11-29
UPDATE:

Have a look searching around for some things for instance:

[http://ubuntuforums.org/showthread.php?t=640898](http://ubuntuforums.org/showthread.php?t=640898)
[http://linuxwacom.sourceforge.net/index.php/howto/inputdev](http://linuxwacom.sourceforge.net/index.php/howto/inputdev)


I'm in the same boat as you and in the midst of the same TwinView Growing Pains.

I'll let you know what my verdict is.

UPDATE: Found that the answer was indeed the options mentioned, namely for each Section "InputDevice" you have in your conf.

for me, stylus, eraser, cursor, and for me pad I have the Option "TwinView" "Horizontal" followed by Option "ScreenNo" "0"

---

### Post by tikitika999 on 2008-11-30
Thanks, I'll try it out and see how it goes.

---

### Post by fraterm on 2008-12-02
> **tikitika999 said:**
> Thanks, I'll try it out and see how it goes.

Curious as to what you were able to get.

I tried setting it to use screen 1 instead of 0 but had no luck with that, so for now I'm stuck with only one monitor to play with my graphire 3, I kind of wanted the right side window to be the drawing zone since it would not have a gnome desktop panel to compete with, but am still investigating how to do it.

Screen 0 is my left monitor Screen 1 is my right.

---

### Post by poobslag on 2009-02-26
I got Wacom and Twinview playing nicely the same way you did, by setting Twinview=horizontal and ScreenNo=0. Strangely though, this only kind-of restricts the stylus to the left monitor - it still strays about 100 pixels onto the right monitor. Here's the relevant bit of my xorg.conf:

```

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom" # USB ONLY?
  Option        "Type"          "stylus"
  Option        "USB"           "on"               # USB ONLY
  Option        "Twinview" "horizontal"
  Option        "ScreenNo" "0"
EndSection

```

The left monitor is at 1280x1024, and the right monitor is at 1440x900 (it's an HD monitor.) Any clue as to how to fix this behavior, to restrict the cursor to my left monitor? I tried playing with some of the other options. "KeepShape" makes the problem noticably worse, allowing the cursor to stray even further onto the right monitor. "BottomX" and "BottomY" are for restricting the "active zone" of my tablet, but there aren't any options to restrict the "active zone" of my monitor.

---

### Post by timmywear on 2009-08-14
Thanks for the guide!!!
This works fine except it maps the tablet on the wrong monitor.
My left monitor is "1"    My right monitor "0"

On my xorg.conf I have to set to My right monitor "0". Maybe I missed something? Here it goes...

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder62)  Wed May 27 01:59:40 PDT 2009


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "stylus"    "SendCoreEvents"
    InputDevice    "eraser"    "SendCoreEvents"
    InputDevice    "cursor"    "SendCoreEvents"
    InputDevice    "pad"
EndSection

Section "Files"
    ModulePath      "/usr/lib64/xorg/modules/extensions/nvidia"
    ModulePath      "/usr/lib64/xorg/modules/drivers"
    ModulePath      "/usr/lib64/xorg/modules"
    FontPath        "/usr/share/fonts/default/Type1"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/input/mice"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from data in "/etc/sysconfig/keyboard"
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option         "XkbLayout" "us"
    Option         "XkbModel" "pc105"
EndSection

Section "InputDevice"
    Driver "wacom"
    Identifier "stylus"
    Option "Device" "/dev/input/wacom"
    Option "Stylus2" "3" # set button to right click
    Option "Type" "stylus"
    Option "USB" "on"
    Option "PressCurve" "50,0,100,50" # Custom preference
    Option "Twinview" "horizontal"
    Option  "ScreenNo" "0"

EndSection

Section "InputDevice"
    Driver "wacom"
    Identifier "eraser"
    Option "Device" "/dev/input/wacom"
    Option "Type" "eraser"
    Option "USB" "on"
    Option "Twinview" "horizontal"
    Option  "ScreenNo" "0"
EndSection

Section "InputDevice"
    Driver "wacom"
    Identifier "cursor"
    Option "Device" "/dev/input/wacom"
    Option "Type" "cursor"
    Option "USB" "on"
    Option "Twinview" "horizontal"
    Option  "ScreenNo" "0"
EndSection

Section "InputDevice"
    Driver "wacom"
    Identifier "pad"
    Option "Device" "/dev/input/wacom"
    Option "Type" "pad"
    Option "USB" "on"
    Option "Twinview" "horizontal"
    Option  "ScreenNo" "0"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Sony SDM-HS95P"
    HorizSync       28.0 - 81.0
    VertRefresh     48.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "HP vs17"
    HorizSync       30.0 - 83.0
    VertRefresh     50.0 - 76.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GT"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"

    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: nvidia-auto-select +1280+0, CRT-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

