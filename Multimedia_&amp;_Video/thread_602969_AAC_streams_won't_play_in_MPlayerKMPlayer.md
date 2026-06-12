---
title: "AAC streams won't play in MPlayer/KMPlayer"
date: 2007-11-04
forum: Multimedia &amp; Video
---

### Post by tghe-retford on 2007-11-04
I am trying to get an AAC stream to work from Radio Swiss Jazz using KMPlayer with the MPlayer engine (Xine won't play Realaudio without serious distortion to the sound on my PC for some odd reason - its like listening to a robot and it cuts out after a minute, whereas MPlayer will play almost anything I throw at it). However, when I try to play an AAC stream using KMPlayer or MPlayer, I just get this:

```
Resolving stream-3.ssatr.ch for AF_INET...
Connecting to server stream-3.ssatr.ch[91.121.1.13]: 80...
Cache size set to 256 KBytes
Cache fill:  3.12% (8192 bytes) 
```
(For your information, the URL is [http://stream-3.ssatr.ch:80/rsj/aacp32](http://stream-3.ssatr.ch:80/rsj/aacp32))

The buffer in KMPlayer stays at 0%.

I can use the Xine player to play AAC's but it means having to switch engine every single time, and I use KMPlayer with the MPlayer engine for my MP3, WIndows Media and Realaudio streams. I do voluntary work for a well known UK Internet radio software manufacturer and I could do with keeping everything to one media player (KMPlayer).

Is there a way to get AAC's to play using MPlayer?

Thanks in advance.

---

### Post by daengbo on 2007-11-04
My cache hung for almost a minute, but the song eventually opened using the standard mplayer from Ubuntu on the command line. You will need to make sure you have [faac]("apt:faac") / [faad]("apt:faad") installed in order to decode.

> danielbo2@danielbo-laptop:~$ mplayer [http://stream-3.ssatr.ch/rsj/aacp32](http://stream-3.ssatr.ch/rsj/aacp32)
MPlayer 2:1.0~rc1-0ubuntu13 (C) 2000-2006 MPlayer Team
CPU: Mobile AMD Sempron(tm) Processor 2800+ (Family: 15, Model: 28, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing [http://stream-3.ssatr.ch/rsj/aacp32](http://stream-3.ssatr.ch/rsj/aacp32).
Resolving stream-3.ssatr.ch for AF_INET6...
Couldn't resolve name for AF_INET6: stream-3.ssatr.ch
Resolving stream-3.ssatr.ch for AF_INET...
Connecting to server stream-3.ssatr.ch[91.121.1.13]: 80...
Cache size set to 320 KBytes
Cache fill:  0.00% (0 bytes)   
ICY Info: StreamTitle='Charly Antolini Jazz Power - Monday';
Cache fill: 12.50% (40960 bytes)   
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll
AAC file format detected.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio) decoder)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   5.9 (05.8) of 0.0 (unknown)  3.2% 76% 

MPlayer interrupted by signal 2 in module: play_audio


Best of luck.

---

### Post by tghe-retford on 2007-11-05
Thanks for that. It did work using MPlayer through the command line and using the MPlayer GUI after a minute of caching.

However, KMPlayer now sticks at 0.00%

```
Resolving stream-3.ssatr.ch for AF_INET...
Connecting to server stream-3.ssatr.ch[91.121.1.13]: 80...
Cache size set to 256 KBytes
Cache fill:  0.00% (0 bytes)
```

Leaving it for a few minutes has this show:

```
ID_VIDEO_ID=0
libavformat file format detected.
```

But still no sound, and no movement since.

It is weird because KMPlayer uses the same MPlayer engine that worked when I used MPlayer on the command line and the MPlayer GUI.

MPlayer:
```
MPlayer 2:1.0~rc1-0ubuntu13 (C) 2000-2006 MPlayer Team
CPU: AMD Sempron(tm) Processor 2800+ (Family: 15, Model: 44, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
```
KMPlayer:
```
MPlayer 2:1.0~rc1-0ubuntu13 (C) 2000-2006 MPlayer Team
CPU: AMD Sempron(tm) Processor 2800+ (Family: 15, Model: 44, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
```

:confused:

Worth submitting a bug report?

---

