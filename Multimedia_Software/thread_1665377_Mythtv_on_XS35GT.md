---
title: "Mythtv on XS35GT"
date: 2011-01-12
forum: Multimedia Software
---

### Post by stevezau on 2011-01-12
Hi All,

I've setup mythtv on Ubuntu 10.10 with mythbuntu (mythtv 0.24). I'm using a shuttle XS35GT which comes with an Ion2 GT218 GPU.

when i enable Advanced(2x) on HD content my GPU stats goes to 99% and the picture starts to shutter etc. When playing SD content is averages at 50-60% depending on the incoming stream. I've tested HD on Temporal 2X and it seems to sit at a very low 20%. No matter what im de-coding the CPU always sits at 10-20% so it appears thats not a bottle neck.

Can anyone confirm is theses numbers sound correct? Not knowing much about h/w i thought the G218 GPU shoud be able to handle Adv(2x) on HD content.

I've installed the latest Nvidia drivers and followed the preformance steps as mentioned on the mythtv website.

```

==============NVSMI LOG==============


Timestamp                       : Wed Jan 12 23:27:58 2011

Driver Version                  : 260.19.29


GPU 0:
        Product Name            : ION
        PCI Device/Vendor ID    : a6f10de
        PCI Location ID         : 0:1:0
        Board Serial            : 6178212881
        Display                 : Connected
        Temperature             : 56 C
        Utilization
            GPU                 : 99%
            Memory              : 33%

```

My xorg.conf is as follows

```

Section "Device"
        Identifier "nvidia"
        Driver  "nvidia"
        Option  "NoLogo"              "true"
        Option  "DynamicTwinView"     "false"
        Option  "NoFlip"              "false"
        Option  "FlatPanelProperties" "Scaling = Native"
        Option  "ModeValidation"      "NoVesaModes, NoXServerModes"        
        Option  "UseDisplayDevice"    "DFP-0"
        Option  "ModeDebug"           "true"
        Option  "HWCursor"            "false"
        Option "UseEvents" "True"
EndSection

Section "Screen"
        Identifier      "screen"
        Device          "nvidia"
        SubSection      "Display"
                Modes "1920x1080_60i" "1280x720_60" 
        EndSubSection
        Option "UseEvents" "True"
EndSection

Section "Extensions"
        Option  "Composite"           "false"
EndSection

```

---

