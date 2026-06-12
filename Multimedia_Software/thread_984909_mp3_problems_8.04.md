---
title: "mp3 problems 8.04"
date: 2008-11-17
forum: Multimedia Software
---

### Post by ItalOz on 2008-11-17
Hi,
I installed recently hardy 8.04 and I can't play mp3s anymore.
I was playing mp3s with ubuntu 7.10 using audacious without problems.
The sound card works because I can correctly hear the login sound.
I've medibuntu enabled. 

When I try to lunch the mp3 from terminal
e.g.
```
totem-gstreamer file.mp3
```
I get
```
** Message: Error: Failed to connect stream: Invalid argument
pulsesink.c(411): gst_pulsesink_prepare (): /play/visbin/abin/audiosinkbin/audio-sink/bin6/autoaudiosink1/autoaudiosink1-actual-sink-pulse


(totem-gstreamer:6491): GStreamer-CRITICAL **: gst_object_unref: assertion `object != NULL' failed
```

I've followed the [[COLOR="Blue"]_Comprehensive Multimedia & Video Howto_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683") and nothing. I've an AMD64.

It might be the case the I need to purge the programs downloaded from the medibuntu but I don't know how to do it.

Any suggestions?

Hey I just found out I can play WMA files?!? This is absurd!

[SOLVED]

I un-installed through synaptic everything related witt mp3 that could be a codec and then I reinstalled following the procedure in the "how to" guide

---

