---
title: "Problem with mplayer/gxine"
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by WanderingKnight on 2007-04-29
I'm using Ubuntu Feisty 7.04

I get this error when trying to play a simple xvid encoded .avi file with mplayer:

> Error opening/initializing the selected video_out (-vo) device

Now, I've tried a couple of -vo via command line, but got only sound (sometimes corrupted) and no video.

When using gxine, the player doesn't show a thing and fast-forwards the file till the end.

What should I do?

---

### Post by 4llf0rn0t on 2007-04-30
ive tried this (using terminal):

mplayer -vo xv filename.avi 
-------------------------------------------snippet ----------------------------------------------------------------------
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 96.0 kbit/6.25% (ratio: 12000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 524 x 212 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.47:1 - prescaling to correct movie aspect.
**VO: [xv] 524x212 => 524x212 Planar YV12**

---

