---
title: "mythfrontend playback with fglrx"
date: 2009-02-10
forum: Mythbuntu
---

### Post by ajut on 2009-02-10
Hello,

I have problem with mythfrontend playback, where CPU of one core is loaded about 80-90% for mpeg-4/AVC TS (DVB-T 720x756) and there are dropped frames.

I tried all possible decoders and video renders combination from "Playback Profiles 3/9" in mythfrontend setup - no luck 

For example mythfrontend can't play VOOM-HD (1920x1088(i?)) at all:( (CPU is over 120%).

I have feeling, that mythfrontend must be misconfigured somehow, because there is XBMC at the same PC (manually compiled from SVN), which can play VOOM_HD (myth://user:pass@server) nicely - 90% CPU and no dropped frames.

Any ideas?

Configuration:
---
MythBuntu 8.10
Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
2GB DDR3
Radeon HD 4550
xorg-driver-fglrx 2:8.543-0ubuntu4
1024x768 S-Video TV out
mythbackend; mythfrontend and XBMC are local
---

xorg.conf
```

Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"

#       Load  "glx"
EndSection

Section "Monitor"
        Identifier   "Configured Monitor"
EndSection

Section "Device"
        Identifier  "Configured Video Device"
        Driver      "fglrx"
        Option      "ForceMonitors" "tv,none"
        Option      "NoTV" "no"
        Option      "TexturedVideo" "off"
        Option      "OpenGLOverlay" "on"
        Option      "TVFormat" "PAL-B"
        Option      "UseFastTLS" "1"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Configured Video Device"
        Monitor    "Configured Monitor"
        DefaultDepth     24
        SubSection "Display"

                #Modes    "800x600"
                Viewport   0 0
                Depth     24
                Modes    "1024x768"
        EndSubSection
EndSection

```

BTW: Before ATI I had Nvidia GT6600, which worked very well with that hardware+software configuration.

---

### Post by ajut on 2009-02-12
Ok. It seems that newest fglrx from AMD site resolved my CPU LOAD problem. SD content takes now 20-30% for playback and HD about 70-80%.

BTW: Seems that Radeon HD 4550 is not officially supported jet (no shown in AMD linux x86 driver download list).

---

