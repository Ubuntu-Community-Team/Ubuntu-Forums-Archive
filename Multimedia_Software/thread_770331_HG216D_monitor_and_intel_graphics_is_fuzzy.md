---
title: "HG216D monitor and intel graphics is fuzzy"
date: 2008-04-27
forum: Multimedia Software
---

### Post by fruzzled on 2008-04-27
I just got a 21.6" Hanns.G HG216D and I have a laptop with a "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller". They are connected using a VGA cable and not HDMI/DVI. Both have a native resolution of 1680x1050. Initially when I setup the monitor it only filled half the screen I fixed this by using gtf to add a Modeline to my xorg.conf. The display is now full screen but I have grainy fuzz over the screen (see [http://images.cjb.net/061ed.jpg](http://images.cjb.net/061ed.jpg)). Any ideas about how I can fix this?

This is what the relevant section of my xorg.conf looks like at the moment.

```
Section "Monitor"
        Identifier      "HG216"
        Option          "DPMS"
        HorizSync       30-82
        VertRefresh     50-75
        DisplaySize     465 291
        Option "DDC" "False"
        # 1680x1050 @ 60.00 Hz (GTF) hsync: 65.22 kHz; pclk: 147.14 MHz
        Modeline "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync
        Option "PreferredMode" "1680x1050_60.00"
EndSection
```

---

