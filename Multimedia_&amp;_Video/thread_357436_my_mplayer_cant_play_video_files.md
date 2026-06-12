---
title: "my mplayer cant play video files"
date: 2007-02-09
forum: Multimedia &amp; Video
---

### Post by nemanaldin on 2007-02-09
hi 
i cant see video files with mplayer but i can hear mp3 files 
when i run video files it give this error:
nemanaldin@nemanaldin:~$ mplayer -vf mualli*.avi
MPlayer 1.0rc1-4.0.3 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3000+ (Family: 15, Model: 47, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2
Option vf: muallim 2.avi doesn't exist.
Error parsing option on the command line: -vf
nemanaldin@nemanaldin:~$ mplayer mualli*.avi
MPlayer 1.0rc1-4.0.3 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3000+ (Family: 15, Model: 47, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2

Playing muallim 2.avi.
AVI file format detected.
VIDEO:  [cvid]  640x480  24bpp  29.970 fps  20140.7 kbps (2458.6 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffcvid] vfm: ffmpeg (Cinepak Video (native codec))
==========================================================================
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 1411.2 kbit/100.00% (ratio: 176400->176400)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.

FATAL: Could not initialize video filters (-vf) or video output (-vo).

Can't restore text mode: Invalid argument

Exiting... (End of file)
plz help me
thanks

---

### Post by nemanaldin on 2007-02-11
hi
no one can help????
thanks

---

### Post by nemanaldin on 2007-02-11
hi
no one can help????
thanks

---

### Post by tbroderick on 2007-02-11
Try using the video output switch or no -vf.

```
mplayer file.avi
```

```
mplayer -vo gl file.avi
```

Change gl to whatever one works like xv, x11, gl2.

---

### Post by nemanaldin on 2007-02-12
hi 
i test all -vo xv , x11 ,...
but it say that exist error in opening or installing
plz help me

---

