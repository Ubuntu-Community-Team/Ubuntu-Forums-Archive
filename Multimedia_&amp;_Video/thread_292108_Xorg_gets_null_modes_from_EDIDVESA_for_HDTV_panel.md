---
title: "Xorg gets null modes from EDID/VESA for HDTV panel"
date: 2006-11-03
forum: Multimedia &amp; Video
---

### Post by Sixer on 2006-11-03
Hi,

I'm having a problem getting a 720p (1280x720) or a 1080i (1920x540) resolution working on my HDTV that is connected to my machine running Ubuntu Edgy with Xorg.

The machine has an Intel i945GM graphics chipset. The JVC LCD HTDV panel is connected to the machine using a DVI <---> HDMI cable. I know the DVI-->HDMI connection is good because upon boot, before Ubuntu kicks in, my TV screen briefly goes white and reports a valid 720p signal. Also, under OS X, I can use the resolutions fine if I use a shareware app to install the custom resolutions and refresh rates.

I'm using the i810 driver that comes standard with Ubuntu 6.10. I've configured xorg.conf with mode lines according to my TV's specifications and added the modes 1920x540, 1920x1080 and 1280x720:

```
Section "Device"
        Identifier      "Intel i945GM"
        Driver          "i810"
        BusID           "PCI:0:2:0"
##      Option          "LinearAlloc" "16144"
        VideoRam        65536
        Option          "DisplayInfo" "FALSE"
        Option          "ForceBIOS" "1920x1440=1280x720"
        Option          "ForceBIOS" "1920x540=1280x720"
        Option          "ForceBIOS" "1280x1024=1280x720"
        Option          "ForceBIOS" "1280x800=1280x720"
        Option          "ForceBIOS" "1024x768=1280x720"
EndSection
        
Section "Monitor"
        Identifier      "JVC LT-26S60"
        Option          "DPMS"
        HorizSync       15-46
        VertRefresh     59-61
        Modeline "1280x720_60.00"  74.48  1280 1336 1472 1664  720 721 724 746  -HSync +Vsync
        Modeline "960x540_60.00"  40.78  960 992 1088 1216  540 541 544 559  -HSync +Vsync
        Modeline "1368x768_60.00"  85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync
        Modeline "1920x540_60.00"  81.57  1920 1984 2176 2432  540 541 544 559  -HSync +Vsync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel i945GM"
        Monitor         "JVC LT-26S60"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1920x540" "1920x1080" "1280x720" "1024x768"
        EndSubSection
EndSection
        

```

When I start Xorg, it knows the HDTV can do 1920x540:
```
(II) I810(0): Display Info: DFP (digital flat panel): attached: TRUE, present: TRUE, size: (1920,540)
```

However, after initiating EDID, it only retrieves VESA modes with null properties only:
```
Mode: 30 (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
        WinBAttributes: 0x0
        WinGranularity: 0
        WinSize: 0
        WinASegment: 0x0
        WinBSegment: 0x0
        WinFuncPtr: 0x0
        BytesPerScanline: 0
        XResolution: 0
        YResolution: 0
        [...]
```

Xorg then dies with the following error:
```
(EE) I810(0): No Video BIOS modes for chosen depth.
(EE) Screen(s) found, but none have a usable configuration.
```

I've given the video BIOS extra mode entries using 915resolution, it looks like Xorg/EDID/VESA get their information from somewhere else.

I have also tried to disable DDC and EDID in the xorf.conf using Option "NoDCC" "1" and Option "IgnoreEDID" "1". These options do not seem to have any effect, as the Xorg output remains the same.

How do I get Xorg/EDID/VESA to detect the right modes, or at least have it use the mode I want? I'm looking to get at least 720p working. I have a feeling that the EDID VESA mode detection is key in fixing my problem.

Any hints are greatly appreciated.

---

### Post by TheHH on 2006-11-14
I got 720p working but not in a 16x9 ratio, if try to do the right resolution for a 16x9 it overscans. No one seems to know how to fix that with the nvidia 6600gt

---

### Post by MrSpiffdifilous on 2007-11-23
I've got 720p also but have massive overscan issues. I can move the mouse about 2 inches off screen to the left, theres an inch between screens, an inch at the top and about 5 inches at the bottom... its bad. Someone should try to port nVidia's nTune app over to linux. its pretty good. fixed overscan in XP in 2 seconds.

---

