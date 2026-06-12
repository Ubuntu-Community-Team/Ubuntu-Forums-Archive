---
title: "problems playing .mkv videos."
date: 2008-08-22
forum: Multimedia Software
---

### Post by SmartRutter on 2008-08-22
The codecs of the particular .mkv that i'm trying to play:
Video: H264 (1024x576, 24fps)
Audio: Vorbis (128kbps bitrate)

Whenever i try playing it with vlc, the video runs too slowly to even possibly view it.  If i use Totem instead, the video runs somewhat better, however still pretty poorly.  Finally, i try xine-ui, the video runs perfectly, but... no sound will play whatever i do. :(  With the previous two programs, the sound will play fine though. :confused:

Any ideas on how to fix this?

---

### Post by lift28 on 2008-08-23
try mplayer
this includes dual cpu enable
```
mplayer -fs -zoom -quiet -vo xv -monitoraspect 16:9 -lavdopts threads=2:fast:skiploopfilter=all -sws 0 movie.mkv
```
on my box it will do all 720 and most 1080

3ghz hyper thread
2 gig of ram
gforce 7600 gs

---

### Post by SmartRutter on 2008-08-24
Thanks, mplayer seems to work well enough.

Time to sit back an enjoy a good video... :)

---

### Post by smoothcne on 2008-10-29
> **lift28 said:**
> try mplayer
this includes dual cpu enable
```
mplayer -fs -zoom -quiet -vo xv -monitoraspect 16:9 -lavdopts threads=2:fast:skiploopfilter=all -sws 0 movie.mkv
```
on my box it will do all 720 and most 1080

3ghz hyper thread
2 gig of ram
gforce 7600 gs

Well, I'm slaving over this issue myself, this is what I got when I tried to run your command string, can you help me make this work:

Smooth@Vortex:~/Videos$ mplayer -fs -zoom -quiet -vo xv -monitoraspect 16:9 -lavdopts threads=2:fast:skiploopfilter=all -sws 0 Planet.Earth.Episode.06.Ice.Worlds.mkv 
MPlayer dev-SVN-r27834-4.3.2 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz (Family: 6, Model: 15, Stepping: 11)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
Option msglevel: Unknown suboption 5
Warning unknown option msglevel at line 6
Planet.Earth.Episode.06.Ice.Worlds.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AC3) "English (AC3)", -aid 0, -alang eng
[mkv] Track ID 3: subtitles (S_TEXT/***), -sid 0, -slang eng
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1920x1080  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...


MPlayer interrupted by signal 2 in module: play_audio

Exiting... (Quit)

---

### Post by shirilover on 2008-10-30
It appears that you did not compile mplayer with xv output.
You could try using -vo gl or -vo gl2 instead.
Also, you can see the list of available video outputs:
```

mplayer -vo help

```

---

