---
title: "MPlayer not recognising video in TS file."
date: 2009-05-20
forum: Multimedia Software
---

### Post by davemar on 2009-05-20
I've got a TS video file which contains a HD H.264 coded video stream along with some audio. I would like to play it back using mplayer, but it doesn't pick up on the video, giving this output:
```

MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3200+ (Family: 15, Model: 47, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing abc.ts.
TS file format detected.
NO VIDEO! AUDIO A52(pid=2329) NO SUBS (yet)!  PROGRAM N. 6940
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:37926.8 (10:32:06.7) of 2822.9 (47:02.9)  2.1% 

```

I've tried VLC (v. 0.9.9a) , which does show the video, but so slowly it only shows a frame every few seconds with lots of stalling. I'm not sure what the sound is like though, as I haven't checked that yet. I tried the same file on my other machine with VLC v0.8.6e and it played pretty much the right speed, but with poor audio (the audio is always bad with TS files on this version of VLC).

I would prefer to stick with mplayer if possible, as it tends to be a bit more reliable than VLC.

I'm running Ubuntu version 9.04, so am I asking the trouble with something too new?

---

### Post by xzero1 on 2009-05-20
You probably don't have the required codec(s). See [https://help.ubuntu.com/community/RestrictedFormats.]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by davemar on 2009-05-21
Followed the instructions in that link, and reinstalled mplayer (using Synaptic), but it still doesn't work. I converted the file to a .avi file using avidemux (using the "copy" video option, so presumably not re-encoding the video part) and mplayer does play that, but far too slowly. It gives out lots of errors like this:
```
Too many video packets in the buffer: (108 in 8605544 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
Cannot sync MAD frame

```
The -ni option doesn't help.

I've turned off all desktop effects too.

---

### Post by xzero1 on 2009-05-21
H.264 has high cpu requirements for decoding. Try running mplayer in benchmark mode i.e. 

```
mplayer -benchmark -frames 2000 -nosound  -cache 800000 -ss 1700 -vo null -lavdopts threads=1:skiploopfilter=all *filename* 
```Divide the total frames decoded (2000) by the total time. The result will be your decoding frame rate average. Now this is before sound and display overhead but it will give you an idea how fast your system is. Now for 720p videos this must be at least 60 fps for no frames to be dropped although the video may still be viewable. An important parameter for  mplayer is the selected video driver "-vo *driver*". The best selection depends on your system so I would benchmark with the "-vo" option to find it.

---

### Post by davemar on 2009-05-21
OK, I tried that with the .avi file, and it could only manage 11fps, so really struggling. It's 1080 HD, so a lot to deal with.

---

### Post by xzero1 on 2009-05-22
1080i or 1080p? What video card do you have?

---

### Post by davemar on 2009-05-22
I'm sure it's 1080i. The video card is a Nvidia 9500 GS, which isn't very well supported under Linux it seems.

---

### Post by xzero1 on 2009-05-22
I think your card is supported, at least according to this link [http://xbmc.org/forum/archive/index.php/t-40362-p-2.html.]("http://xbmc.org/forum/archive/index.php/t-40362-p-2.html")
You will need a version of mplayer that supports vdapu. I don't have such a card so I can't tell you in detail how to do it. But it is worth looking into.

---

