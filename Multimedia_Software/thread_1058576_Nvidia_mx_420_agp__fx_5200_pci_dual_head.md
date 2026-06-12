---
title: "Nvidia mx 420 agp / fx 5200 pci dual head"
date: 2009-02-03
forum: Multimedia Software
---

### Post by Gcottrell on 2009-02-03
Hello,

I have 2 NVIDIA cards that I would like to attempt a dual head configuration for. The first is the MX 420 AGP. I have the NVIDIA proprietary driver installed for it, and it is working properly. When I add the second card (FX 5200 PCI) the computer still starts on the MX 420, but X does not start. I get an error about No screens being found.

The driver for the MX 420 is the 96 driver, and the FX 5200 is the 173 driver. 

Ubuntu won't let me have more than one driver activated.

I'm running Ubuntu 8.10

I have no idea how to edit the xorg.conf file to meet my needs. At the moment I do not have the FX 5200 in my system due to X not starting properly.

Here is my xorg.conf
_________________________________________________________________________


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
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection


_______________________________________________________________________

Any help someone could give me to get this working would be greatly appreciated!

---

### Post by sibernet on 2009-02-14
I'm looking at doing the same thing. Let me know if you figure it out. Thanks.

---

