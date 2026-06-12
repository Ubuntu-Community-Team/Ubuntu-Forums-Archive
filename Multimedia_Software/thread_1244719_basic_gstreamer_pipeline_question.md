---
title: "basic gstreamer pipeline question"
date: 2009-08-19
forum: Multimedia Software
---

### Post by heluani on 2009-08-19
Hi, I'm trying to convert .wav raw audio to .ulaw with gstreamer. I grab one of the Alsa sample audio files:
```
gst-launch filesrc location = Front_Right.wav ! wavparse ! audioconvert ! alsasink
```
and that plays the file.
next we can try something like
```
gst-launch filesrc location = Front_Right.wav ! wavparse ! mulawenc ! mulawdec ! alsasink
```
And that plays the file, 
but if I try 
```
gst-launch filesrc location = Front_Right.wav ! wavparse ! mulawenc ! filesink location = file.ulaw
``` 
and then ```
$gst-launch filesrc location = file.ulaw ! mulawdec ! alsasink
Setting pipeline to PAUSED ...
Pipeline is PREROLLING ...
ERROR: from element /GstPipeline:pipeline0/GstFileSrc:filesrc0: Internal data flow error.
Additional debug info:
gstbasesrc.c(2378): gst_base_src_loop (): /GstPipeline:pipeline0/GstFileSrc:filesrc0:
streaming task paused, reason not-negotiated (-4)
ERROR: pipeline doesn't want to preroll.
Setting pipeline to NULL ...
Freeing pipeline ...
```
what am I missing?

Thanks, 

R.

---

