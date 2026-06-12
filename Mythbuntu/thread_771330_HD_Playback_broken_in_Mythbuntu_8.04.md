---
title: "HD Playback broken in Mythbuntu 8.04"
date: 2008-04-27
forum: Mythbuntu
---

### Post by aseriesoftubes on 2008-04-27
I just upgraded from the 8.04 beta to the release version, and I'm growing less and less happy with Mythbuntu.

Before ever using the beta, I used Ubuntu 7.10 and MythTV .20.2. I played back HD using XvMC, and even though my processor is a little slow (P4 2.6GHz), everything worked fine. 

Once I upgraded to .21, XvMC broke. I would only see a black screen when attempting to play back anything using XvMC. I upgraded to the beta, and the problem persisted, though I managed to get decent HD playback using libmpeg2 and some of the less-CPU-intensive deinterlacing methods.

I just upgraded to the official 8.04 release, and my problems have gotten worse. Now I get a tearing effect about 1/3 of the way down from the top of my screen, and playback is jerky. Some HD recordings also pause every second, and fill my logs with "WriteAudio: buffer underrun" errors.

I tried XvMC again and got the black screen coupled with 100% CPU usage. I've checked and unchecked the Sync to VBlank options in nvidia-settings, but the settings don't stick. 

What is going on here? Is XvMC completely broken? I've searched the web and this forum, but none of the tips I've found have helped.

My setup (frontend only):
P4 2.6GHz
Geforce 6800, AGP 8x, 128MB
512MB RAM
SPDIF audio using SB Live

---

### Post by gavinjc on 2008-05-06
I had the same problem so I went through the XvMC setup guide at:

[http://www.mythtv.org/wiki/index.php/XvMC]("http://www.mythtv.org/wiki/index.php/XvMC") 

everything seemed OK except for the xorg.conf so I added this to my xorg.conf and XvMC is now working again.

```
Section "Device"
    Identifier "Videocard0"
    Driver  "nvidia"
    Option "UseEvents" "true"
    Option "XvmcUsesTextures" "false"
    Option "NVAGP" "1"
EndSection

Section "Extensions"
    Option "Composite" "Disabled"
EndSection
```

Cheers Gavin C.

---

### Post by aseriesoftubes on 2008-05-07
Right, I did the same and it works pretty well now (I probably should have marked this thread [Solved], oops). 

The one issue I still have is some pretty severe stuttering when the OSD comes up when playing HD recordings. This is apparently a known issue. Anyone have any suggested fixes?

---

