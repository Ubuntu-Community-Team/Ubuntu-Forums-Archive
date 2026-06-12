---
title: "AVerMedia TVPhone98"
date: 2005-11-08
forum: Multimedia &amp; Video
---

### Post by kamillozo on 2005-11-08
Hello everybody!
I need some help to get my tv tuner work properly under breezy. I got AVerMedia TVPhone98.
When I run lspci I got:
```
0000:00:0c.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
0000:00:0c.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)

```

When I start tvtime:
```
Uruchomione tvtime 1.0.1.
Czytanie konfiguracji z /etc/tvtime/tvtime.xml
Czytanie konfiguracji z /home/kamil/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: http://gatos.souceforge.net/
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

```

Zapping TV starts without any errors but I can't find any channel...
I really don't know what should I do. Do I have to add any lines to /etc/modprobe.d/aliases?
Does anyone have this card running under ubuntu? Help me please...

---

