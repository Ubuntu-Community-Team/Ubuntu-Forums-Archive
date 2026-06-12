---
title: "XvMC doesn't want to work on fresh Mythbuntu 9.04 install"
date: 2009-05-19
forum: Mythbuntu
---

### Post by dmfrey on 2009-05-19
I tried to enable XvMC on my fresh install of Mythbuntu 9.04.  It doesn't seem to work.  HD appears to playback fine, but I get significant tearing on SD and ripped dvds.

Card: Asus EN8400GS Silent

Playback Profile: Standard CPU--

The logs show quite a bit of this message when playing HD recordings:
```

2009-05-19 08:41:02.919 VideoOutputXv Error: XvMC output requested, but is not supported by display.
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".

```

I also see this:
```

2009-05-19 08:41:03.059 VideoOutputXv: Desired video renderer 'xvmc-blit' not available.
			codec 'MPEG2' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2009-05-19 08:41:03.060 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-05-19 08:41:03.113 VideoOutputXv: Ack! Disabling ChromaKey OSD
			We can't use ChromaKey OSD if chromakeying is not supported!
2009-05-19 08:41:03.114 OSD Theme Dimensions W: 640 H: 480

```

XvMCConfig is setup as follows:
```

libXvMCNVIDIA_dynamic.so.1

```

xorg.conf is configured as follows (relevant portions shown):
```

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
        Option  "RenderAccel" "true"
        Option "UseEvents" "true"
        Option "XvmcUsesTextures" "false"  # necessary for color Chromakey OSD)
        Option "NVAGP" "3"                 # some users report 2 or 3 works better
EndSection

Section "Extensions"
        Option "Composite" "Disabled"
EndSection

```

I can tell XvMC is not working because it is still showing the blue OSD instead of the black OSD.

Any help would be greatly appreciated.

Thanks.

---

### Post by ianhaycox on 2009-05-19
Your config file should be /etc/X11/XvMCConfig not X**c**MCConfig

---

### Post by dmfrey on 2009-05-19
It is...that was a typo.  I will fix it now.

---

### Post by nickrout on 2009-05-19
xvmc does not work on 8000 series nvidia cards. I think they stopped about 6000 or 7000.

EDIT, from wikipedia entry for xvmc:

> Hardware manufacturers

[edit] Nvidia

There are currently three X11 Nvidia drivers available: a 2D-only open source but obfuscated driver maintained by Nvidia called nv, an open source driver based on nv developed by the Linux community called Nouveau, and a proprietary binary driver by Nvidia. Nouveau is not pursuing XvMC support [1], the 2D nv driver does not support XvMC, and t**he official proprietary binary driver by Nvidia only supports MPEG-2 offloading (mo comp and iDCT) on hardware up to and including the GeForce 7000 series**.

---

### Post by dmfrey on 2009-05-19
Thanks.  I was unaware they stopped supporting xvmc.  I guess vdpau will take its place anyway.

---

### Post by nickrout on 2009-05-20
> **dmfrey said:**
> Thanks.  I was unaware they stopped supporting xvmc.  I guess vdpau will take its place anyway.

Yes it should work well for you if you use JYA's repositories.

---

