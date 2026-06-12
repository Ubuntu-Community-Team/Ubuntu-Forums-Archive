---
title: "Ati Catalyst tweaks"
date: 2009-07-27
forum: Multimedia Software
---

### Post by xzero1 on 2009-07-27
These links has been very useful so I thought I would post them here:

 [http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

[http://www.linuxinsight.com/full-screen-flash-not-working-under-compiz.html](http://www.linuxinsight.com/full-screen-flash-not-working-under-compiz.html)

Note the last option 'Undirect Fullscreen Windows" must be  enabled for xv fullscreen video acceleration on supported cards. These options may also affect some wine games.

Tested using Ubuntu Jaunty 64 bit, catalyst 9.6 on an ati 3300IGP. Feel free to post additional tweaks or fixes.

BTW, until I installed 9.6 I had xorg freezing issues as many have posted about. With 9.6 there are no real issues to report.:)

I have recently found a more up to date link thanks to another poster: [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

My current xorg.conf file:
```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
    Option        "AIGLX" "on" #->Enables Xorg's AIGLX rendering technic
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "UseFastTLS" "1"
    Option        "TexturedVideo" "on" #->AVIVO accelerated video
    Option        "OpenGLOverlay" "off"#->Deprecated generally older than Acropolis that's why off
    Option        "Textured2D" "on" #->Used to be experimental now works for all new cards!
    Option        "VideoOverlay" "off"
    BusID       "PCI:1:5:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "DRI"
    Group        "Video"
    Mode         0666
EndSection

Section "Extensions"
    Option        "RENDER" "Enable"
    Option        "DAMAGE" "Enable"
    Option        "Composite" "Enable"
EndSection
```

---

