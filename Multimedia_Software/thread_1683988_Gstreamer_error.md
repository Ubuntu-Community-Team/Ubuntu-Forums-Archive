---
title: "Gstreamer error"
date: 2011-02-08
forum: Multimedia Software
---

### Post by mrfsrf on 2011-02-08
Hi,

I'm having some problems while trying to play swf files

here is the snippet from terminal

luka@luka-laptop:~/Downloads$ gst-launch filesrc location=/home/luka/Downloads/movie.swf !  decodebin  !  ffmpegcolorspace  ! xvimagesink
Setting pipeline to PAUSED ...
Pipeline is PREROLLING ...
ERROR: from element /GstPipeline:pipeline0/GstDecodeBin:decodebin0/ffdemux_swf:ffdemux_swf0: GStreamer encountered a general supporting library error.
Additional debug info:
gstffmpegdemux.c(1243): gst_ffmpegdemux_open (): /GstPipeline:pipeline0/GstDecodeBin:decodebin0/ffdemux_swf:ffdemux_swf0:
Input/output error
ERROR: pipeline doesn't want to preroll.
Setting pipeline to NULL ...
Freeing pipeline ...
luka@luka-laptop:~/Downloads$ 

anyone knows a workaround? thx!

---

