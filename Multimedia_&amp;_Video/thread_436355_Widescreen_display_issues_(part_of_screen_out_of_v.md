---
title: "Widescreen display issues (part of screen out of view)"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by mattstang on 2007-05-07
I'm having a very strange issue.

I have an ATI Xpress 200G with a Samsung SyncMaster 940BW (1440x900).  The widescreen IS in fact working, but part of my desktop is "out of viewing range".  So the screen has an Auto position feature, but does not resolve it.  The screen does NOT have a V-size and H-size, only V-position and H-position.

My monitor config in xorg.conf is:

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "SAM"
        ModelName    "SyncMaster"
        HorizSync       30.0 - 82.0
        VertRefresh     50.0 - 85.0
        Option          "DPMS"
        Modeline        "1440x900_70.00" 126.98 1440 1536 1688 1936 900 901 904 937 -HSync +Vsync
        Modeline        "1440x900_60.00" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
        DisplaySize     1440 900
 ### Comment all HorizSync and VertRefresh values to use DDC:
#       HorizSync    30.0 - 81.0
#       VertRefresh  56.0 - 75.0
EndSection

My video adapter config is:

Section "Device"
        Identifier  "Card0"
        Driver      "ati"
        VendorName  "ATI Technologies Inc"
        BoardName   "RS480 [Radeon Xpress 200G Series]"
        BusID       "PCI:1:5:0"
EndSection

and screen config is:

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        SubSection "Display"
                Depth     24
                Modes   "1440x900"
        EndSubSection
EndSection

This issue is by no means devastating, but very annoying

Any advise would be much appreciated

-mattstang

---

### Post by kkm1978 on 2008-05-01
I have the same issue. If some one has solution please post.

---

