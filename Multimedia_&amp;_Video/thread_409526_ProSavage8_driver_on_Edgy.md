---
title: "ProSavage8 driver on Edgy"
date: 2007-04-14
forum: Multimedia &amp; Video
---

### Post by srudes2 on 2007-04-14
Hello,
From the the xorg.conf file I conclude that I probably have a ProSavage8 video card in my notebook. I'm looking for a way to make the frame rate faster when playing for example movies. I understand that this has to be the 3d acceleration where I'm looking for right? Could anyone help me finding a way to support my card with 3d acceleration under edgy?
Thanks

video part of my xorg.conf file: 

```

Section "Device"
    Identifier    "S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
    Driver        "savage"
    BusID        "PCI:1:0:0"
    Option        "DMPS"
    Option        "HWCursor" "true"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    HorizSync    30-97
    VertRefresh    50-180
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1400x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1400x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1400x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1400x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1400x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1400x1050"
    EndSubSection
    Option        "DPMS"
EndSection

```

---

