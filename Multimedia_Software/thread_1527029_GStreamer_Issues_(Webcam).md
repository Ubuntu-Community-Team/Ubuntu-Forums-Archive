---
title: "GStreamer Issues (Webcam)"
date: 2010-07-08
forum: Multimedia Software
---

### Post by muliganstew on 2010-07-08
So after looking around I've found numerous threads about similar topics, but my problem is a little bit different so I thought I would just start a new thread.  
  I'll provide a general narrative of what has happened over the past few days in case it helps deciphering what happened.
  I'm trying to set up my webcam on my Dell Inspiron 700m in which I have 10.04 installed.  However, whenever I open any application that uses the webcam (C250 Logitech) it crashes my entire system (Some text flashes but it is too quick to read and then my screen becomes black).  I tried Skype, Cheese, Camorama, and testing from GStreamer-properties, and all of them had the same result.
   However, using:

```
gst-launch v4l2src ! ffmpegcolorspace ! ximagesink
```

I was able to get a stream working.  Also
  When I ran gstreamer-properties I was given:

```
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
```

So I naturally thought I was missing some packages.  After digging around it was suggested that I install the gstreamer0.10-ffmpeg, gstreamer0.10-plugins-bad, gstreamer0.10-plugins-ugly.  Once doing this I was able to get my webcam working (except with camorama).  However, the skipping unavailable plugins messages continued to come up.

Furthermore, the problem didn't permanently go away either.  I tried using my external monitor while using my webcam and not only did it crash my computer, but also the webcam did not work upon reboot (I've had issues with my laptop working with this monitor prior, the screen flickers).  I had to completely remove, install, and reboot using the above packages mentioned to get it working again.

Although everything is working fine at the moment, I'm still really perplexed as what the heck really happened.  If anyone could shed some light on some possibilities (I'm still relatively a linux noob) so that can permanently stop this problem it would be much appreciated.

---

### Post by NoBugs! on 2010-07-09
Can you get a crash report when this happens?
Using [Apport]("https://wiki.ubuntu.com/Apport"), you may be able to track where this is happening and see if a bug report has been filed.

---

### Post by no2498 on 2010-07-09
as for the gstreamer-properties


gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'



we all get them or i have anyway from 710, 804 and on 910

glad you got the cam working

---

