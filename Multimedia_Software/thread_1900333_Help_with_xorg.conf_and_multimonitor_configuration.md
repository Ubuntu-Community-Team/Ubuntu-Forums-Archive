---
title: "Help with xorg.conf and multimonitor configuration"
date: 2011-12-26
forum: Multimedia Software
---

### Post by elite1967 on 2011-12-26
Hi all,
hope the Xmas went well for everyone.

I am using a Ubuntu 11.04 server as a media player (with XBMC) with nVidia GT430.

Here is my question:
My video card has 3 outputs: VGA, DVI and HDMI.
I would like to have this configuration:
- VIDEO to the VGA output 
- AUDIO to the HDMI output

VGA is "CRT-1", DVI is "DFP-0" and HDMI is "DFP-1"
I use X11 for my media player application, so I configured xorg.conf in the following way:

```
Section "Device"
        Identifier "nvidia"
        Driver  "nvidia"
        Option  "NoLogo"              "true"
        Option  "DynamicTwinView"     "false"
        Option  "NoFlip"              "false"
        Option  "FlatPanelProperties" "Scaling = Native"
        Option  "ModeValidation"      "NoVesaModes, NoXServerModes"
        Option  "UseDisplayDevice"    "CRT-1"
        Option  "ModeDebug"           "true"
        Option  "HWCursor"            "false"
EndSection

Section "Screen"
        Identifier      "screen"
        Device          "nvidia"
        SubSection      "Display"
                Modes "1920x1080_60"
        EndSubSection
EndSection

Section "Extensions"
        Option  "Composite"           "false"
EndSection
```

But, if I connect both HDMI and VGA terminal, the video output goes to the HDMI disregarding the xorg.conf.
If I connect only the VGA the video goes to the VGA.

So, and here is the question, how can I force the video to the VGA terminal even if the HDMI terminal is connected?

Any idea?

---

