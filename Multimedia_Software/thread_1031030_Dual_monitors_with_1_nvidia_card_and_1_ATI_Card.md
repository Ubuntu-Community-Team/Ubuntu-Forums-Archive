---
title: "Dual monitors with 1 nvidia card and 1 ATI Card"
date: 2009-01-04
forum: Multimedia Software
---

### Post by jbz104 on 2009-01-04
Forgive me if this has already been asked/answered (and please point me in the right direction)

Is it possible to run dual monitors across two separate graphics cards from different vendors? I have the proprietary drivers running my nVidia card smoothly, but I was hoping to get something out of my ATI card as well (which is currently just displaying a black screen).

the cards are (as listed by lspci): ATI 3D Rage II+ 215GTB [Mach64 GTB]
and an nvidia GeForce4 MX 440 AGP 8x

I've been tinkering around with my xorg.conf file a bit, and was hoping that I could just add extra monitor/device/screen sections specific to ATI to get it working, but thus far I haven't been very successful.

below is the working xorg.conf file for my nvidia driver, followed by the dev one I've been trying to configure to include the ATI card.

```

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
    BusId          "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "UseFBDev" "true"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

```

and here is the dev xorg.conf I'm hoping to get working with ATI

```

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
    Identifier     "Monitor 1"
EndSection

Section "Monitor"
   Identifier      "Monitor 2"
EndSection

Section "Device"
    Identifier     "Nvidia Video Device"
    Driver         "nvidia"
    BusId          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "ATI Video Device"
    Driver         "ati"
    BusId          "PCI:0:f:0"
EndSection

Section "Screen"
    Identifier     "Screen 1"
    Device         "Nvidia Video Device"
    Monitor        "Monitor 1"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "UseFBDev" "true"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen 2"
    Device         "ATI Video Device"
    Monitor        "Monitor 2"
    DefaultDepth   24
EndSection


```

is this even possible? Thanks!

Justin

---

