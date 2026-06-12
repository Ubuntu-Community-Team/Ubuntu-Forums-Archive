---
title: "Stuttering video when running at 50Hz."
date: 2010-08-22
forum: Multimedia Software
---

### Post by thecapsaicinkid on 2010-08-22
I'm seeing regular stuttering in PAL video when running at the default 1920x1080 50Hz but not apparent when I use nvidia-settings to switch output to 60Hz. It's most noticeable when the video pans and you can see the video stutter ever half second or so.

Ubuntu 10.04 64bit 
Nvidia driver 195.36.24-0ubuntu1~10.04 
Xorg.conf [http://pastebin.com/fPvnkGAj](http://pastebin.com/fPvnkGAj) 
nvidia-settings cleared

Any ideas?

---

### Post by no2498 on 2010-08-22
you may try this wright down your settings first so you can set it back if needed


5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    
5.2.&#8195;I have a Mac with iSight and a ATI graphics card, and the colors are weird.


      This is a problem with the ATI graphics card, though there is a work around.
      Change the video-output to custom and insert the following: "ffmpegcolorspace !
      video/x-raw-yuv,format=(fourcc)YV12 ! ffmpegcolorspace ! xvimagesink".
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and select custom from the drop down menu.

---

### Post by thecapsaicinkid on 2010-08-22
Hi,

No those aren't applicable.

---

### Post by no2498 on 2010-08-23
this 1 did not help you ? did you try it


5.1.&#8195;The video is sluggish/has a slow response. What can I do?


You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
This means, that your cpu is doing all the work. Change it to "xvimagesink"
("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.



To change the settings, run "gstreamer-properties", click the Video tab
and change the appropriate settings.

---

