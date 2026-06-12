---
title: "Resolution 1280x1024"
date: 2010-08-31
forum: Multimedia Software
---

### Post by stefanog on 2010-08-31
Hi,
this is my monitor [http://www0.dealtime.co.uk/xPF-AOC-LM765](http://www0.dealtime.co.uk/xPF-AOC-LM765)
and this is my xorg.conf:
```

Section "Monitor"
   Identifier   "Monitor Generico"
   Option      "DPMS"
   HorizSync     30.0-80.0
   VertRefresh   55.0-75.0
EndSection

Section "Screen"
   Identifier   "Default Screen"
   Device      "Scheda video generica"
   Monitor      "Monitor Generico"
   DefaultDepth   24

        SubSection "Display"
      Depth      24
      Modes       "1280x1024"  "1280x960" "1280x854" "1152x768" "1152x864" "1024x768" "800x600"
   EndSubSection

 SubSection "Display"
      Depth      32
      Modes       "1280x1024"  "1280x960" "1280x854" "1152x768" "1152x864" "1024x768" "800x600"
   EndSubSection

EndSection

```

I am not able to reach 1280x1024 resolution. The max res i can set in Preferences>Monitor is 1152x864. (Ubuntu 10.04)
Suggestions?

---

