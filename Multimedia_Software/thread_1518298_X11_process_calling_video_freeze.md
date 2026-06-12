---
title: "X11 process calling video freeze"
date: 2010-06-26
forum: Multimedia Software
---

### Post by Dysport on 2010-06-26
I have a strange problem on my MythTV PC: From time to time when I watch TV or a video in VLC the picture freezes but the sound will go on. After some time the picture comes back, first with some ugly artifacts in it and then completely. I've found out by letting htop run in the mean time that during these time CPU usage spikes up to a 100%, I also identified the process causing it (see attached screenshot) ```
/usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm:0.Xauth - nolisten tcp vt7"
```but I have no idea what it does or why it behaves that way. Can someone fill my gaps here?

By the way I'm not running Mythbuntu, but Ubuntu (gnome) with a mythback- and -frontend (don't know whether that's relevant though). I have a nVidia graphics card and a dual screen setup.

---

### Post by Dysport on 2010-08-14
bump

---

### Post by no2498 on 2010-08-14
you may try this it comes from the cheese help file faq's


5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.

---

