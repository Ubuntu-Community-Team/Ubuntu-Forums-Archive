---
title: "NVIDIA Tv-out: Resolution/pan&amp;scan"
date: 2009-07-29
forum: Multimedia Software
---

### Post by Hisae on 2009-07-29
[B]Alrighties, being a ubuntu newbie (I installed it 2 days ago) I've managed to get everything up and running properly, to my own amazement.
Except one thing. My TV.[/B]

The TV's an Philips something-something 42" FullHD LCD, and it's connected to the PC via a component-cable jacked to a an component-svideo converter that's crammed into the gfxcard.

I managed to get a picture by sudo running the nvidia settings panel, choosing twinview, and then writing to xorg.conf and rebooting. The "apply" button was pretty much worthless.

**The problem is that the image is really tiny. It's nowhere near the size of the TV.**
The rendered area is just a tiny little square in the middle of the tv-screen.

 [B]I've got no idea how to fix this since I've only used the OS for about 2 days now.
So if anyone can help I'd be grateful.

System: Ubuntu 9.04
GFX: Nvidia 8800GT
Driver: Nvidia X Server 180.??

Here's my xorg.conf, since it'll probably be needed:[/B]


Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
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

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer P223W"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GT"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GT"
    BusID          "PCI:3:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0, TV: nvidia-auto-select +1680+0"
# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0, TV: nvidia-auto-select @1920x1080 +1680+0"
# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0, TV: nvidia-auto-select @1920x1080 +1680+0"
# Removed Option "TwinView" "0"
# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, TV: nvidia-auto-select +1680+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by rannable on 2009-07-29
Hey when you say composite cable is that HDMI or some custom made cable?
Does the TV have a vga port?

---

### Post by Hisae on 2009-07-29
I just checked it up. It's not composite, it's component apparently.
It looks like this:

[http://www.high-definition-info.co.uk/Images/Component_video_RCA.jpg](http://www.high-definition-info.co.uk/Images/Component_video_RCA.jpg)

There's no VGA port on my card.

---

