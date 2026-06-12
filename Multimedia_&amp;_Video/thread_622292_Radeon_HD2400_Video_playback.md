---
title: "Radeon HD2400 Video playback"
date: 2007-11-24
forum: Multimedia &amp; Video
---

### Post by fa2k on 2007-11-24
Update: It seems that the driver was not installed/enabled. I will update this post with results after installing it, 
Update2: New driver, no fix.
Update3: Xorg.0.log indicates old driver is in use. Giving up for now.

I just installed the new Catalyst driver; version 7.10, hoping that it would fix some problems. It improved things, but not all. When I watch videos, i get a "tearing" artifact. This happens equally in OpenGL and Xv modes, and in VLC and MPlayer. It happens for videos of all resolutions and codecs. My CPU is a (single core) Athlon 3800 which should be fast enough.

When in 60Hz mode for 1280x720, or 30Hz (interlaced, i think) for 1920x1080, the effect randomly appears in high-motion scenes, on all parts of the screen.

When in 50Hz, or 25Hz, modes, the effect is confined to a single line of tearing, on the left side diagonal, then horizontal. This effect is more noticeable than the previous one.

I have verified that Direct Rendering and XVideo are both working. Can I enable some kind of vertical sync? 
This is the device section of my xorg.conf, it's not very interesting, however:

```

Section "Device"

#       Option      "VideoOverlay" "on"
#       Option      "OpenGLOverlay" "off"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        BoardName   "ati"
        Option      "TexturedVideoSync" "on"
        Option      "ForceMonitors" "tmds2"
        BusID       "PCI:6:0:0"
EndSection

```

---

