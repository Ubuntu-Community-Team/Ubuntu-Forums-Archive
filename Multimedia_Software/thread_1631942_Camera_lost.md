---
title: "Camera lost"
date: 2010-11-27
forum: Multimedia Software
---

### Post by WilsonMESS on 2010-11-27
Previously I have taken photos using cheese, and the camera on my ASUS 1005PE worked, but today when I open cheese, it didn't respond, so I killed the process. After that, I reopened cheese and it shows that "no device found". According to its help file, I opened gstreamer-properties, and I found this when I execute that command in terminal:
```
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /GstPipeline:pipeline0/GstV4lSrc:v4lsrc1]

```In the video tab, I found both "video for linux"(v4l and v4l2) not working (with a message indicates "device "dev/video0" does not exist"), so I wonder what happened. There is one big change recently: I changed system language and time format in ubuntu from Chinese to English, but I don't think that's the case. Is there any way to solve this? Thanks!

P.S.: I know that mic on EeePC never works, but is there any solution? Kind regards.

---

### Post by no2498 on 2010-11-28
try this it helps some times

gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1


ive had to do it 10 times in/on 10.04

---

