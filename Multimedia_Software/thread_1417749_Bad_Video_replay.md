---
title: "Bad Video replay"
date: 2010-02-27
forum: Multimedia Software
---

### Post by malel on 2010-02-27
I am trying to play some video pieces from the internet but it does about 3 seconds then stops and starts again . Its very jerky. Some help please


Using Xubuntu 8.04 on a Pentium 4 2Gb ram

---

### Post by no2498 on 2010-02-27
open a terminal type ( gstreamer-properties ) click enter
click video
set the plugin part of the setting to xwindow systems (no xv)
hope this helps

---

### Post by malel on 2010-02-27
Thank you for that but it did not help . Here is what I got


mal@Pentium4:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(463): gst_v4l2_open (): /GstPipeline:pipeline1/GstV4l2Src:v4l2src4:
system error: No such file or directory]
mal@Pentium4:~$

---

