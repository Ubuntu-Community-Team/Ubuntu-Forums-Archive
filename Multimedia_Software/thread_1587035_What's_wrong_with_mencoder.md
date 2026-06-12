---
title: "What's wrong with mencoder?"
date: 2010-10-02
forum: Multimedia Software
---

### Post by SpecialNeeds on 2010-10-02
I'm trying to convert a video from .ogv to .avi I use this statement:
```
mencoder video.ogv -oac mp3lame -ovc lavc -o video.avi
```
and get this message.
```
MEncoder SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
success: format: 0  data: 0x0 - 0x1b51e0
Ogg stream 0 is of an unknown type
[Ogg] stream 1: video (Theora v3.2.1), -vid 0
[Ogg] stream 2: audio (Vorbis), -aid 0
Ogg file format detected.
VIDEO:  [theo]  1360x768  24bpp  20.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:18  fourcc:0x6F656874  size:1360x768  fps:20.000  ftime:=0.0500
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22500 Hz, 1 ch, s16le, 90.0 kbit/25.00% (ratio: 11248->45000)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x9c7ceb0]Missing extradata!
Could not open codec.
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
VDec: vo config request - 1360 x 768 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
videocodec: libavcodec (1360x768 fourcc=34504d46 [FMP4])
Selected video codec: [theora] vfm: theora (Theora (free, reworked VP3))
==========================================================================
Cannot set LAME options, check bitrate/samplerate, some very low bitrates
(<32) need lower samplerates (i.e. -srate 8000).
If everything else fails, try a preset.
Exiting...

```
Thanks for the answers.

---

### Post by andrew.46 on 2010-10-08
Hi Special,

Perhaps try something like the following:

```

mencoder video.ogv \
        -oac mp3lame -lameopts preset=standard \
        -ovc lavc -o video.avi

```

If this conquers the audio problem you might have to look at beefing up the video options a little too.

Andrew

---

