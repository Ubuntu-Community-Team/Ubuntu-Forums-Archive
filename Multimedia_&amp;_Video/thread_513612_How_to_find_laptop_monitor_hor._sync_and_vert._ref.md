---
title: "How to find laptop monitor hor. sync and vert. refresh rates"
date: 2007-07-30
forum: Multimedia &amp; Video
---

### Post by blingboi on 2007-07-30
hello guys, new feisty fawn user here and really love the os so far(still playing around though).

my question is, how do I find out my laptop monitors refresh rates
my laptop is a compaq presario v4000t(mobility x700 pro)(pentium-m 1.7)

i looked at my repair manual but can not find the horizontal sync and vertical refresh rates...

my original problem was that i could not get a resolution above 800x600 and the screen looked really messed up

i didnt want to install the proprietary driver because it would not kick me into screensaver mode or turn off my monitor(it would just black screen out)

so this time i edited my xorg.conf file

ORIGINAL=========
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection
===============

EDITED==========
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-72
        VertRefresh     43-60
EndSection
===============

then i added "1280x800"(my native resolution) to the screen section of the org.conf
i rebooted x server and bam, my native resolution and i can go into screensaver mode and my monitor can turn off if i set it to

my question was about the horizontal sync and vertical refresh rates, im afraid even though everything is working fine, it might blow up my laptop monitor later

how can i go about finding the actual settings? thankers

---

### Post by MrHippocampus on 2007-07-30
You shouldn't have to worry, most modern displays will just say "Input not supported" or something similar (or just a black screen) if you try and send it a signal with a too high Hz/resolution. If its displaying an image then everything should be ok.

---

### Post by blingboi on 2007-07-30
hey thanks mr

---

