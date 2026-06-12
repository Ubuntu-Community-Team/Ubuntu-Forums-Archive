---
title: "No Audio"
date: 2008-12-13
forum: Mythbuntu
---

### Post by jlr4u on 2008-12-13
I loaded an old machine with mythtv and can not seem to get the audio working.  It seems I have a codec problem. The audio works fine on an avi file.   I loaded ivtv and created a test file which also does not have audio, but the video is fine. Can some review the mplayer log give me some suggestions?

```
Playing /tmp/test_capture.mpg.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  8000.0 kbps (1000.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 224.0 kbit/14.58% (ratio: 28000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] Failed to connect to server: Connection refused
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12
Cannot sync MAD frame: -0.038 ct: -0.150  46/ 46 20%  4%  2.1% 1 0
Cannot sync MAD frame
Cannot sync MAD frame: -0.039 ct: -0.153  47/ 47 20%  4%  2.1% 1 0
```

---

