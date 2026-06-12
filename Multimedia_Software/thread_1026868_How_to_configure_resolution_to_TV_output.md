---
title: "How to configure resolution to TV output?"
date: 2008-12-31
forum: Multimedia Software
---

### Post by irotas on 2008-12-31
I finally got my TV output mostly working for my ATI Radeon X300 video card on my Dell D610 laptop (Intrepid Ibex) over an S-Video cable. The only thing I haven't been able to figure out is how to keep my laptop LCD screen at 1400x1050 while running the TV screen (NTSC-M) at 640x480.

Here's my xorg.conf:
Section  "Device"
  Identifier  "Configured Video Device"
  Driver      "fglrx"
  Option      "VideoOverlay"       "on"
  Option      "OpenGLOverlay"      "off"
  Option      "TVFormat"           "NTSC-M"
  Option      "ForceMonitors"      "tv,none"
  Option      "NoTV"               "no"
  Option      "UseInternalAGPGART" "no"
EndSection

Section  "Monitor"
  Identifier  "Configured Monitor"
EndSection

Section  "Screen"
  Identifier    "Default Screen"
  Monitor       "Configured Monitor"
  Device        "Configured Video Device"
  DefaultDepth	24
  SubSection  "Display"
    Viewport  0 0
    Depth     24
    Modes     "1400x1050" "640x480"
  EndSubSection
EndSection


Any ideas? I looked around Google and so far have not had any luck.

Thanks,
Adam

---

