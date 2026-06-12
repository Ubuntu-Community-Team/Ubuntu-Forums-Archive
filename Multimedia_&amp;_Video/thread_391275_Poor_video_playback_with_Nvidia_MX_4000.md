---
title: "Poor video playback with Nvidia MX 4000"
date: 2007-03-23
forum: Multimedia &amp; Video
---

### Post by barney_1 on 2007-03-23
Hi folks,

I have recently purchased and installed an Nvidia MX 4000 for use with my MythTV box.  I was able to get the card working today with driver version 1.0-9631.  I installed this driver from the packed at Nvidia's website as I couldn't get the Envy script to make it past the build process.

I have enabled the TV out and can watch video on my Television but the playback is poor.  When there is a lot of motion the picture is jerky.  I'll post some pertinent information below:

lspci:
```
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] (rev c1)

```

Device section of xorg.conf:
```
Section "Device"
        Identifier      "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "UseFBDev"              "true"
        Option "TwinView" "true"
        Option "TwinViewOrientation" "Clone"
        Option "TVOutFormat" "SVIDEO"
        Option "TVStandard" "NTSC-M"
        Option "SecondMonitorHorizSync" "30-50"
        Option "SecondMonitorVertRefresh" "60"
        Option "MetaModes" "1024x768,1024x768;800x600,800x600;640x480,640x480;    512x384,512x384"
EndSection

```

glxinfo | grep rendering
```
direct rendering: yes
```

Any ideas?

---

### Post by barney_1 on 2007-03-24
I believe I have found a solution to this problem in the MythTV settings.

From the MythTV main menu go to Utilities/Setup --> Setup --> TV Settings --> Playback 
Check the box titled:
```
Enable OpenGL vertical sync for timing
```

I hope this helps if you were experiencing similar video quality issues.

---

### Post by barney_1 on 2007-04-10
I've decided this card is very poor for video performance with mythtv.  I sold it on ebay and went back to my ATI Radeon 9000.

---

