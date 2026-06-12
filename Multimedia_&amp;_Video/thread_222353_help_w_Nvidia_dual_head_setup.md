---
title: "help w/ Nvidia dual head setup"
date: 2006-07-24
forum: Multimedia &amp; Video
---

### Post by reuben on 2006-07-24
Hey guys,

I have an NVidia GForce 6600 AGP8X, and two monitors -- an LCD viewsonic, and a generic CRT. The CRT is connected via VGA, and the LCD via DVI. 

I'm having trouble getting both monitors to come up; in text mode, the LCD displays, but when X comes up the CRT takes the show. Attached are the output from lcpci, my xorg.conf, and then the x startup log. Any help is appreciated.

---

### Post by reuben on 2006-07-24
I tried switching from the nvidia to nv drivers, and that brought both monitors up. However, the sync was way off on the CRT, and switching the ids in the conf didn't help anyway. How can I work out which monitor the conf refers to?

---

### Post by cracker on 2006-07-25
Take this lightly, because I really don't know what I'm doing, but shouldn't there only be one device? You are only using one card...

```
Section "Device"
    Identifier     "NVIDIA1"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "NVIDIA1"
    Monitor        "Monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "NVIDIA1"
    Monitor        "Monitor2"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

I don't understand why you added all color depths for the LCD and not the CRT--I would have added them all, or at least done it for the CRT rather than the LCD.

I'm also thinking there would be some kind of option in the Screen sections defining which port they use on the card. Again, I don't really know, just taking a logical guess.

---

### Post by reuben on 2006-07-25
You were close! Thanks for your help. Here's the advice from the nvidia forums:

[http://www.nvnews.net/vbulletin/showthread.php?p=946552&posted=1#post946552](http://www.nvnews.net/vbulletin/showthread.php?p=946552&posted=1#post946552)

Now I just have KDE issues to sift thru (mutter mutter) :D

---

