---
title: "flickering monitor with nouveau"
date: 2010-06-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by reub2000 on 2010-06-21
My current setup is 2 monitors, an LCD on the left and CRT on the left. The issue, is that the CRT on the right flickers 3 or 4 times while KDE is loading. I configured the setup in maverick as such:

```
Section "Monitor"
        Identifier "NEC"
EndSection

Section "Monitor"
        Identifier "CRT"
        VertRefresh 75-85
        HorizSync   31.5-110
        Option  "RightOf" "NEC"

EndSection

Section "Device"
        Identifier      "gf7800gs"
        Driver          "nouveau"
        Option  "Monitor-DVI-I-1" "NEC"
        Option  "Monitor-VGA-1"   "CRT"
EndSection

Section "Screen"
        Identifier      "dual_head"
        DefaultDepth    24
          SubSection "Display"
                Depth 24
                Virtual 2560 1024
          EndSubSection
        Device  "gf7800gs"
EndSection

Section "ServerLayout"
        Identifier      "layout1"
        Screen          "dual_head"
        Option  "AIGLX" "false"
EndSection

```

---

