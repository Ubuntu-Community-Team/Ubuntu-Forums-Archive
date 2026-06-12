---
title: "ATI Mobility Xpress 1250 question"
date: 2008-10-05
forum: Multimedia Software
---

### Post by slackskillz on 2008-10-05
When I first came to Ubuntu with a fresh install, I let the hardware manager automatically install a ATI driver, and I was getting a FPS reading from glxgears at about 1200.

Then, I had to reinstall and I again let Ubuntu hardware manager install my ATI driver, after a lot of problems (for unknown reasons) and my FPS was down to about 600.

Now, I installed the ATI proprietary driver and my FPS is even lower! I don't know what I'm doing wrong, but it seems like my card is running like crap!
```

daren@v0rtex:~$ glxgears
2146 frames in 5.0 seconds = 429.092 FPS
2252 frames in 5.0 seconds = 450.344 FPS
2249 frames in 5.0 seconds = 449.730 FPS
```

Maybe someone has some suggestions and some modifications that I can do to help my card perform better? Here's a copy of my X11 config..
```

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
        InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
EndSection

Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizEdgeScroll" "0"
EndSection

Section "Monitor"
        Identifier   "Configured Monitor"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "Configured Video Device"
        Option      "UseFBDev" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:1:5:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Configured Video Device"
        Monitor    "Configured Monitor"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection
```

Thanks, I appreciate any help as I am learning..

---

