---
title: "Improve Video Playback"
date: 2008-11-12
forum: Mythbuntu
---

### Post by verevi on 2008-11-12
How do I improve the video playback of live TV?  

Currently, when a camera pans left or right, it looks a bit jagged. 

I just freshly installed 8.10.  I'm using an intel video card (82945G).  My xorg.conf is simply this (do I need to do something to install the intel driver?  when I apt-get xserver-xorg-video-intel, it says it is already installed):

```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```I have tried changes profiles from CPU-,CPU++, etc but its still the same. Any help would be greatly appreciated.

---

