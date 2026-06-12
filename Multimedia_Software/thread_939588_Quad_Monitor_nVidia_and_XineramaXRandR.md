---
title: "Quad Monitor nVidia and Xinerama/XRandR"
date: 2008-10-06
forum: Multimedia Software
---

### Post by Whitespace on 2008-10-06
First off, I'm running 8.04 LTS.  I have a quad monitor setup with two Quadro 570s.  I have two monitors on each, in Twinview, using the nVidia drivers.  All the monitors are the same.

The setup is a square, with each card taking up each horizontal row of monitors.  So the top two monitors go to one card, and the bottom two go to another card.

I have xinerama enabled for two reasons:
[LIST]
[*]they're stacked in a square fashion, and I don't think I can do that without xinerama
[*]to move each monitor away from each other to compensate for the bevels (I actually want dead space)
[/LIST]

Everything works fine if I separate each monitor on the card horizontally, but if I separate the two X screens, I can't move the mouse to each one.  Horizontally, I can move the mouse into the dead space behind the bevel, but if I enable dead space vertically, I'm unable to go up to the top two monitors.

After a LOT of trial and error, I've determined that this is the cause of it.

Any thoughts?  Also, I made the lower left display the primary on it's X screen, but modal dialog boxes still pop up in between the two bottom screens (like the login screen).  Can I make just one monitor be the primary?

Also, the whole reason why I'm doing this is to create a "monitor wall" of sorts with 4xHDTVs later on in the week, so this is a test for fullscreen video with bevel removal via xinerama.  I can maximize a VLC window to fit all four monitors (if I had no vertical dead space, of course), and the video plays fine in VLC, but fullscreen is only for one X screen?

Perhaps the Video Wall filter would be best, but does it allow me to "remove" video that the bevel "covers"?

---

### Post by renzi on 2008-12-17
would you mind posting your xorg.conf?  I too am working towards a quad monitor setup 1 x 4 though (not a square 2x2).

I have 2 cards with dual output each, yet I can only get one card recognized at a time?!?!

and... I thought Xinerama & XRandR could not run together - how did you pull that off?

---

### Post by stig51 on 2008-12-18
Hello,

I'm working on a similar project than Whitespace. I would like to create a desktop over 4 monitors using 2 GPUs (1x4). Using the package nvidia-settings I'm only able to perform 2x2.

I'm using an 780i chipset and 2x 9800GTX+ with nvidia-glx-new installed.




Following my xorg.conf file :

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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
    ModelName      "Iiyama PLE2208HDS"
    HorizSync       30.0 - 84.0
    VertRefresh     55.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Iiyama PLE2208HDS"
    HorizSync       30.0 - 84.0
    VertRefresh     55.0 - 76.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Unknown"
    BusID          "PCI:4:0:0"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Unknown"
    BusID          "PCI:3:0:0"
EndSection

Section "Screen"

    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: 1280x768 +0+0, CRT-1: 1280x768 +1280+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"

    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "TwinView" "1"
    Option         "metamodes" "CRT-0: 1280x768 +0+0, CRT-1: 1280x768 +1280+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by stig51 on 2008-12-23
Check here [http://ubuntuforums.org/showthread.php?t=884161]("http://ubuntuforums.org/showthread.php?t=884161")

---

