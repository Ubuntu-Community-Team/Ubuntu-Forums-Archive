---
title: "Tv-out problems"
date: 2008-05-01
forum: Mythbuntu
---

### Post by Narreh on 2008-05-01
I've tried serval editions of the Mythbuntu release both 7.10 and 8.04 and I seem to get the same problem with the TV-out, all i get on my TV is a flimmering image going back and fourth. I''m kinda newbish when it comes to Linux, I've also tried different cables to get the TV-out working and on my windows machine i've got picture.

I'v got an AMD 2000+
1GB RAM
Geforce 3 Ti200 128MB (TV-out)

Anyone got any idéas?

---

### Post by Narreh on 2008-05-01
I seem to get problems whatever I do, Now I installed the 8.04 version and it seems like the mouse and keyboard is delayed, cannot doubleclosk due to delay with pressing buttons and moving mouse, Its like I can use a button and then theres a 0,5seconds delay until i can do anything else. so the mouse kinda "lags" and same with keyboard.

Any ideas?

---

### Post by stronzo on 2008-05-01
your flickering problem may be related to Pal / NTSC settings.
open your "/etc/X11/xorg.conf" with an editor an add the following line to the "device" section (where your graphiccard is listed):

Option          "TVStandard" "PAL-B"

PAL-B should be set by you depending on your country, it can also be NTSC, PAL-I etc.

This is my Device Section:

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
        Option          "TVStandard" "PAL-B"
EndSection

---

