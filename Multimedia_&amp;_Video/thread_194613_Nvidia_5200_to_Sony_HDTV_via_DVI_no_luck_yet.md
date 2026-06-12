---
title: "Nvidia 5200 to Sony HDTV via DVI: no luck yet"
date: 2006-06-11
forum: Multimedia &amp; Video
---

### Post by dara on 2006-06-11
I'm closer to getting most of my current hardware to work with Ubuntu 6.06 than other Linux options I've tried (Fedora, KnoppMyth, Suse).  I have a wireless USB networking device (mostly) working (see post: Ubuntu 6.06 - Dapper rt2500 driver kind of works...), SPDIF on my sound card works (post: [multimedia] Ubuntu 6.06 - HOWTO: Chaintech AV710 SPDIF).  

But I'm not having as easy a time with getting my video card (Chaintech FX 5200) to drive my TV (Sony KDF-42WE655) via its DVI output (using a DVI to HDMI connector at the TV).

Ideally I'd like to get Twinview (in clone mode) working so I don't have to turn on my power hungry TV just go queue up a few music files.  But I'd be happy just to get the TV to work.  But if anybody happens to know answers to my questions on Twinview, that would be great:

1] I've read it is often not possible to use VGA and DVI ports at the same time if you are using the DVI in its analog mode.  Is it usually possible to use both when the DVI port is connected to a TV (HDMI) port?

2] My CRT can run at 1280x1024, but only at 60 Hz and the flicker is terrible.  Do I have to run the CRT and TV at the same resolution and frequency?  (Example xorg.conf files I've seen up to now are the same).

3] If I'm running the system without the TV on and then turn the TV on, is there a way to activate the DVI connection without restarting the computer?

As far as getting the TV to work by itself, my strategy was to first see if the TV could be auto detected, so I unplugged my monitor, plugged in the TV (powered and selected the HDMI input), then booted with the CD in the drive.  I never saw anything and when I plugged in the CRT (I got the screen "Failed to start the X server").  Then I reviewed Modelines from avsforum.com, read a few Ubuntu HOWTOs, put together the first xorg.conf given below.  This time I get some jittery purple lines on the screen but nothing resolvable.  I do have the nvidia driver working using the CRT alone (second xorg.conf).  Finally, I include the xorg.conf from my try at twinview.  

I could try deleting modeline options to move to the next, but the iterative process is kind of slow (I should probably figure out how to remote login from a Windows laptop to change the xorg.conf files between retries).

I'm happy to move this to a different thread if advised.  I'd be happy to move this if advised.  Thanks for any pointers anybody has.

Dara Parsavand

HDTV xorg.conf (keyboard, mouse, font sections deleted)

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "Monitor"
    Identifier "SonyTV"
    VendorName "Sony"
    ModelName "KDF-42WE655"
    Option "UseEDID" "FALSE"
    DisplaySize 320 180
    HorizSync 30.0 - 90.0
    #VertRefresh 20.0 - 150.0
    VertRefresh 20.0 - 60.0

# Why do lines vary on character before *sync?
Modeline "1200x688" 73.765 1200 1336 1416 1648 688 703 708 746 +hsync +vsync
ModeLine "1280x720" 75.600 1280 1360 1400 1648 720 738 757 787 +hsync +vsync
ModeLine "1304x734" 74.250 1304 1336 1376 1648 734 745 750 773 +hsync +vsync
ModeLine "1312x744" 79.096 1312 1376 1512 1728 744 745 748 774 +hsync +vsync
ModeLine "1320x744" 78.140 1320 1384 1520 1720 734 758 763 784 +hsync +vsync
ModeLine "1328x744" 74.732 1328 1432 1568 1648 744 745 748 756 +hsync +vsync
Modeline "1336x746" 75.964 1336 1396 1420 1648 746 749 750 769 -hsync -vsync 
ModeLine "1344x728" 74.160 1344 1424 1464 1648 728 729 734 750 -hsync -vsync 
ModeLine "1344x734" 78.923 1344 1512 1560 1720 734 758 763 784 +hsync +vsync
Modeline "1376x744" 79.031 1376 1376 1424 1736 744 752 757 771 +hsync -vsync 
ModeLine "1376x768" 86.946 1376 1440 1576 1912 768 777 780 780 +hsync +vsync
ModeLine "1384x768" 84.203 1384 1512 1656 1872 768 768 771 771 +hsync +vsync
ModeLine "1384x784" 85.421 1384 1456 1600 1816 784 785 788 811 +hsync +vsync

Section "Device"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
    VendorName     "Chaintech"
    BoardName      "NVIDIA GeForce FX (generic)"
    Option "RenderAccel" "true"
    Option "AllowGLXWithComposite" "true"
    Option "ConnectedMonitor" "DFP"
    Option "NoLogo" "1"
    Option "RenderAccel" "true"
    Option "AllowGLXWithComposite" "true"
EndSection

Section "Screen"
    Identifier "TV"
    Device "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor "SonyTV"
    DefaultDepth 24
    SubSection "Display"
        Viewport 0 0
        Depth 24
        Modes "1384x784" "1384x768" "1376x768" "1376x744" "1344x734" "1344x728" "1336x746" "1328x744" "1320x744" "1312x744" "1304x734" "1280x720" "1200x688"
    EndSubSection
EndSection

# Don't know if I need this yet
#Section "DRI"
#    Group 0
#    Mode 0666
#EndSection

```

Working xorg.conf for a small CRT
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "Monitor"
    Identifier     "DELL E771p"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "DELL E771p"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768"
    EndSubSection
EndSection

```

Try at twinview xorg.conf

```

Section "ServerLayout"
    Identifier "TwinView Configuration"
    Screen 0 "Default Screen" 0 0
    InputDevice "Configured Mouse"
    InputDevice "Generic Keyboard"
    Option "Xinerama" "Off"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "Monitor"
    Identifier     "DELL E771p"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
    VendorName "Videocard vendor"
    BoardName "NVIDIA GeForce 5200"
    BusID "PCI:1:5:0"
    Option "NvAGP" "2"
    Option "NoLogo" "0"
    Option "RenderAccel" "0"
    Option "CursorShadow" "1"
    Option "Coolbits" "1"
    Option "ConnectedMonitor" "crt, dfp"
    Option "NoPowerConnectorCheck"
    Option "TwinView" "1"
    Option "Metamodes" "1024x768,1280x768; 1280x768,1280x768; 1024x768,1024x768; 1024x768,NULL"
    Option "SecondMonitorHorizSync" "30-50"
    Option "SecondMonitorVertRefresh" "60"
    # Option "NoTwinViewXineramaInfo"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "DELL E771p"
    DefaultDepth    24
    SubSection     "Display"
    Viewport 0 0
    Depth       24
# NOT SURE ABOUT LINE BELOW
    Modes      "1280x768" "1024x768"
    EndSubSection
EndSection

```

---

### Post by xaphod on 2006-08-05
I have the exact same TV, the exact same video card, and the exact same problem :) I'm also using Dapper Drake. I'm using DVI out from the chaintech into HDMI input of the TV.

I've had some luck with one modeline although there's some overscan happening even with the tv's overscan set to -1.

Below are portions of my xorg.conf, hope this helps. If you find a modeline that works with the tv without overscan let me know!

Btw, don't try and get twinview working yet...

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        #Load   "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "Device"
        Identifier      "nvidia fx 5200"
        Driver          "nvidia"
        BusID           "PCI:3:0:0"
        Option          "RenderAccel"   "On"
        Option          "IgnoreDisplayDevices"  "DFP,TV"
        Option          "NoRenderExtension"     "on"
        Option          "Accel" "on"
        Option          "AllowGLXWithComposite" "off"
        Option          "XvmcUsesTextures" "false"
EndSection

Section "Monitor"
        Identifier      "SonyTV"
        Option          "ConnectedMonitor"      "DFP"
        Option          "IgnoreEDID"

        VendorName      "Sony"
        ModelName       "KDF-42WE655"
        HorizSync       30-50
        VertRefresh     59-61
        DisplaySize     320     180
        ModeLine        "ATSC-720p60Hz" 73.765 1200 1336 1416 
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nvidia fx 5200"
        Monitor         "SonyTV"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "ATSC-720p60Hz"
        EndSubSection
EndSection

---

