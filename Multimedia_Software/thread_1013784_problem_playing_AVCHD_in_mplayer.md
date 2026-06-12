---
title: "problem playing AVCHD in mplayer"
date: 2008-12-17
forum: Multimedia Software
---

### Post by uberdonkey5 on 2008-12-17
Hi, would like to know what I am doing wrong. Though I've reverted to windows to edit AVCHD, I would like to play this format in linux.

I have followed these instructions:
[http://blog.mymediasystem.net/avchd/the-playback-avchd-howto-with-mplayer/](http://blog.mymediasystem.net/avchd/the-playback-avchd-howto-with-mplayer/)

but come up with this error when I try to play mplayer (from the terminal).
I type:

mplayer -demuxer lavf -ao sdl -vo xv -lavdopts threads=3:fast:skiploopfilter=all 00001.MTS

and it responds with:

MPlayer dev-SVN-r28159-4.2.3 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Playing 00001.MTS.
libavformat file format detected.
LAVF: Program 1 
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [H264]  1920x1080  0bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
No such audio driver 'sdl'
Could not open/initialize audio device -> no sound.
Audio: no sound
Video: no video


any ideas? I guess I am missing something, like a driver, but not sure what I should be doing. Any help useful
thanks

---

### Post by xzero1 on 2008-12-17
Try 'mplayer 00001.MTS'  (all defaults). You may be forcing an option incompatible with your system.  If it works experiment with the other options you may require.

---

### Post by uberdonkey5 on 2008-12-17
oops I feel so ashamed! Thankyou very much, it did work (though sound didn't sync, but that is issue that always seems to be happening with AVCHD).

---

### Post by jtappin on 2008-12-19
When I try this with the medibuntu mplayer for intrepid with default options, I get an error that it doesn't know the frame rate. If I give it a frame rate (-fps 29.97) then it plays a corrupt version of the file for a bit, then segfaults. (I don't have the detailed error report here now).

One question I have before I go any further is:
Does mplayer have problems trying to play video streams with a larger image size than the screen (in this case video 1920x1080, screen 1280x1024)?

---

### Post by uberdonkey5 on 2008-12-19
My screen resolution is 1140 x 900 and it seems to play high definition vid of 1920 x 1080. Afraid can't help you more than this.

---

