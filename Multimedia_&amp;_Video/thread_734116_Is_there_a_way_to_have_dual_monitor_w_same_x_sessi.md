---
title: "Is there a way to have dual monitor w/ same x session, but separate workspaces?"
date: 2008-03-24
forum: Multimedia &amp; Video
---

### Post by belgarth on 2008-03-24
Hi all,

I'm looking for a way to get around the restriction of not being able to move windows between seperate x sessions when using dual monitors. Is there a way to have each monitor display a separate workspace of the same x session? This would seem like a way to get around the restriction, but I can't find any mention on if this is possible.

If is is needed my pc is a IBM thinkpad T61p w/, nVidia 570M Quadro running Gutsy.

Thanks for any help,
Brett

---

### Post by mattk132 on 2008-03-24
If you have an nvidia, the best way to set it up is with the command nvidia-settings.  This will give you a nice gui to fix your problems.:)

---

### Post by .nedberg on 2008-03-24
On Nvidia it is called TwinView.

In my xorg.conf, device section I have:
```

Section "Device"
        Identifier      "nVidia Corporation NV43 [GeForce 6600 GT]"
        Driver          "nvidia"
        Busid           "PCI:5:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "False"
        Option "Twinview" "true"
        Option "MetaModes" "1280x1024,1280x1024; 1280x1024,1024x768; 1024x768,1024x768"
        Option "SecondMonitorHorizSync" "30-65"
        Option "SecondMonitorVertRefresh" "50-75"
        Option "TwinViewOrientation" "RightOf"
EndSection


```

Works like a charm!

---

