---
title: "Switching GPU, Panel+Enable SLI on 9800M"
date: 2010-02-06
forum: Multimedia Software
---

### Post by Martins2040 on 2010-02-06
Hey there, ive been browsing a bit to try get anywhere with this.

Running Ubuntu 9.10 32bit

I got 3 gfx cards in my laptop, Qosmio x300
1x9400M (default bootup card IDBus 04:00.0)
2x9800M GTS (for hybrid SLI...just sitting there on ID 2 and 3)

So can i somehow switch from GPU 0 to GPU 1 using only 1 9800M card?
xorg.conf makes an error during startup, if just forcing ID from 4 to 2 or 3.

OR even just somehow enable those two 9800M cards to run SLI even tho im booting up on the slower 9400M?

I get this when running lspci:

02:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9800M GTS] (rev a1)
03:00.0 3D controller: nVidia Corporation G94 [GeForce 9800M GTS] (rev a1)
04:00.0 VGA compatible controller: nVidia Corporation C79 [GeForce 9400M G] (rev b1)


Showing it can detect the cards. I know im not the only in here with serveral cards build into newer systems:)
 
My xorg.conf shows this:

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
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
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BusID          "PCI:4:0:0"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "SLI" "on"
    Option         "MultiGPU" "On"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by Martins2040 on 2010-02-07
bump

---

