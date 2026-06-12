---
title: "NVidia dual screen problem"
date: 2008-08-15
forum: Multimedia Software
---

### Post by TwoOranges on 2008-08-15
I just upgraded from 7.10 to 8.04 (fresh install). I configured my nvidia card for dual screen setup, but for some reason using dual screen sometimes freezes applications or makes them run slower. For instance: opening a new tab in Epiphany takes about 2 seconds when dual screen is enabled, while a tab is opened almost instantly when dual screen is disabled.

I added the following snippet to the device section of my Xorg.conf file
```
        Option "RenderAccel" "0"
        Option "CursorShadow" "1"
        Option "Coolbits" "1"
        Option "ConnectedMonitor" "dfp, dfp"
        Option "NoPowerConnectorCheck"
        Option "TwinView" "1"
        Option "TwinViewOrientation" "RightOf"
        Option     "SecondMonitorHorizSync"   "UseEdidFreqs"
        Option     "SecondMonitorVertRefresh" "UseEdidFreqs"

```

This is the same configuration I did last year for Ubuntu 7.10, but for some reason it doesn't seem to work correct in 8.10 :( Any help would be appreciated :)

---

### Post by TwoOranges on 2008-08-15
Ah, never mind :) I recreated the file with the NVidia settings application and now it's working perfectly ;)

---

