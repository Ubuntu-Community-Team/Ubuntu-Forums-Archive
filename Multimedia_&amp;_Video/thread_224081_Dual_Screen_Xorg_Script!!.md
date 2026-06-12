---
title: "Dual Screen Xorg Script!!"
date: 2006-07-27
forum: Multimedia &amp; Video
---

### Post by StrikerWorldWide on 2006-07-27
Help me please!! I am quite the n00b, but I have trolled the web looking for ways to get my dual monitors (both Benq FP71G+S) working in TwinView on Dapper. I must have restored my backup easily 7 times desperately trying anything and everything to get it to work. 

I got it working once, but the refresh rate wouldn't change, so I beg of someone, anyone - please give me a custom xorg.conf script so I can end my hellish nightmare.

Here's my standard xorg.conf
```

Section "Device"
        Identifier      "NVIDIA Corporation NV43 [GeForce 6600 GT]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "BenQ FP71G+S"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV43 [GeForce 6600 GT]"
        Monitor         "BenQ FP71G+S"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection


```

Someone please?

-Striker

---

### Post by SuperMike on 2006-07-27
Um, have you looked here first?

[http://ubuntuforums.org/showthread.php?t=187177]("http://ubuntuforums.org/showthread.php?t=187177")

---

### Post by tseliot on 2006-07-27
One of these guide might help you:
[http://www.ubuntuforums.org/showthread.php?t=85769](http://www.ubuntuforums.org/showthread.php?t=85769)

[http://www.ubuntuforums.org/showthread.php?t=221174&highlight=twinview](http://www.ubuntuforums.org/showthread.php?t=221174&highlight=twinview)

---

