---
title: "TwinView :  Apps start between monitors"
date: 2007-11-26
forum: Multimedia &amp; Video
---

### Post by derjur on 2007-11-26
i'm not sure how to search for this, but i did try ;)

i'm running twinview for dual monitors, and find it works like a charm.  but when i start an app, it always starts dead center in the screen, and when i maximize, it covers both screens.  

i haven't been able to find an option to set this, nor do i know exactly how to search for it.

---

### Post by rsambuca on 2007-11-26
Which video driver?  And which method did you use to achieve the twinview?

---

### Post by derjur on 2007-11-26
nvidia-glx-new 100.14.19+

i ran nvidia-setting (sudo) to set twinview.

---

### Post by rsambuca on 2007-11-26
Mine doesn't behave this way.  Can you post your xorg.conf?

---

### Post by derjur on 2007-11-26
```


Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection




Section "Device"
    Identifier     "nVidia Corporation NV44 [Quadro NVS 285]"
    Driver         "nvidia"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    BusID          "PCI:3:0:0"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 285"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV44 [Quadro NVS 285]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT-0: nvidia-auto-select +0+0, CRT-1: nvidia-auto-select +1280+0"
EndSection


```

---

### Post by rsambuca on 2007-11-26
First, I recommend making a backup of this xorg since you know it works.  Not how you want it to, but it does work!

Next, try commenting out the line that says:

 Option         "Xinerama" "0"

To your first "Device" Section, try adding these lines:

        Option          "TwinView"      "True"
        Option          "TwinViewOrientation"   "RightOf"
        Option          "UseEdidFreqs"  "True"
        Option          "MetaModes"     "1280x1024,1280x1024; 1280x1024,1280x720"

Delete or comment out the second "Device" Section

Save it and then restart X with the ol' Control-Alt-Backspace.  Cross your fingers.  If that doesn't work, then copy back your backup.

Either way, let us know how it goes, and good luck!

---

### Post by derjur on 2007-11-26
that did it...

i did have to tweak the identifiers a bit, but now it behaves as i'd expect.

many thanks!

---

### Post by derjur on 2007-11-26
now compiz has an octogon on both monitors...  i'd read about this in my travels


[http://forum.compiz-fusion.org/showthread.php?t=2168](http://forum.compiz-fusion.org/showthread.php?t=2168)

now, as i run several VMs on this machine, i'm ditching compiz for something a little more lightweight like openbox and won't bother fixing this problem.  but there is the link for posterity :D

---

### Post by rsambuca on 2007-11-26
Glad to help.  Just a lucky guess!

---

