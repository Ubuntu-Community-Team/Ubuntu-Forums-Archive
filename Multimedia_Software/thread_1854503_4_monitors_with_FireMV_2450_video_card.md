---
title: "4 monitors with FireMV 2450 video card"
date: 2011-10-04
forum: Multimedia Software
---

### Post by wgg1970 on 2011-10-04
Does anyone have a working xorg.conf that they can share for getting 4 1920x1080 monitors working? Preferably for single large desktop.

Question: Do you need to have all monitors plugged in and powered on before you run:

# aticonfig --initial --heads=4

Hints and any expert advice welcome!

Here is my current xorg.conf

Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
        Screen         "amdcccle-Screen[3]-1" RightOf "aticonfig-Screen[0]-0"
EndSection

Section "Module"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "0-DFP1"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1920x1080"
        Option      "TargetRefresh" "60"
        Option      "Position" "0 0"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
EndSection

Section "Monitor"
        Identifier   "0-DFP2"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1920x1080"
        Option      "TargetRefresh" "60"
        Option      "Position" "0 0"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        Option      "Monitor-DFP2" "0-DFP2"
        BusID       "PCI:3:0:0"
EndSection

Section "Device"
        Identifier  "amdcccle-Device[3]-1"
        Driver      "fglrx"
        Option      "Monitor-DFP1" "0-DFP1"
        BusID       "PCI:3:0:0"
        Screen      1
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Screen"
        Identifier "amdcccle-Screen[3]-1"
        Device     "amdcccle-Device[3]-1"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

---

