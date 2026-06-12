---
title: "choppy video playback in feisty"
date: 2007-06-10
forum: Multimedia &amp; Video
---

### Post by uman2008 on 2007-06-10
Hello. I finally managed to get feisty working on my dell 6400 inspiron laptop, but only one issue left to solve ;) I'm using beryl 0.3.0 and fglrx 8.34.8 with my ati radeon mobility x1400 card. Everything is working fine, except for video playback, for example xvid videos in video lan player look choppy, horizontal chops occur on fast scene change. I didnt manage to get still image showing chop, so i recorded video I played in videolan player, so that you get the idea of what I'm talking about. Link to the video: [http://rapidshare.com/files/36402868/chop.ogg.html](http://rapidshare.com/files/36402868/chop.ogg.html)

edit: forgot to mention, video runs smooth but chops occur on every other scene
edit2: friend that has ibm with ati radeon 7500 reported no chops visible on the video, so I'll add my xorg.conf just in case
```
Section "ServerFlags"
        Option      "AIGLX" "off"
EndSection
...
Section "Device"
        Identifier  "Generic Video Card"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
        Option "UseInternalAGPGART" "yes"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "on"
        Option "NvAGP" "1"
EndSection
...
Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "Disable"
EndSection


```

---

### Post by mocha on 2007-06-30
I have this same problem on a fresh install of Feisty using the latest generic kernel(s).  I posted a bug report but haven't got much reaction to it.  My machine is a C2D E6420.  It's plenty fast.  I used to use much lesser machines with Hoary, Dapper, and Edgy and didn't have these problems.

---

### Post by xagor on 2007-07-05
I'm fairly new to Linux and this is the first Ubuntu (Feisty) version I've installed.  I'm also experiencing choppy video playback. My problem only occurs during playback through my LAN. If the file is local there is no problem. 

I installed Feisty on an Alienware 51m laptop w/ ATI Radeon mobility 7500.
I'm using beryl as well.

Any information to pass on to this newb will be appreciated

TIA!

---

