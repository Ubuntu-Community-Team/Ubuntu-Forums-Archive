---
title: "unable to play any video"
date: 2007-12-20
forum: Multimedia &amp; Video
---

### Post by saurabh kakkar on 2007-12-20
hi
i m unable to play any video even the Experience ubuntu,ogg either in Mpalyer nd totem 
plz help me i have installed all the restricted packages but all in vein

---

### Post by Nano Geek on 2007-12-20
Run this in the terminal and tell me what it says or does. ```
totem /usr/share/example-content/Experience\ ubuntu.ogg 
```

---

### Post by saurabh kakkar on 2007-12-21
> **asjdfwejqrfjcvm msz34rq33 said:**
> Run this in the terminal and tell me what it says or does. ```
totem /usr/share/example-content/Experience\ ubuntu.ogg 
```

I m only able to hear sound no video :(

---

### Post by Richard Perry on 2007-12-21
I have a similar problem.  I have followed the sticky for for installing multimedia.  I can watch videos on abc.com and cnn.com, but when I go to  BBC-1, I get only sound, no video.  When mplayer  comes up I get this message, "Error opening/initializing the selected video-out (-vo) device."

I tried running the totem command in terminal as suggested by the first response.  Nelson Mandela came through loud and clear.

Should I be using totem instead of mplayer?  How do I do that?

---

### Post by Armadillo Kilr on 2007-12-21
i actually was able to watch it

---

### Post by Nano Geek on 2007-12-21
Run **gstreamer-properties** in the terminal, go to the **Video** tab, and take a screenshot of the window.

---

### Post by saurabh kakkar on 2007-12-21
> **asjdfwejqrfjcvm msz34rq33 said:**
> Run **gstreamer-properties** in the terminal, go to the **Video** tab, and take a screenshot of the window.

Thanks sir u made my day :) i solved problem by setting Video output No Xv

By the way i m getting this output 
```

saurabh@ubuntu:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /pipeline3/v4lsrc4]
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /pipeline5/v4lsrc6]

```

---

### Post by Nano Geek on 2007-12-21
> **saurabh kakkar said:**
> Thanks sir u made my day :) i solved problem by setting Video output No Xv

By the way i m getting this output 
```

saurabh@ubuntu:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /pipeline3/v4lsrc4]
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /pipeline5/v4lsrc6]

```I'm glad you fixed it.

As long as it's working properly, I would ignore that error.

Merry Christmas!

---

