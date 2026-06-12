---
title: "Load MythTV load right screen"
date: 2007-08-17
forum: Multimedia &amp; Video
---

### Post by loudestnoise on 2007-08-17
Here's what I currently have going. I have Ubuntu set to autologin as the mythtv user and have it so mythfrontend will load by itself.  The idea is to have my MythTV act as you guessed it, a PVR.  I cannot however, force MythTV to load on my s-video output.  For some reason it loads on the main screen. I want it to load on my TV, which is connected via s-video.  I followed instructions [here]("https://wiki.ubuntu.com/NvidiaTVOut") on getting my nvidia geforce 5200 to output, which is working fine, I just need mythtv to load on that screen at startup, not on the main screen. In fact, I don't plan on having a computer monitor even connected, just the TV via s-video. Here's the part that I edited in my xorg.conf, if that helps.

```

Section "Device"
    Identifier    "nVidia GeForce 5200"
    Driver        "nvidia" 
    BusID        "PCI:1:0:0"
    Option        "ConnectedMonitor"  "CRT, TV"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS" 
    HorizSync    30-70
    VertRefresh    50-160
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "nVidia GeForce 5200"
    Monitor        "Generic Monitor" 
    DefaultDepth    24
    Option        "Twinview"
    Option        "TVOutFormat"  "SVIDEO"
    Option        "TVStandard"   "NTSC-M"
    Option        "Metamodes"    "1024x768,640x480; 1024x768,NULL; 800x600,NULL; 640x480,NULL" 
    
    SubSection "Display"
        Depth        1
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4 
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1024x768" "800x600" "640x480" 
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display" 
        Depth        16
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1024x768" "800x600" "640x480" 
    EndSubSection
EndSection


```

---

### Post by loudestnoise on 2007-08-17
Solved my own problem by adding

```
	Option			"UseDisplayDevice" "TV"
```

to the Device section of xorg.conf

---

