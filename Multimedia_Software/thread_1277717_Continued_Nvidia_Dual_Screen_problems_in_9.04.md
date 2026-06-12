---
title: "Continued Nvidia Dual Screen problems in 9.04"
date: 2009-09-28
forum: Multimedia Software
---

### Post by Audax Dreik on 2009-09-28
Alright, I've done quite a bit of research on this topic, but it's possible that I may have missed some obvious solution already posted, if so, please be kind and point me in the right direction. I have found several "solutions" on my own already, but none that have worked precisely for me.

I have an Nvidia Geforce 420 Go on an old Toshiba Satellite (not sure of the exact model) with the 96.43.10 drivers. I am trying to get dual screens going and am very close to success with the one problem that my mouse continuously gets stuck on the second screen and cannot be moved back to the first, let me give you the details.

Twinview does not seem to be an option, when I try it I get a whole host of problems, primarily that most windows are a flat white, including my terminal. The desktop background does not display, nor do any of the icons on it apparently. I can still interact with everything, albeit blindly. In this mode however, the mouse behaves properly and I can move it freely between screens. I don't know how to begin tackling this problem but if anyone has any ideas I will post a pertinent xorg.conf and maybe you can help me on that front.

I would much rather however have the laptop monitor and the TV screen as separate X screens. As I stated before, I've managed to watch several movies on the TV in this way perfectly, but cannot move the mouse back to the primary laptop screen which eventually makes things unmanageable. Here is my xorg.conf file under the current settings that cause this:

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
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
    ModelName      "Nvidia Default Flat Panel"
    HorizSync       29.0 - 49.0
    VertRefresh     0.0 - 61.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 33.0
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
    BoardName      "GeForce4 420 Go"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce4 420 Go"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "UseDisplayDevice" "DFP"
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"

# Removed Option "metamodes" "DFP: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1024x768 +0+0"
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
    Option         "metamodes" "TV: 1024x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

Now, I'm far from an expert, but everything here looks more or less alright to me. You'll notice under the ServerLayout that I have Screen1 RighOf Screen0. However, whenever I open the Nvidia Settings panel it always has Screen1 placed at an Absolute +1024 +0, no matter how many times I change this in the panel and save the new xorg.conf, it always displays that way under the panel the next time I start it up. As well, it recognizes the TV, but I don't seem to have options to configure Screen1 under the settings panel, only ever Screen0.

So I hope that was descriptive enough, if it wasn't just let me know what else you need to know and I'll be sure to reply with the information. For the time being, I suppose I will just run the TV as the single screen, but again, this really isn't ideal. I've worked on this laptop as a media center very hard for the past few days and it's rather upsetting to get this close and get hung up on such a silly little problem (I mean seriously, the mouse getting stuck on the second screen? Is that some kinda joke?) that it's a little upsetting, you know?

Thanks in advance for any and all help you can give me!

---

