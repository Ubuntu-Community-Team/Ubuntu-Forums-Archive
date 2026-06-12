---
title: "Pixelated playback on desktop recording"
date: 2010-11-24
forum: Multimedia Software
---

### Post by Oven Glove on 2010-11-24
I've been using RecordMyDesktop to do some simple videos (no fancy effects) and when I play them back, they are all jaggedy and pixelated and barely viewable.

If this is an ubuntu problem then I would really appreciate your help on this.

Thanks,
Owen.

---

### Post by no2498 on 2010-11-25
owen try this it helps me
it comes from the program cheese
its a driver thing
i dont know what ubuntu you have or driver's you use
you will most likely need to do a computer restart before it works 

The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    


hope it helps you
btw you can change it back the same way

---

### Post by Oven Glove on 2010-11-26
Doing what you said hasn't changed it. I wish I could show you exactly what it looks like but the attachments don't support videos.

So you know I have an ATI integrated graphics chip and I'm running the latest release of 10.10.

---

