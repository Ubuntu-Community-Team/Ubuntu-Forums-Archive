---
title: "Driver &amp; Display issues/questions"
date: 2009-11-04
forum: Multimedia Software
---

### Post by DMisigoy on 2009-11-04
First, should I be able to enable desktop visual effects using the nv driver? I have a GeForce 7900 GTX connected to an Acer H233H monitor via DVI cable. When I try to use the nvidia driver all I get is a blank black screen when I should see the login screen. I've attached two versions of my xorg.conf that had this same result. I am using 9.10 now, but tried a variety of methods and solutions for installing the driver in 9.04 and a few here, none of them being successful, but varying in their degrees on ineffectivity. Any and all help is appreciated.

---

### Post by DMisigoy on 2009-11-05
Let me make this easier

> Section "Monitor"
    Identifier "ACER H233H"
    Option "DPMS"
    HorizSync 54.2 - 83.8
    VertRefresh 49 - 75
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"

    Monitor "ACER H233H"
    DefaultDepth 24
    SubSection "Display"
        Modes "1920x1200" "1920x1080" "1680x1050" "1600x900" "1440x900" "1365x768" "1280x720" "852x480"
    EndSubSection
EndSection

Section "Module"
    Load    "glx"
    Disable    "dri2"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
EndSection
&
> Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
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
    Identifier     "ACER H233H"
    HorizSync       54.2 - 83.8
    VertRefresh     49.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 7 Series"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "ACER H233H"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200" "1920x1080" "1680x1050" "1600x900" "1440x900" "1365x768" "1280x720" "852x480"
    EndSubSection
EndSection

---

