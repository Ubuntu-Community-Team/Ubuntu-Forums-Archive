---
title: "Clone displays across 2 cards (ATI Radeon)"
date: 2012-02-26
forum: Multimedia Software
---

### Post by BigDJ on 2012-02-26
The task is to clone 3 monitors on 2 graphic cards.

While I allways thought it would be difficult to get an extended desktop over 2 cards, with the ATI prop driver and Xinerama this would work almost out of the box (worked on 10.10 gnome, on 11.10 unity it was impossible to use the catalyst gui but manually editing xorg.conf based on the working 10.10 would almost do). 

10.10: On 2 displays, attached to one graphics card (ATI Radeon HD 3200), cloning works. The 3rd display (ATI Radeon E4690) will either be part of an extended Xinerama screen, or a second MultiView-screen (:0.1), but not a clone of the displays on the 3200 ...

11.10: Xinerama extended screen works with a manually edited xorg.conf. Cloning of two monitors on the same card works, but not with the specified resolution/sync-settings. As the 3rd monitor on the 2nd card would not have the cloning option as in 10.10 either, I did not bother solving the resolution problem.

The Catalyst Control Center does not show a "clone" option on the 3rd screen in either 10.10 nor 11.10.

Using the open-source radeon driver does not help, as RandR is not specified to connect 2 GPUs - at least this is what I understand.

The working Xinerama-Proprietary-xorg.conf looks as follows:

```
Section "ServerLayout"
        Identifier     "amdcccle Layout"
        Screen      0  "amdcccle-Screen[1]-0" 0 0
        Screen         "amdcccle-Screen[2]-0" RightOf "amdcccle-Screen[1]-0"
        InputDevice    "touch0"
        InputDevice    "touch1"
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "InputDevice"
        Identifier  "touch0"
        Driver      "evdev"
        Option      "Device" "/dev/input/event6"
        Option      "Calibration" "0 1920 0 1080"
EndSection

Section "InputDevice"
        Identifier  "touch1"
        Driver      "evdev"
        Option      "Device" "/dev/input/event7"
        Option      "Calibration" "0 1920 0 1080"
EndSection

Section "ServerFlags"
        Option      "Xinerama" "on"
EndSection

Section "Monitor"
        Identifier   "0-DFP1"
        Option      "VendorName" "Acer"
        Option      "ModelName" "T230H-1"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1920x1080"
        Option      "TargetRefresh" "60"
        Option      "Position" "0 0"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
EndSection

Section "Monitor"
        Identifier   "0-DFP2"
        Option      "VendorName" "Acer"
        Option      "ModelName" "T230H-2"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1920x1080"
        Option      "TargetRefresh" "60"
        Option      "Position" "1920 0"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
EndSection

Section "Monitor"
        Identifier   "1-DFP2"
        Option      "VendorName" "LG"
        Option      "ModelName" "42LG5000"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1920x1080"
        Option      "TargetRefresh" "60"
        Option      "Position" "0 0"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
EndSection

Section "Device"
        Identifier  "amdcccle-Device[1]-0"
        Driver      "fglrx"
        Option      "Monitor-DFP1" "0-DFP1"
        Option      "Monitor-DFP2" "0-DFP2"
        BusID       "PCI:1:5:0"
EndSection

Section "Device"
        Identifier  "amdcccle-Device[2]-0"
        Driver      "fglrx"
        Option      "Monitor-DFP2" "1-DFP2"
        BusID       "PCI:2:0:0"
EndSection

Section "Screen"
        Identifier "amdcccle-Screen[1]-0"
        Device     "amdcccle-Device[1]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Virtual   3840 1920
                Depth     24
        EndSubSection
EndSection

Section "Screen"
        Identifier "amdcccle-Screen[2]-0"
        Device     "amdcccle-Device[2]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

```

Any idea how to transform the Xinerama-setup into a Cloning-setup? An answer in the sense of "not possible" would not make me happy, but it would still help!

---

