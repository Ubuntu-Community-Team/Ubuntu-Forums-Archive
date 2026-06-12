---
title: "NVidia TV-Out problems"
date: 2009-07-21
forum: Multimedia Software
---

### Post by Ineffablewombat on 2009-07-21
I'm having some trouble getting a Nvidia GeForce FX5500 card to properly display on my television.  I just put the card in a computer that's been running Ubuntu Server edition 8.10 for awhile.  I want the television to be the only display (I just want to use it for video playback, I can ssh in for everything else).  
I've confirmed that the nvidia proprietary drivers work, and was able to get X to display on an old monitor that I dragged out of the basement for troubleshooting purposes.  (Even getting to that point was quite an adventure, but envyng did the trick)    
Now I've hooked up the television, modified xorg.conf, and... Well.  I'm pretty sure it's doing *something*.  When I type startx the monitor goes blank, and the television goes from displaying black and white static, to displaying *green* and black and white static with little flecks of other colors.  
Here's my current xorg.conf: 
```

Section "Monitor"
        Identifier     "Monitor0"
        VendorName     "Unknown"
        ModelName      "Unknown"
        HorizSync       30.0 - 50.0
        VertRefresh     60
#       Option         "DPMS"
EndSection

Section "Screen"
        Identifier     "Screen0"
        Device         "Device0"
        Monitor        "Monitor0"
        SubSection "Display"
                Depth       24
                Modes       "640x480"
        EndSubSection
        Option "ConnectedMonitor" "TV"
        Option "TVOutFormat" "SVIDEO"
        Option "TVStandard" "NTSC-M"
EndSection

Section "Module"
        Load           "dbe"
        Load           "extmod"
        Load           "freetype"
        Load    "glx"
        Disable "dri2"
EndSection

Section "InputDevice"
        Identifier     "Mouse0"
        Driver         "mouse"
        Option         "Protocol" "auto"
        Option         "Device" "/dev/psaux"
        Option         "Emulate3Buttons" "no"
        Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
        Identifier     "Keyboard0"
        Driver         "kbd"
EndSection

Section "ServerLayout"
        Identifier     "Layout0"
        Screen      0  "Screen0" 0 0
        InputDevice    "Keyboard0" "CoreKeyboard"
        InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Device"
        Identifier     "Device0"
        VendorName     "NVIDIA Corporation"
        Driver  "nvidia"
EndSection

```
I've used this television and the connector cord (SVIDEO plug on the video card end, plugs into the composite video in on the TV) mostly successfully on my main desktop computer (running ubuntu 8.10) as a secondary display using an Nvidia GeForce 8600.  I say "mostly" partially because running the cords over the the television requires extensions and couplers and so forth which means the signal degrades horribly if you look at it funny, and partially because from time to time, with no trigger that I can figure out, both displays get corrupted in a funny pattern of small yellow squares.  (Tangent- anyone have a clue what's up with that?)

---

