---
title: "mplayer:poor performance in Fullscreen mode"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by mdky on 2007-05-07
My PC: Amd64 3000+/Ati x1600/1G Ram/160G HD
System:Ubuntu 7.04 Feisty  32bit version
Video Driver: xorg-driver-fglrx_8.36.5-1_i386
Mplayer version: MPlayer dev-SVN-r23238-4.1.2
video output method( as -vo param ) : xv, gl, gl2 all the same

Here is the problem.When I playing a movie in mplayer fullscreen mode, I find that the picture looks *Choppy?*
see below:
[[IMG]http://lh3.google.com/image/deadivan/Rj6xLqUKJiI/AAAAAAAAAAw/TvSY6qlxdB0/s400/video.jpg[/IMG]]("http://picasaweb.google.com/deadivan/UbuntuAtiVideo/photo#5061677845106533922")
but in windows mode, it looks good
what should i deal with it ?
> mplayer output
MPlayer dev-SVN-r23238-4.1.2 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3000+ (Family: 15, Model: 44, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2
Cannot load bitmap font: ~/.mplayer/subfont.ttf

Playing /media/***.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AC3), -aid 0, -alang und
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  720x480  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 6 ch, s16le, 448.0 kbit/9.72% (ratio: 56000->576000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [oss] 48000Hz 6ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.80:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 864x480 Planar YV12 
A:   1.6 V:   1.6 A-V:  0.009 ct:  0.007  39/ 39 50%  8%  1.8% 0 0 
Exiting... (Quit)

---

### Post by mdky on 2007-05-07
update: mplayer  window mode is choppy too...
don't have enough fill rate?

---

### Post by r3bol on 2007-05-07
I've had excellent results with Kaffeine and xine on other distros (even full screen).

---

