---
title: "TV Out As On My Monitor? (NVIDIA FX 6200)"
date: 2006-08-23
forum: Multimedia &amp; Video
---

### Post by BitTorrentBuddha on 2006-08-23
Hey, I was looking to get the same display on my TV as on my monitor with my NVIDIA FX 6200 GPU. I've already looked at [this thread](http://www.ubuntuforums.org/showthread.php?t=98456), but it set up the TV as a separate display which had no preferences saved nor anything (most importantly codecs) installed. Is there a way to just have my TV display what my monitor displays?

---

### Post by BerlinOliver on 2006-08-23
Nvidia has the option Twinview. With this you can clone your Monitor to the TV. But at my place it only showed the upper left part of my desktop. But I think you can change this.

Here are my Twinview options from my xorg.conf:
```

       Option "TwinView"
       Option "SecondMonitorHorizSync"     "30-50"
       Option "SecondMonitorVertRefresh"   "60"
       Option "MetaModes" "1024x768, 640x480; 1024x768, 1024x768;"
       Option "TVStandard" "PAL-B"
       Option "TwinViewOrientation" "Clone"
       Option "NoLogo" "off"
       Option "HWCursor" "on"
       Option "CursorShadow" "off"
       Option "TVOutFormat" "COMPOSITE"

```

These options you can add to the device section.

---

