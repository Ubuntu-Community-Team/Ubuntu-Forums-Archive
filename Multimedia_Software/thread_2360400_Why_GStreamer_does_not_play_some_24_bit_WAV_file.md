---
title: "Why GStreamer does not play some 24 bit WAV file?"
date: 2017-05-04
forum: Multimedia Software
---

### Post by dmitriano on 2017-05-04
I tried to play a [sound converted to various formats with sox utility]("http://developernote.com/2017/04/how-to-convert-mp3-to-wav-in-ubuntu/") on KUbuntu 14.04 (and on CentOS 7), using the command provided in my [previous post]("https://ubuntuforums.org/showthread.php?t=2360128"):

gst-launch-1.0 filesrc location=somefile.wav ! wavparse ! alsasink

The following files played fine:
[http://developernote.com/wp-content/uploads/2017/04/incoming.mp3](http://developernote.com/wp-content/uploads/2017/04/incoming.mp3)
[http://developernote.com/wp-content/uploads/2017/04/incoming16.wav](http://developernote.com/wp-content/uploads/2017/04/incoming16.wav)
[http://developernote.com/wp-content/uploads/2017/04/incoming32.wav](http://developernote.com/wp-content/uploads/2017/04/incoming32.wav)

But some 24-bit WAV file [http://developernote.com/wp-content/uploads/2017/04/incoming24.wav](http://developernote.com/wp-content/uploads/2017/04/incoming24.wav) does not:
gst-launch-1.0 filesrc location=incoming24.wav ! wavparse ! alsasink
Setting pipeline to PAUSED ...
Pipeline is PREROLLING ...
ERROR: from element /GstPipeline:pipeline0/GstWavParse:wavparse0: Internal data flow error.
Additional debug info:
gstwavparse.c(2468): gst_wavparse_loop (): /GstPipeline:pipeline0/GstWavParse:wavparse0:
streaming task paused, reason not-negotiated (-4)
ERROR: pipeline doesn't want to preroll.
Setting pipeline to NULL ...
Freeing pipeline ...

also some 24-bit WAV file [http://developernote.com/wp-content/uploads/2017/04/beep.wav](http://developernote.com/wp-content/uploads/2017/04/beep.wav) does not play.

'play' command plays incoming24.wav and beep.wav well on my KUbuntu machine.

The question is how to figure out what files are played well and what files does not? Why GStreamer does not like 24-bit format?

---

### Post by mc4man on 2017-05-04
it (incoming.wav) would playback ok with that command in 16.04 (gst-1.8.x) but not in 14.04 (there I use gst-1.6.x, default is likely earlier.
Maybe find a different command, for example this would work here - 
...... ! wavparse ! pulsesink

---

