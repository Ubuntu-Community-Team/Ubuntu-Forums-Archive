---
title: "Video Playback Issues"
date: 2010-11-24
forum: Multimedia Software
---

### Post by Qbert on 2010-11-24
I have two media servers I'm running 10.10 on.  They're very similar specs wise.  They're both using 45w AMD CPUs with 2GB of memory.  The one big difference is one has a nvidia gpu while the other is ATI.  At any rate, the ATI machine runs great and I don't have any trouble with it, but the nvidia machines has video playback issues.  Movies like to stutter quite a bit and I see lines during playback like where the picture isn't rendered correctly, so you see a line.  I'm wondering if there's anything I could look at to get the second box working correctly?  Like I said they're very similar and I installed them the same.  I mostly use VLC for playback, but I've tried other software like smplayer or movie player, but they offered the same results.  Thanks for any help.

---

### Post by no2498 on 2010-11-25
this may or may not help with nvidia

it comes from the program cheese


The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    

a computer restart 


you can reset it back the same way


hope it helps you

---

