---
title: "How to use Web Cam"
date: 2010-11-28
forum: Multimedia Software
---

### Post by borgward on 2010-11-28
How do I use web cam. Ubuntu 10.04 LTS. Dell Inspiron 1520. What software package do I need to download for it?

---

### Post by matt_symes on 2010-11-28
Hi

Download cheese.

Kind regards

---

### Post by borgward on 2010-11-28
Thanks. That was fast.

I have it working now. I am presently using the web cam built into my laptop. motion is blurred. Is that because I am using the built in web cam or because of my processor speed. This laptop is only running the Pentium Dual Core (not the core II Duo) 1.73 GHz 2GB Ram

---

### Post by matt_symes on 2010-11-28
Hi

> Is that because I am using the built in web cam or because of my processor speed. I have to say i am not sure, it could be either. What's it like at running other video?

> 
Thanks. That was fast.We aim to please :)

Kind regards

---

### Post by no2498 on 2010-11-28
cheese has a nice kelp file look in the faq's

The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    


thats from cheese

---

### Post by borgward on 2010-11-30
I ran command, but no change:

xyz@1520:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'

Multimedia Systems Selector window came up. It is now set on Video tab as:

Default Output
X Window System: (X11/XShm/Xv) 

Device: Default - the other options are Intel Textured Video, and Intel Video Overlay

Pipeline: xvimagesink

Default Input
Plugin: Video for Linux (v41)  or 1? is that a 1 or a L?

Device: None

Pipeline: v4lsrc

The Preference window shows:

Device: Laptop Integrated Webcam (dev/video0)

Resolution: 1600 X 1200

Cheese becomes extremely slow when I begin recording.

Cheese -> Recording

It actually comes to a stop, and ten starts and stops over and over.

---

### Post by no2498 on 2010-12-01
hope you use the 32 bit sys
this is only for the 32 bit not 64 bit

wxcam 

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)


if you can use it pin it to the top panel
i can start making a movie in 3 sec

---

### Post by borgward on 2010-12-01
Quoting myself "This laptop is only running the Pentium Dual Core (not the core II Duo) 1.73 GHz 2GB Ram" That processor is 64 bit.

Are there any other programs that will run the web cam with Ubuntu? Has anybody else been able to use Cheese on a Dell 1520 laptop?

---

### Post by matt_symes on 2010-12-01
Hi

Sorry your having so many problems with cheese. It has worked fine for me. However, have a look at this page. It might help.

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

EDIT: Does lowering the recording resolution help?

Kind regards

---

