---
title: "Recording multiple audio inputs with avconv (Aka ffmpeg)"
date: 2012-04-21
forum: Multimedia Software
---

### Post by J V on 2012-04-21
I want to record the pulseaudio monitor of internal audio (So the audio the system is producing) and a microphone into the same file, as separate audio "Tracks" or "Channels" so that I can pick them apart later in a video editor.

For simply recording the screen and audio output I use a script file like this:
```
#!/bin/bash
avconv \
-f alsa  \
-i hw:1,0 \
-i hw:0,0 \
-f x11grab -r 30 -s hd1080 -i :0.0 \
-vcodec libx264 -vf 'scale=-1:720' -pre:v lossless_ultrafast \
-acodec libmp3lame \
-threads 0 -y $@
```This should record both the mic and the audio output, however it gives an error stating: cannot set channel count to 2 (Invalid argument)

Edit: Careful watching of the avconv output shows me (Note the "Stream mapping"):
```
[alsa @ 0xfdbac0] capture with some ALSA plugins, especially dsnoop, may hang.
[alsa @ 0xfdbac0] Estimating duration from bitrate, this may be inaccurate
Input #0, alsa, from 'pulse':
  Duration: N/A, start: 1335056595.405298, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
[alsa @ 0xfdc7c0] Estimating duration from bitrate, this may be inaccurate
Input #1, alsa, from 'hw:1,0':
  Duration: N/A, start: 54417.351882, bitrate: N/A
    Stream #1.0: Audio: pcm_s16le, 48000 Hz, 1 channels, s16, 768 kb/s
[x11grab @ 0xfdd900] device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1920 height: 1080
[x11grab @ 0xfdd900] shared memory extension  found
[x11grab @ 0xfdd900] Estimating duration from bitrate, this may be inaccurate
Input #2, x11grab, from ':0.0':
  Duration: N/A, start: 1335056595.756955, bitrate: 1990656 kb/s
    Stream #2.0: Video: rawvideo, bgra, 1920x1080, 1990656 kb/s, 30 tbr, 1000k tbn, 30 tbc
Incompatible pixel format 'bgra' for codec 'libx264', auto-selecting format 'yuv420p'
[buffer @ 0xfd62e0] w:1920 h:1080 pixfmt:bgra
[scale @ 0xfffa40] w:1920 h:1080 fmt:bgra -> w:1280 h:720 fmt:yuv420p flags:0x4
[libx264 @ 0xfd8d20] using cpu capabilities: MMX2 SSE2Fast SSSE3 FastShuffle SSE4.2 AVX
[libx264 @ 0xfd8d20] profile High 4:4:4 Predictive, level 3.1, 4:2:0 8-bit
Output #0, avi, to 'out.avi':
  Metadata:
    ISFT            : Lavf53.21.0
    Stream #0.0: Video: libx264, yuv420p, 1280x720, q=-1--1, 30 tbn, 30 tbc
    Stream #0.1: Audio: libmp3lame, 48000 Hz, 2 channels, s16, 200 kb/s
Stream mapping:
  Stream #2:0 -> #0:0 (rawvideo -> libx264)
  Stream #0:0 -> #0:1 (pcm_s16le -> libmp3lame)
```I'm mapping something wrong...

Edit: Found how to map it! This works, but I'd like to avoid using pulse as input, since it tends to vary
```
#!/bin/bash
avconv \
-f alsa -ac 2 -i pulse \
-f alsa -ac 1 -i hw:1,0 \
-f x11grab -r 30 -s hd1080 -i :0.0 \
-map 0:0 -map 1:0 -map 2:0 \
-vcodec libx264 -vf 'scale=-1:720' -pre:v lossless_ultrafast \
-acodec libmp3lame \
-threads 0 -y $@
```

---

