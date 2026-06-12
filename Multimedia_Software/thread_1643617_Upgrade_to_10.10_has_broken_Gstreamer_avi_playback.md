---
title: "Upgrade to 10.10 has broken Gstreamer avi playback"
date: 2010-12-12
forum: Multimedia Software
---

### Post by gabe_rosser on 2010-12-12
Hi all,

I upgraded to 10.10 recently (from 10.04).  Just came to play a .avi file using movie player (which previously worked in 10.04) and it no longer plays.  Instead I get the "an error occurred" dialogue box stating "Internal data stream error".

The file plays in VLC, reporting the codec '8 bits grayscale (GREY)'.

I have checked my gstreamer-plugins and I have everything that I believe I need: good, bad, ugly, ffmpeg.  Also have the multiverse packages and w64codecs (I'm on x86_64).

I've tried reinstalling the gstreamer plugins but it doesn't help.

An obvious solution is just to use VLC, BUT I need gstreamer to work because I use Matlab to process videos and it uses the gstreamer libs to import them.

Any ideas please?

Thanks

---

