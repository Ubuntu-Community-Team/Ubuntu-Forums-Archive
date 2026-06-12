---
title: "Weird video issues after yesterday ubuntu upgrade"
date: 2009-10-30
forum: Multimedia Software
---

### Post by b0riss on 2009-10-30
Hello

I have upgraded ubuntu yesterday to lastest version and now colors in all videos changed as follows:

[[IMG]http://img137.imageshack.us/img137/5545/video1.th.png[/IMG]](http://img137.imageshack.us/i/video1.png/)

I tried different video players such as Xine, VLC, Mplayer, etc but in each of this players colors are changed, there is on exception: Avidemux:

[[IMG]http://img252.imageshack.us/img252/3121/video2.th.png[/IMG]](http://img252.imageshack.us/i/video2.png/)

[[IMG]http://img42.imageshack.us/img42/5755/video3.th.png[/IMG]](http://img42.imageshack.us/i/video3.png/)

Does anyone have the same problem? I did not changed any settings, just upgraded ubuntu yesterday, and then shut in down. This issue related only to videos in mentioned video players, if I watch video on youtube everything is ok.

No changes were made in xorg.conf, but if it make sense here is contents of this file:

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL E196FP"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500 GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: nvidia-auto-select +1680+0, DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by irvingswiftj86 on 2009-10-30
I have the same problem....
Has anyone any idea on how to fix this?

---

### Post by pir on 2009-10-31
[img]http://u.kexx.net/img1808.png[/img]
had that.

Found out it was simply the hue. You can change it for all video playback in totem: 
Edit > preferences > display > RESET TO DEFAULTS (bottom-right)


[SIZE="1"]For all the googlers with this problem, some tags:
video weird colors, video strange colors, video problems after upgrade to ubuntu 9.10. VLC weird colors after upgrade. Totem weird colors after upgrade[/SIZE]

[img]http://u.kexx.net/img1809.png[/img]

---

### Post by b0riss on 2009-11-01
> **pir said:**
> [img]http://u.kexx.net/img1808.png[/img]
had that.

Found out it was simply the hue. You can change it for all video playback in totem: 
Edit > preferences > display > RESET TO DEFAULTS (bottom-right)


[SIZE="1"]For all the googlers with this problem, some tags:
video weird colors, video strange colors, video problems after upgrade to ubuntu 9.10. VLC weird colors after upgrade. Totem weird colors after upgrade[/SIZE]

[img]http://u.kexx.net/img1809.png[/img]
Thank you :)

---

### Post by arde on 2009-11-02
Thank you all - the reset to defaults in totem worked for me too.

---

### Post by kswenson on 2009-11-02
This happened to me too...
  I know I didn't touch those settings so this must be a bug.

---

### Post by Underlien on 2009-11-06
Thx for posting the answer, solved the problem for me too.

(wierd bug, i have never used totem player so there's no way i have changed that setting my self)

Cheers!

---

