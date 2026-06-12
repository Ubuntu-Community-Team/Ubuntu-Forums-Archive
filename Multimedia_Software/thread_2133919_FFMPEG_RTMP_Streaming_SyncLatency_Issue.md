---
title: "FFMPEG RTMP Streaming Sync/Latency Issue"
date: 2013-04-09
forum: Multimedia Software
---

### Post by mrspacklecrisp on 2013-04-09
Ubuntu 12.04

I am trying to set up a small private justin.tv channel from my underpowered computer. I've gotten most stuff working, but I still have a big latency problem and more importantly the video is far behind the audio. How can I resolve this?

This is the command I am using:

```
ffmpeg -f x11grab -s 550:400 -r 10 -i :0.0 -f alsa -ac 2 -i pulse -vcodec libx264 -qscale 31 -preset ultrafast -ab 96k -s 550x400 -acodec libmp3lame -ar 44100 -threads 0 -tune zerolatency -f flv rtmp://live.justin.tv/app/[LIVEKEYGOESHERE] 

```

I can only take a small portion of the screen, and it's not yet adjusted to the right section so don't worry about that.

I'm almost certain 'ultrafast' is not the best preset to use, but I get errors for other kinds which I know is a problem specific to the ubuntu build.

EDIT:
Here are a couple highlights from the output. I'm sorry, I will post a fuller example later.

```

[x11grab @ 0x9315240] Estimating duration from bitrate, this may be inaccurate

Input #0, x11grab, from ':0.0':
  Duration: N/A, start: 1365532044.067209, bitrate: 70399 kb/s
    Stream #0.0: Video: rawvideo, bgra, 550x400, 70399 kb/s, 10 tbr, 1000k tbn, 10 tbc
[alsa @ 0x9320280] capture with some ALSA plugins, especially dsnoop, may hang.
[alsa @ 0x9320280] Estimating duration from bitrate, this may be inaccurate
Input #1, alsa, from 'pulse':
  Duration: N/A, start: 1365532043.999368, bitrate: N/A
    Stream #1.0: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
Incompatible pixel format 'bgra' for codec 'libx264', auto-selecting format 'yuv420p'

```

---

### Post by mrspacklecrisp on 2013-04-14
Bump

Edit: Here is full output.

[http://pastebin.com/NLXfBRgk](http://pastebin.com/NLXfBRgk)

---

