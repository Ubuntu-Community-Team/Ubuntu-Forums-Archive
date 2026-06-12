---
title: "TwinView: clone picture to screen and projector at the same time"
date: 2007-06-17
forum: Multimedia &amp; Video
---

### Post by EmuMannen on 2007-06-17
I’m so frustrated! I just bought some new hardware for a HTPC (replacing my VCR, STB, DVD etc.). I built it around an abit NF-M2 nView because it’s onboard GeForce 6150 and because it was well supported under Linux.

I started however under Windows XP running the Open Source media center “Mediaportal”. It worked pretty well and I was especially impressed by how easy and seamless the new nVidia ForceWare drivers under XP supported image cloning between two screens. In my case those are a Samsung Syncmaster 172W (1280x768 ) LCD screen via VGA (CRT-0) and an Epson EMP-TW100 (1280x720) projector via DVI (DFP-0).

Under Windows there are no problems setting the screen resolution to 1280x720 and clone the image from the screen to the projector. It doesn’t matter if the screen or projector is powered on before or while the HTPC is powered on, I always got the same picture on the screen and the projector (extremely convenient eliminating the need for a video switch between the screen and projector).

My initial test with Mediaportal was promising but I really wanted to get rid of Windows XP running as much Open Source as possible. I therefore installed Ubuntu 7.04 and I planned to continue with MPlayer, Tvtime and Freevo (or maybe fallback on MythTv). My first task would be to setup X the same way Windows was configured, 1280x720 cloned between CRT-0 and DFP-0 on the onboard GeForce 6150.

I have spent at least ten hours reading and experimenting without any success! The picture shows up on both devices during POST and Ubuntu bootup but it seems impossible to get 1280x720 on both devices under X!

I have read over 200 different forum postings and related web pages about the binary nVidia drivers and TwinView and I have tried almost as many different configurations in xorg.conf but I haven’t found anything that works the same way as under Windows. I would have guessed that the screen was unable to do 1280x720 or that the projector was unable to do 1280x720 via DVI if I hadn’t seen it working under Windows XP before I tried Ubuntu. But it just makes me even more frustrated when it works so easily under Windows and I can’t seem to get even close under Ubuntu. Why has such a simple task have to be near impossible when using Linux, I’m even using the nVidia binary drivers for good sake!

It feels so frustrating being forced back to a Windows solution because of such a simple problem as not being able to get a 1280x720 picture on both the screen and projector at the same time but it is a requirement in my living room. Does anyone have a solution to my problem or do I really have to roll back to XP? Below is a copy of my current xorg.conf:

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
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
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Generic"
    HorizSync       30.0 - 61.0
    VertRefresh     56.0 - 75.0
    ModeLine       "1280x720_75" 98.49 1280 1336 1616 1728 720 722 734 760 #75Hz
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6150"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "UseEDID" "False"
    Option         "HorizSync" "CRT-0: 30-61; DFP-0: 24-91"
    Option         "VertRefresh" "CRT-0: 56-75; DFP-0: 56-85"
    Option         "TwinView" "True"
    Option         "TwinViewOrientation" "Clone"
    Option         "MetaModes" "1280x720_75, 1280x720_75"
    Option         "ConnectedMonitor" "DFP-0, CRT-0"
    SubSection     "Display"
        Depth       24
        Modes      "1280x720_75"
    EndSubSection
EndSection

```

---

### Post by steveneddy on 2007-06-17
```
gksudo nvidia-settings
```

On the menu on the left, go to X Server Display Configuration

This is a GUI way of doing what you need with out having to mess around with the xorg.conf file.

And you can save your settings for later if you wish.

---

### Post by EmuMannen on 2007-06-17
> **steveneddy said:**
> ```
gksudo nvidia-settings
```

On the menu on the left, go to X Server Display Configuration

This is a GUI way of doing what you need with out having to mess around with the xorg.conf file.

And you can save your settings for later if you wish.
That&#8217;s the first thing I tried but it seems to be impossible to do what I want to do using &#8220;nvidia-settings&#8221; because the two &#8220;screens&#8221; showing up in the GUI (the Samsung screen and the Epson projector) doesn&#8217;t allow me to set any of them to 1280x720. The screen allows 1280x768 (its native resolution) but 1280x720 doesn&#8217;t even show up as an alternative for the projector! It is possible to force the screen to use 1280x720 using a modeline but I then lack a picture on the projector (even if the modeline falls well within what&#8217;s supported by the projector, and I know that the projector can do 1280x720 through DVI because I already done it under XP and with a modeline from a Unix based Momitsu V880 DVD-player using a custom modeline). :(

---

### Post by steveneddy on 2007-06-17
Why don't you add the resolution you need to the xorg.conf file?

Then run nvidia-settings again?

---

### Post by EmuMannen on 2007-06-18
> **steveneddy said:**
> Why don't you add the resolution you need to the xorg.conf file?

Then run nvidia-settings again?
Made no difference, I have tried 1280x720, 1280x720_60 etc. but none (1280x720) is showing up as available resolution for the screen or projector if I try to use "nvidia-settings". 

This is so typical; every time I try to use Linux for anything except as a server, some little detail is ruining the experience! I spent another 4 hours today trying to solve the problem without success. I guess that there is some combination of switches and settings that would make it work but who cares if it is near impossible to figure it out?!? 

I have RTFM, the nVidia binary drivers README, and every forum and webpage I have found discussing this problem. I have tried every combination of suggested solutions but without success. I am not alone, that&#8217;s for sure and I guess that I won't be the only one forced back to Windows XP because they cant figure things out...

I really hate this, I want to run Linux and especially Ubuntu but it is details like this that&#8217;s keeping me from it... Linux might be free but time is money... :(

---

### Post by raffytaffy on 2007-06-18
try this
 sudo nvidia-xconfig --twinview

---

### Post by EmuMannen on 2007-06-19
Problem solved, the "magic" setting was "ExactModeTimingsDVI" "True", the following settings in xorg.conf made it work exactly the way I wanted it (any modeline is read now by X, I would run 50Hz, since I am in PAL-land, if only my screen synced to it, the projector does):
```

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Generic"
    HorizSync       30.0 - 61.0
    VertRefresh     56.0 - 75.0
    Modeline        "1280x720" 74.25 1280 1320 1376 1650 720 722 728 750 #ATSC-720-60p
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6150"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "HorizSync" "CRT-0: 30-61; DFP-0: 24-91"
    Option         "VertRefresh" "CRT-0: 56-75; DFP-0: 56-85"
    Option         "NoLogo" "True"
    Option         "TwinView" "True"
    Option         "TwinViewOrientation" "Clone"
    Option         "NoTwinViewXineramaInfo" "True"
    Option         "MetaModes" "1280x720, 1280x720"
    Option         "ConnectedMonitor" "DFP-0, CRT-0"
    Option         "ExactModeTimingsDVI" "True"
    Option         "DPI" "75 x 75"
    Option         "UseEDID" "False"
    Option         "ModeValidation" "AllowNon60HzDFPModes, NoEdidModes, NoEdidDFPMaxSizeCheck, NoVertRefreshCheck, NoHorizSyncCheck, NoMaxSizeCheck, NoDFPNativeResolutionCheck, NoEdidMaxPClkCheck"
    SubSection     "Display"
        Depth       24
        Modes      "1280x720"
    EndSubSection
EndSection

```

---

