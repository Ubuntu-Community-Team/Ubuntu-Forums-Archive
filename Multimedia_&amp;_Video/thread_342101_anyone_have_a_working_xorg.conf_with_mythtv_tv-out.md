---
title: "anyone have a working xorg.conf with mythtv tv-out for ati 9250?"
date: 2007-01-19
forum: Multimedia &amp; Video
---

### Post by toorima on 2007-01-19
Anyone have a perfectly working xorg.conf for a ati 9250 pro with tv-out only? 
I have problems with mythtvs internal player, if I have VideoOverlay "on" disabled in xorg.conf video size is good but very jerky when watching tv or a recording, if I have have it enabled picture isn't jerky but only the top half or so can be seen on the tv.
Mplayer and vlc aren't jerky when videooverlay is disabled, only mythtv frontend is having problems.

```
Section "Monitor"
        Identifier   "Generic Monitor"
        HorizSync    28.0 - 40.0
        VertRefresh  43.0 - 60.0
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "TVFormat" "NTSC-M"
        Option      "ForceMonitors" "tv,nocrt1"
        Option      "UseFBDev" "false"
#       Option      "TVOverscan" "on"
        Option      "OverlayOnTV" "0"
        Option      "TexturedVideo" "on"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "Generic Monitor"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "800x600"
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection
```

My system is
Celeron 1.3 Ghz
256 mb ram
ATI Radeon 9250 PRO pci 128 mb with repos fglrx driver (does the open source driver give tv-out for this card?)
Hauppauge pvr-150 retail

---

### Post by bruceleo on 2007-04-12
In /etc/X11/xorg.conf:
Under "Devices" set Option "VideoOverlay" to "off"

---

### Post by toorima on 2007-04-13
Yeah like I said in the original post, VideoOverlay "on" gives good size but jerky picture, VideoOverlay "off" makes the picture way to big but it's not jerky

But I "solved" it by selling the ati card and got a nvidia with dvi out, and with a dvi to hdmi converter, picture is perfect on my 42" plasma.

---

### Post by bruceleo on 2007-04-14
> **toorima said:**
> Yeah like I said in the original post, VideoOverlay "on" gives good size but jerky picture, VideoOverlay "off" makes the picture way to big but it's not jerky

But I "solved" it by selling the ati card and got a nvidia with dvi out, and with a dvi to hdmi converter, picture is perfect on my 42" plasma.

Yeah, that works too.

---

### Post by Stefanius on 2007-11-09
hi,

Maybe a sily qeustion, but how did you get youre driver working? and wich version/installation method did you use? I tried several options but none of them shows anything on my TV (obly a bluring picture)

I also have a 9250. Is it enough to copy youre Xconf.org section above, or must i do something else?

Stef.

---

