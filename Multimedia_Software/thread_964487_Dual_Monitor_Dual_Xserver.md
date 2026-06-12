---
title: "Dual Monitor Dual Xserver?"
date: 2008-10-30
forum: Multimedia Software
---

### Post by FlashOmega on 2008-10-30
Alrighty, new Ubuntu 8.10... fun fun

So I have a strange question... well I think its strange... tell me if im crazy here

I have 2 monitors on an nvidia 8800gtx vid card
I already installed the nvidia drivers right from nvidia manually (works fine, glxinfo | grep direct says yes.

I have 2 different resolutions for my monitors, 1680x1050 and 1920x1080

I want to run 2 seperate xservers mainly because I dont like my background stretching and I want to be able to toss a video up on my big screen and still switch through multiple desktops on my other while I program and what not.

I had this running however with some minor issues.

1. things like my bluetooth icon and my network icon didnt know which one to go on so they opened their own windows instead of attaching to a bar

2. my bigger res screen showed the toolbar and background in the size of the other screen with black edges .. however I could move my mouse onto those edges.

I am not overly concerned with using compiz-fusion on both screens but that would be cool, perhaps a talk for after the first part is working

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "true"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
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

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer AL2016W"
    HorizSync       31.0 - 84.0
    VertRefresh     56.0 - 77.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "JKC JTF1905UE"
    HorizSync       14.0 - 91.0
    VertRefresh     22.0 - 80.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTX"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTX"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
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
    Option         "metamodes" "DFP-0: 1920x1080 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

So right now I have it as an extension. so my background is stretched, however here is my xorg.conf for it, to make it the other way with the glitchy sizes and icon windows I simply change xinerama to false and that gets me to that phase.

As you might see I used nvidia-settings to setup the original xorg.conf and then starting changing from there... so if something doesnt make sense let me know and I will cut it and write it your way.

Thanks for any help.

---

### Post by FlashOmega on 2008-11-02
BUMP??

am I way off......... is this not currently possible?

---

### Post by MunkyJunky on 2008-11-02
I have this going on Ubuntu 8.04, on an Nvidia 6600 LE. It's pretty easy to get going, just install Nvidia X server settings (through synaptic), then just press alt+f2 and run "gksudo nvidia-settings". You have to run the program as root, or it just gets frustrating when it won't save :D

I imagine it'll be the same on 8.10, but I'm not running it myself.

---

### Post by Macdelaney on 2008-11-10
Exactly what configuration are you using?  Could you post the details? I'm trying to get the same as FlashOmega but cant really figure out how

---

### Post by FlashOmega on 2009-01-08
I switched back to 8.04 and the nvidia config tool did all the work for me, no issues at all.  If you like I can post my xorg file from 8.04 when I get home.

---

