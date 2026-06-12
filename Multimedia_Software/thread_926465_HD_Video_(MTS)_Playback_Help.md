---
title: "HD Video (MTS) Playback Help"
date: 2008-09-22
forum: Multimedia Software
---

### Post by ddixonr on 2008-09-22
I read tons of posts, but most of them seem to try and transcode mts files into avi to play them. Well I have had no luck with m2tsavi (or whatever it is called). The quality is terrible after it finishes.

Running mplayer from a terminal plays the audio, but not the video. Here is the output:
```
~/Videos$ mplayer 00007.MTS
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Genuine Intel(R) CPU           T2050  @ 1.60GHz (Family: 6, Model: 14, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 00007.MTS.
TS file format detected.
VIDEO H264(pid=4113) AUDIO A52(pid=4352) NO SUBS (yet)!  PROGRAM N. 1
FPS not specified in the header or invalid, use the -fps option.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 256.0 kbit/16.67% (ratio: 32000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [pulse] Failed to connect to server: Invalid argument
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
a52: CRC check failed!  8 (18:18.7)  1.1% 
A:  49.0 (48.9) of 1098.8 (18:18.7)  1.1% 

```

Any suggestions?

---

### Post by fubarbundy on 2009-04-01
For the benefit anyone who has come across this question from a search, just do what mplayer suggests! E.g.:

mplayer -fps 50 00001.MTS

---

