---
title: "[SOLVED] Samsung HDTV no sound w/ nvidia driver"
date: 2009-06-08
forum: Multimedia Software
---

### Post by aun on 2009-06-08
I'm entering this post to hopefully save other people some reasonably painful debugging.  

Problem:
Using HDTV as a monitor (in my case Samsung Model# LN40B530) via DVI video with analog audio, sound works with VESA driver.  No sound is obtained using using Nvidia proprietary driver (177 confirmed).  This is a known issue (see [http://forums.nvidia.com/index.php?showtopic=46914&st=20&p=336974&#entry336974](http://forums.nvidia.com/index.php?showtopic=46914&st=20&p=336974&#entry336974)) caused by the nvidia driver's interaction with the TV. 

Background:
In the currrent generation of display hardware the video driver is supplied information from the display via EDID ([http://en.wikipedia.org/wiki/EDID](http://en.wikipedia.org/wiki/EDID)). HDMI connections carry audio.  DVI connections normally do not, but can, since they have additional available data pins.  Evidently, the nvidia driver is telling the TV that an audio signal is being sent over DVI, but unless the video card supports it, no such signal is actually being sent.  On some TVs a configuration option is available to manually specify the corrrect audio source, but on others (such as the Samsung specified) no such option is present.

Solution:
Modify xorg.conf to manually specify resolution parameters and prohibit the driver from using EDID.  (For the uninitiated xorg.conf is your video configuration file - full explanation is beyond the scope of this post.  Proceed carefully.)

Here is a working xorg.conf for the Samsung LN40B530:

```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    Option         "ExactModeTimingsDVI" 
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "SAMSUNG"
    ModelName      "LN40B530"
    DisplaySize    160 90
    HorizSync      26.0 - 81.0
    VertRefresh    24.0 - 75.0
    ModeLine "1920x1080p60" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +HSync +VSync
    ModeLine "1360x768p60" 85.50 1360 1424 1536 1792 768 771 777 795 +HSync +VSync
    ModeLine "1280x720p60" 74.25 1280 1390 1430 1650 720 725 730 750 +HSync +VSync
    ModeLine "720x480p60" 27.00 720 736 798 858 480 489 495 525 -HSync -VSync
    #DisplaySize    190 107	#1920x1080@256dpi
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "UseEdid" "FALSE"
    Option         "ModeValidation" "NoXServerModes, NoVesaModes, NoMaxPClkCheck, NoEdidMaxPClkCheck, NoMaxSizeCheck, NoHorizSyncCheck, NoVertRefreshCheck, NoWidthAlignmentCheck,  NoDFPNativeResolutionCheck, NoEdidDFPMaxSizeCheck"
    SubSection     "Display"
        Depth       24
          Modes "1920x1080p60" "1360x768p60" "1280x720p60" "720x480p60"
    EndSubSection
EndSection

```

The UseEdid and ModeValidation options in the Screen section prevent the video driver from using EDID to automatically communticate with the TV (some of these may be overkill for the problem at hand - if you can eliminate any, have at it), so you will need to specify "ModeLines" and "Modes" for your display.  If you do not have the specific model above, see [http://www.mythtv.org/wiki/Modeline_Database](http://www.mythtv.org/wiki/Modeline_Database) for modelines for your model or instructions on how to generate your own.

PS: As a separate issue, if you are using a TV to view from across the room, fonts will be almost invisible.  You may want to set the "DisplaySize" accordingly.  For a 40 inch screen at 9-10 feet, the equivalent of 256 dpi seems about right.  Uncommenting that line might help.  You will also want to set the DPI options in Gnome (System/Preferences/Appearance/Fonts/Details).  Don't expect desktop effects to play nicely with all of this.  I had system freezes unless I turned off desktop effects.

Since I am not very active on the forum, I will probably be mostly unreliable for replies to questions.   If a moderator feels this will be more helpful elsewhere, feel free to move it.

---

### Post by ant_thomas on 2010-01-04
I realise this reply is quite a bit later but I'd just like to say thank you for posting your solution. I've been searching for the last few hours for ways to cure the problem with my 37" Samsung TV and this is the only thing that has actually been both sensible and worked.

Seems you posted it on my birthday too, I'll assume it was a birthday present I forgot to open :D

---

