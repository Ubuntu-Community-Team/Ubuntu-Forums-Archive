---
title: "[SOLVED] Incorrect default monitor resolution"
date: 2008-10-28
forum: Multimedia Software
---

### Post by 289Shelby on 2008-10-28
I'm having problems getting my monitor to default to the correct resolution. It defaults to 1680x1050 instead of 1920x1200.

This is on Feisty. I know, I know:-)

This is what the relevant part of Xorg.0.log shows:

(WW) NVIDIA(0): The EDID for Hitachi W240D DVI (DFP-0) contradicts itself:
(WW) NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
(WW) NVIDIA(0):     EDID's valid HorizSync range (30.000-83.000 kHz) would
(WW) NVIDIA(0):     exclude this mode's HorizSync (28.1 kHz); ignoring
(WW) NVIDIA(0):     HorizSync check for mode "1920x1080".
(WW) NVIDIA(0): The EDID for Hitachi W240D DVI (DFP-0) contradicts itself:
(WW) NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
(WW) NVIDIA(0):     EDID's valid VertRefresh range (59.000-76.000 Hz) would
(WW) NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
(WW) NVIDIA(0):     VertRefresh check for mode "1920x1080".

and this is what edid-readings show:


        Mode    "1920x1200"     # vfreq 59.950Hz, hfreq 74.038kHz
                DotClock        154.000000
                HTimings        1920 1968 2000 2080
                VTimings        1200 1203 1209 1235
                Flags   "-HSync" "+VSync"

I'm not sure why the 'log' file is showing one set of frequency figures and the edid-readings showing another. Shouldn't these be the same?


I tried using the option "UseEDID" "false" but that results in a resolution of 640x480.

Card is NVIDIA GeForce 7600 GS

If I go into nvidia-settings I can change it to the correct resolution and it will stay like that without any problems, until the next reboot.

It's not that I can't get the correct resolution it's just that I have to change it each time I boot the system.

If anyone can help I would appreciate it.

---

### Post by aeiah on 2008-10-28
launch nvidia-settings with sudo, and it should save your changes
```

sudo nvidia-settings
```

for some reason nvidia-settings never tells you that it wont save settings without admin rights

---

### Post by 289Shelby on 2008-10-28
No joy. As soon as I restart X it drops back to 1680x1050.

---

### Post by 289Shelby on 2008-11-06
I've managed to get this sorted now. What I had to do was edit the file:

```


/usr/share/applications/kde/display.desktop

and comment out the "NoDisplay=True" option


```

This allowed me to right click on the Desktop-> Configure Desktop -> Display and then select "Apply settings on KDE startup"

With that done the correct resolution held.

---

