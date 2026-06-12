---
title: "flash video slow 10.04 vs. 9.10 old laptop"
date: 2010-08-24
forum: Multimedia Software
---

### Post by gracchus on 2010-08-24
I just upgraded from 9.10 to 10.04 by doing a reformat and fresh install from the cd.  I have an old dell inspiron 1000 with a 2.26ghz centrino and SiS integrated video chipset.  It used to run flash player playing 360p youtube clips in fullscreen very smoothly and better than my windows 7 install but with 10.04 it is doing about 1 frame every 5 sec.  Can anyone suggest some fix before I downgrade to 9.10?

---

### Post by no2498 on 2010-08-25
wright down your setting first so you can change it back if this does not help

5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    


i do hope it helps you

---

