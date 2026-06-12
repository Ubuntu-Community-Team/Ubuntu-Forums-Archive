---
title: "Is there any way to blacklist a particular resolution?"
date: 2007-09-19
forum: Multimedia &amp; Video
---

### Post by deadlydeathcone on 2007-09-19
I ask this because my monitor only supports one refresh rate per resolution, but for 640x480 two are detected:

```
Screen 0: minimum 320 x 240, current 1280 x 800, maximum 1280 x 800
default connected 1280x800+0+0 0mm x 0mm
   1280x800       50.0* 
   1024x768       51.0  
   800x600        52.0  
   800x512        53.0  
   720x450        54.0  
   640x512        55.0  
   640x480        56.0     57.0  
   640x400        58.0  
   640x384        59.0  
   512x384        60.0  
   400x300        61.0  
   320x240        62.0  
```

The problem is that the refresh rate of 56 is automatically selected (as it's the lowest), but it's out of range for my monitor: I need the 57 refresh rate.

I've searched quite a bit and found nothing for this, so sorry if it's been answered before. Is there a workaround?

Here's my xorg.conf. I added the "Modes" section, but to no avail:

```
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
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
        Option          "HorizScrollDelta"      "0"
EndSection

Section "Device"
        Identifier      "nVidia Corporation MCP51 PCI-X GeForce Go 6100"
        Driver          "nvidia"
        Busid           "PCI:0:5:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       30-75
        Vertrefresh     60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation MCP51 PCI-X GeForce Go 6100"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        Option          "TwinView" "0"
        SubSection "Display"
                Modes           "1280x800@60"   "1024x768@60"   "800x600@60"   "640x480@60"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "Synaptics Touchpad"
EndSection

Section "Module"
        Load            "glx"
EndSection

Section "ServerFlags"
        Option          "Xinerama"      "0"
EndSection

```

---

### Post by dcstar on 2007-09-20
> **deadlydeathcone said:**
> I ask this because my monitor only supports one refresh rate per resolution, but for 640x480 two are detected:
.......

Try installing the **xresprobe** and **discover1** packages, then do:
```
sudo dpkg-reconfigure xserver-xorg
```
and see if the monitor is correctly detected.

---

