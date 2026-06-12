---
title: "SVIDEO Out on 8800GS - option missing?"
date: 2009-10-24
forum: Multimedia Software
---

### Post by Durandle on 2009-10-24
Hi,

I've been trying various suggestions from here and other forums (most of which are out of date) in order to get the svideo out port to work under Xubuntu.

Currently I have nvidia driver 185.18.36 installed, but the setting program insists it can't find any svideo. I've tried various ways of editing the xorgs.conf, all of which have resulted in not being able to restart gdm or a blank screen - I did manage to at one point have it turn off my LCD screen and output only to svideo, but the screen  was a mess of fuzz lines static and pink.

Any help here would be fantastic, having a HTPC that can't output to my TV kinda makes it not an HTPC!

For reference the current state of my xorgs.conf is anything but clean:

------------------
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen 0       "Screen0" 0 0
    Screen 1       "Screen1" rightof "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
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

Section "Monitor"
        Identifier      "Monitor" #CRT
EndSection

Section "Monitor"
        Identifier      "Television" #TV
        HorizSync 30-50
        VertRefresh 60
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    Screen 0
    Option         "NoLogo"        "true"
    Option         "RenderAccel"   "true"
    BusID          "PCI:01:0:0"
#    Option         "ConnectedMonitor" "CRT,TV"
EndSection

Section "Device"
        Identifier      "Device1"
        Driver          "nvidia"
        Screen 1
        BusID           "PCI:01:0:0"
EndSection

Section "Screen"
        Identifier      "Screen0"
        Device          "Device0"
        Monitor         "Monitor"
        DefaultDepth    24
        Option          "NoLogo" "True"
        Option          "ConnectedMonitor" "Monitor"
        SubSection "Display"
                Depth      24
                Modes      "nvidia-auto-select"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Screen1"
        Device          "Device1"
        Monitor         "Television"
        DefaultDepth    24
        Option  "TVOutFormat" "SVIDEO"
        Option  "TVStandard" "PAL-I"
        Option  "ConnectedMonitor" "Television"
        SubSection "Display"
                Depth 24
                Modes "640x480"
        EndSubSection
EndSection
------------------

---

### Post by Durandle on 2009-10-25
Additional to this, whenever I restart it sets the screen resolution to the default, no matter what it was when it was shutdown.

---

