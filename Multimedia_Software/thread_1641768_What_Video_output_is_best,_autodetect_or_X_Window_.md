---
title: "What Video output is best, autodetect or X Window etc"
date: 2010-12-09
forum: Multimedia Software
---

### Post by ricky222 on 2010-12-09
Hi, in the control centre under multi media selector for configuring GStreamer it has Autodetect and two other setting, X Window System (No Xv) and X Window System (X11/XShm/Xv) etc.

When I test the X Window System (No Xv) the test card in full screen is far better then autodetect, should I keep this setting, the reason I ask is I can't notice the difference when watching video, thanks.

---

### Post by no2498 on 2010-12-09
this comes from the program cheese webcam booth's faq's

&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.

---

