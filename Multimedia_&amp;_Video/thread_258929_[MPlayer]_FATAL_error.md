---
title: "[MPlayer] FATAL error"
date: 2006-09-16
forum: Multimedia &amp; Video
---

### Post by Yoozer on 2006-09-16
This isn't so much a hardware problem as a software one, but V&S seemed like the best place to put it.

Because the Ubuntu mplayer package in the multiverse repository is one version behind the current one ( pre-8 ), I decided to go the somewhat foolhardy compile-it-myself route and downloaded the source distribution (without skin) from MPlayerHQ. I ran ./configure (without supplying any arguments), then make, then make install, all sans incident. Next I grabbed the essential codec bundle and placed its contents in /usr/local/lib/codecs. But whenever I try to play a video file (of any format), I get the following output:



************************************************
mplayer Blabla.avi
MPlayer 1.0pre8-4.0.3 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3000+ (Family: 15, Model: 31, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2


Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.


Playing Blabla.avi.
AVI file format detected.
VIDEO:  [DIV3]  608x256  24bpp  23.976 fps  2225.1 kbps (271.6 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.4.1 (build 2066/release)
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
AC3: 5.1 (3f+2r+lfe)  48000 Hz  384.0 kbit/s
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffdivx] vfm: ffmpeg (FFmpeg DivX ;-) (MS MPEG-4 v3))
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 608 x 256 (preferred colorspace: Planar YV12)


Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDec: vo config request - 608 x 256 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.

FATAL: Could not initialize video filters (-vf) or video output (-vo).

Can't restore text mode: Invalid argument
************************************************



(Ignore the RTC init error, it's not really relevant).

Clearly the issue isn't as trivial as a missing codec, because it identifies the ones used to encode the video just fine. I can't figure out what's causing vout to fail initialization, though, and none of the drivers that a "mplayer -vo help" lists work either. Does anyone have ANY idea how to fix this?

BTW, this is on an otherwise FRESH installation of (the AMD64 version of) Ubuntu 6.06, kernel 2.6.15-26-amd64-generic, so odds are I've simply forgotten some packages, but I wouldn't know which.

Thanks!

---

