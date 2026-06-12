---
title: "Terrible performance of Intel GMA 950"
date: 2009-03-19
forum: Multimedia Software
---

### Post by pugofstardock on 2009-03-19
Hi, 
i have the problem of terrible slow graphics
i have an Toshiba satellite l40-137 notebook 
Core Duo 2x1,73 Ghz, 2 Gb of RAM, Intel GMA 950 Graphics connected via VGA to an external LCD (1440x900) and running Jaunty 

glxgears shows about 270 fps and even 720p h264 which runs fine on windows, stutters like hell

It WAS ok once but i dont know why it changed. 
I tried every tweak in xorg.conf i could find (see below) 

Also I tried glxgears on KDE 4 instead of gnome but no difference

Any help would be great, because i hate it to be outperformed by my wifes 2003 HP NX7000 (1,6 Ghz Centrino 512 MB RAM) on XP

Oh and sorry for the most probably terrible englisch. I'm German. 

```



Section "Screen"
        Identifier      "Configured Screen Device"
        Device  "Configured Video Device"
        DefaultDepth    24

EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

Section "Device"
        Identifier    "Intel 945"
        Boardname    "Intel 945"
        Busid        "PCI:0:2:0"
        Driver        "intel"
        Vendorname    "Intel"
        Option  "DRI"   "True"
        Option  "FramebufferCompression"        "False" #if FBC is on screen freezes on unregular intervals
        VideoRam        131072






Option "XAANoOffscreenPixmaps" "true"
Option "AllowGLXWithComposite" "true"
Option "AddARGBGLXVisuals" "true"
Option "DisableGLXRootClipping" "true"
Option "AIGLX" "On"

Option "XvMC" "true"

#Option "MigrationHeuristic" "greedy" # freezes screen

EndSection


Section "Module"
Load "glx"
Load "GLcore"
Load "dri"
Load "v4l"
Load "ddc"
Load "extmod"
EndSection


Section "DRI"
        Mode    0666
EndSection


Section "InputDevice"
       Identifier      "Configured Mouse"
       Driver          "evdev"
       Option          "CorePointer"
       Option          "Buttons"       "7"
       Option          "ZAxisMapping"  "4 5"
       Option          "ButtonMapping" "1 2 3 6 7"
       Option          "Name"  "Logitech USB-PS/2 Optical Mouse"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection



```

---

### Post by mathiasbrito on 2009-03-30
I'm also experiencing poor performance after updating to Jaunty 9.04 Beta. The composites in Kwin, are slower then before. If I run glxinfo i'm informed that direct rendering are enabled. So I really don't know the reason for this behavior. I'm know running with composites disabled.

Any hints?

---

