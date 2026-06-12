---
title: "mplayer/mencoder audio sync problem"
date: 2009-11-04
forum: Multimedia Software
---

### Post by zackiv31 on 2009-11-04
I just upgraded from Jaunty to Karmic and mplayer now cannot play my H.264 / AVC PCM files correctly.

The audio is out of sync on all of them, and they worked perfectly fine before.

VLC plays them perfectly fine, but I am using mplayer for its encoding (mencoder) and this is a huge problem.


Is anyone else having these types of problems with H.264 + PCM files (or others?)


On play its output is the following:

```

me@me:/media/scratch/untitled$ mplayer movie.mov 
MPlayer UNKNOWN-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing SHASTIMULI.mov.
libavformat file format detected.
[lavf] Audio stream found, -aid 0
[lavf] Video stream found, -vid 1
VIDEO:  [avc1]  1920x1080  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 0.0 kbit/0.00% (ratio: 0->192000)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
[pulse] working around probably broken pause functionality,
        see http://www.pulseaudio.org/ticket/440
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 1920 x 1080 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 1920x1080 => 1920x1080 Planar YV12 
A:   5.7 V:   5.7 A-V:  0.002 ct: -0.218   0/  0 66%  6%  0.1% 4 0 

```

Doesn't have any skipped frames or anything, but when I use mencoder to try to encode it to something else, I get a skipped frame almost every second.

Once again, I did not have these problems prior to the upgrade.

---

