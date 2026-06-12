---
title: "mplayer too slow on new laptop"
date: 2008-11-15
forum: Multimedia Software
---

### Post by shizow on 2008-11-15
i have a Dell Vostro 1310 with 128 MB nVidia GeForce 8400M GS
i use intrepid.

when i play a file with a high resolution like 1280x720
mplayer says that the CPU is too slow to play it
why is this so?

here my x.org file

```


Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

```

---

### Post by shizow on 2008-12-22
can anyone help please?

---

### Post by shirilover on 2008-12-23
Your graphics card will have very little to do with playing back HD video in linux. Most of the decoding work is done by the processor.

From the Dell information page, it states the the Vostro 1310 comes standard with a 1.8 GHz dual-core processor. You may have trouble attempting to play HD H.264 video with this processor.

You can add the following to your mplayer command line:
-lavdopts fast:threads=2:skiploopfilter=all
or by adding the following to ~/.mplayer/config
lavdopts=fast:threads=2:skiploopfilter=all

---

### Post by shizow on 2009-01-09
solved:
i had to set my CPU power to Performance

---

