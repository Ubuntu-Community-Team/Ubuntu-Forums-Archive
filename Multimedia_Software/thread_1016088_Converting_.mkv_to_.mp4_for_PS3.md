---
title: "Converting .mkv to .mp4 for PS3"
date: 2008-12-19
forum: Multimedia Software
---

### Post by dr0pp on 2008-12-19
Hey everyone, since I can't post in [this](http://ubuntuforums.org/showthread.php?t=548547) thread, I had to make a new one in reference to it.

I'm trying to use the bash script in the third page of that thread, and it worked fine the first two files I tried it on, but now when I get to the aac encoding step, mplayer doesn't play the .ac3 file so I never get my new .aac file.

Anyways, here's the output of terminal:
```
*************************************************************
*                                                           *
*  Nero AAC Encoder                                         *
*  Copyright 2008 Nero AG                                   *
*  All Rights Reserved Worldwide                            *
*                                                           *
*  Package build date: Sep 17 2008                          *
*  Package version:    1.3.3.0                              *
*                                                           *
*  See -help for a complete list of available parameters.   *
*                                                           *
*************************************************************

MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: AMD Phenom(tm) 9600 Quad-Core Processor (Family: 16, Model: 2, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
115 audio & 237 video codecs
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing audio.ac3.
libavformat file format detected.
[mpeg @ 0xc16830]Could not find codec parameters (Audio: mp2, 384 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Audio: mp2, 160 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Audio: mp2, 192 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Audio: mp2, 160 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Audio: mp2, 256 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Audio: mp2, 64 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Audio: mp2, 80 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Video: mpeg1video, 1099x3206, 42126 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Audio: mp2, 64 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Audio: mp2, 448 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Audio: mp2, 128 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Video: mpeg2video)
[mpeg @ 0xc16830]Could not find codec parameters (Audio: mp2, 128 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Video: mpeg1video, 3229x2898, 85917 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Audio: mp2, 128 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Audio: mp2, 160 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Video: mpeg2video)
[mpeg @ 0xc16830]Could not find codec parameters (Video: mpeg1video, 1705x1416, 90062 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Audio: mp2, 224 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Audio: mp2, 32 kb/s)
LAVF_header: av_find_stream_info() failed
libavformat file format detected.
[mpeg @ 0xc16830]Could not find codec parameters (Audio: mp2, 384 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Audio: mp2, 160 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Audio: mp2, 192 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Audio: mp2, 160 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Audio: mp2, 256 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Audio: mp2, 64 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Audio: mp2, 80 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Video: mpeg1video, 1099x3206, 42126 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Audio: mp2, 64 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Audio: mp2, 448 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Audio: mp2, 128 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Video: mpeg2video)
[mpeg @ 0xc16830]Could not find codec parameters (Audio: mp2, 128 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Video: mpeg1video, 3229x2898, 85917 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Audio: mp2, 128 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Audio: mp2, 160 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Video: mpeg2video)
[mpeg @ 0xc16830]Could not find codec parameters (Video: mpeg1video, 1705x1416, 90062 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Audio: mp2, 224 kb/s)
[mpeg @ 0xc16830]Could not find codec parameters (Audio: mp2, 32 kb/s)
LAVF_header: av_find_stream_info() failed


Exiting... (End of file)
```

Any ideas why mplayer won't play the .ac3? Thanks~

---

