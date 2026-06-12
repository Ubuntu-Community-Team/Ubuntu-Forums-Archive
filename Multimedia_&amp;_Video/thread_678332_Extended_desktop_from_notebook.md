---
title: "Extended desktop from notebook"
date: 2008-01-25
forum: Multimedia &amp; Video
---

### Post by omgitsdev on 2008-01-25
Hey ya'll.

I'm running Gutsy on a Sony Vaio TZ-180n. The panel's native resolution is 1366x768. On it's own, the display functions perfectly, however, as it's super-tiny, I picked up a Samsung 906bw (native 1440x900) which after tweaking for a while, managed to configure for ubuntu. 

but not all the way. I'm not able to have my external LCD as an extension of my notebook panel (or vice versa) all the GUI options allow me to do is have a cloned screen... but not a good clone, the display on my notebook is set at 1440x900 such that i am only able to see the top left corner of what i see on my external LCD. This wouldn't bother me TOO much, but all my applications treat their environment as a 1366x768 space. Meaning: if i maximize a window, it fills up my entire notebook panel, but on the external LCD, there is a space on the right and bottom of the window that just displays the desktop background.

My questions, then, are: A) how do i fix to only display on my external LCD? B) How do i set up to have the external be an extension of my notebook panel?

---

### Post by bluefrog on 2008-02-08
if it helps, here is my xorg.conf for VAIO VGN-FS215E which enables a dual head extension for my laptop and an LCD. At the end of this post you will find my original single head xorg.conf

The only resolution I have for both screens is 1280x800 which is my "normal" laptop resolution.
I had to tweak xorg.conf by hand as the "screen and graphics" menu does not give anything workable.

James Dupin

dual head

```
Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "fr"
        Option          "XkbVariant"    "oss"
        Option          "XkbOptions"    "lv3:ralt_switch"
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
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Boardname       "i810"
        Busid           "PCI:0:2:0"
        Driver          "i810"
        Screen  0
        Option          "MonitorLayout" "CRT,LFP"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "screen0"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "screen0" 0 0
  screen 1 "screen1" rightof "screen0"
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
        Load            "GLcore"
        Load            "v4l"
EndSection
Section "device" #  
        Identifier      "device1"
        Boardname       "i810"
        Busid           "PCI:0:2:0"
        Driver          "i810"
        Screen  1
        Option          "MonitorLayout" "CRT,LFP"
EndSection
Section "screen" #  
        Identifier      "screen1"
        Device          "device1"
        Defaultdepth    24
        Monitor         "monitor1"
        SubSection "Display"              
                Modes           "1280x1024"
        EndSubSection
EndSection
Section "monitor" #  
        Identifier      "monitor1"
        Option          "DPMS"
EndSection
Section "ServerFlags"
        Option          "Xinerama"      "true"
EndSection
```

single head
```

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "fr"
        Option          "XkbVariant"    "oss"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

```

---

### Post by bluefrog on 2008-02-08
update...

One small problem with the later configuration, though. Gdm crashes upon screensaver activation.

I can live with it but just wanted to warn others...

James Dupin

---

