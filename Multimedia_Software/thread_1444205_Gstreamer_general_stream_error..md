---
title: "Gstreamer general stream error."
date: 2010-04-01
forum: Multimedia Software
---

### Post by John.Barner on 2010-04-01
Greetings,

I am having problems playing a MKV file with Totem. The movie plays for a few seconds and then I get a "general stream error" (see attached screenshot). When run from the terminal, Totem gives the following error.

```
** Message: Error: GStreamer encountered a general stream error.
matroska-demux.c(5075): gst_matroska_demux_loop (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin20/GstMatroskaDemux:matroskademux0:
stream stopped, reason error
```

The video codec is H264, with MPEG-4 AAC audio. I have followed the stickied [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683"), with no success. I have a feeling this is an audio issue, as another file with MPEG-4 AAC audio also refuses to play after a few seconds. I have a similar file with Vorbis audio that has no problems. Any suggestions?

---

### Post by no2498 on 2010-04-01
open a terminal type smplayer
it will tell you how to install it
ive been all over looking for good help with mplayer
open all files the same way just x out of them after they tre to play leave the down load folder open
click and open folder right click open with smplayer
you should be able to see them now

hope this helps

---

