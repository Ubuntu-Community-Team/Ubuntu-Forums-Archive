---
title: "ATI dual head working, resolution issue with one head"
date: 2008-01-09
forum: Multimedia &amp; Video
---

### Post by BigEHokie on 2008-01-09
I should have included this with the title, but i am having issues with Gutsy.

I used the aticonfig --initial=dual-head process to get a dual head setup that (almost) works.  One of the monitors seems to be set at 1400x1050 (I think) but it only supports 1280x1024.  Here is my setup:

Dell D610 connected to docking station.  BenQ 17" connected with DVI, Dell 17" connected via VGA.  The Dell monitor is the one with the resolution issue, the BenQ is fine.

Here is my xorg.conf

```

Section "Files"
EndSection

Section "InputDevice"
    Identifier  "Generic Keyboard"
    Driver      "kbd"
    Option      "CoreKeyboard"
    Option      "XkbRules"  "xorg"
    Option      "XkbModel"  "pc105"
    Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier  "Configured Mouse"
    Driver      "mouse"
    Option      "CorePointer"
    Option      "Device"    "/dev/input/mice"
    Option      "Protocol"  "ImPS/2"
    Option      "ZAxisMapping"  "4 5"
    Option      "Emulate3Buttons"   "true"
EndSection

Section "InputDevice"
    Identifier  "Synaptics Touchpad"
    Driver      "synaptics"
    Option      "SendCoreEvents"    "true"
    Option      "Device"    "/dev/psaux"
    Option      "Protocol"  "auto-dev"
    Option      "HorizEdgeScroll"   "0"
EndSection

Section "InputDevice"
    Driver      "wacom"
    Identifier  "stylus"
    Option      "Device"    "/dev/input/wacom"
    Option      "Type"  "stylus"
    Option      "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver      "wacom"
    Identifier  "eraser"
    Option      "Device"    "/dev/input/wacom"
    Option      "Type"  "eraser"
    Option      "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver      "wacom"
    Identifier  "cursor"
    Option      "Device"    "/dev/input/wacom"
    Option      "Type"  "cursor"
    Option      "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
    Identifier  "ATI Technologies Inc M22 [Mobility Radeon X300]"
    Driver      "fglrx"
    Busid       "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier  "Generic Monitor"
    Option      "DPMS"
EndSection

Section "Screen"
    Identifier  "Default Screen"
    Device      "ATI Technologies Inc M22 [Mobility Radeon X300]"
    Monitor     "Generic Monitor"
    Defaultdepth    24
    SubSection "Display"
        Modes       "1400x1050" "1280x1024"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier  "Default Layout"
  screen "Default Screen"
    Inputdevice "Generic Keyboard"
    Inputdevice "Configured Mouse"

    # Uncomment if you have a wacom tablet
    #   InputDevice     "stylus"    "SendCoreEvents"
    #   InputDevice     "cursor"    "SendCoreEvents"
    #   InputDevice     "eraser"    "SendCoreEvents"
    Inputdevice "Synaptics Touchpad"
EndSection
Section "Module"
    Load        "glx"
EndSection
Section "Extensions"
    Option      "Composite" "0"
EndSection

```

Some things I tried....I tried removing the 1400x1050 mode, but that did nothing.  When I use a different xorg.conf and start the machine with only the single BenQ monitor configured in X, the Dell is "cloned" and still has this same problem.

Any suggestions on how to get the resolution on the Dell to be correct?  It's missing about 15% of the left part of the screen and about 10% from the top of teh screen.

Thanks in advance.

---

