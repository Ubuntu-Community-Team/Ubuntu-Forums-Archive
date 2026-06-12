---
title: "using avconv and getting odd &quot;pts has no value&quot; error"
date: 2013-03-18
forum: Multimedia Software
---

### Post by daloonik on 2013-03-18
Hi all!I can't seem to save a video using avconv. There seem to be streams available for download but all I get is a "PTS has no value" error. What does this error mean? Thanks for any help.```
naftee@asddsa:~$ avconv -fflags discardcorrupt -i "rtsp://medias-rtsp.tou.tv/vodtoutv/_definst_/mp4:003/MP4/e/2011-01-19_enfantstele_0008_1200" -c:v copy -c:a copy going_bald.mp4avconv version 0.8.5-4:0.8.5-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers  built on Jan 24 2013 18:03:14 with gcc 4.6.3[rtsp @ 0x8624340] Estimating duration from bitrate, this may be inaccurateInput #0, rtsp, from 'rtsp://medias-rtsp.tou.tv/vodtoutv/_definst_/mp4:003/MP4/e/2011-01-19_enfantstele_0008_1200':  Metadata:    title           : 003/MP4/e/2011-01-19_enfantstele_0008_1200  Duration: 00:44:22.70, start: 0.000000, bitrate: N/A    Stream #0.0: Audio: aac, 44100 Hz, stereo, s16    Stream #0.1: Video: h264 (Main), yuv420p, 852x480 [PAR 1:1 DAR 71:40], 29.97 fps, 1k tbr, 90k tbn, 59.94 tbcOutput #0, mp4, to 'going_bald.mp4':  Metadata:    title           : 003/MP4/e/2011-01-19_enfantstele_0008_1200    encoder         : Lavf53.21.1    Stream #0.0: Video: libx264, yuv420p, 852x480 [PAR 1:1 DAR 71:40], q=2-31, 90k tbn, 90k tbc    Stream #0.1: Audio: libvo_aacenc, 44100 Hz, stereoStream mapping:  Stream #0:1 -> #0:0 (copy)  Stream #0:0 -> #0:1 (copy)Press ctrl-c to stop encoding[mp4 @ 0x863b880] pts has no value[mp4 @ 0x863b880] pts < dts in stream 0av_interleaved_write_frame(): Invalid argument
```

---

### Post by andrew.46 on 2013-03-18
Hmmm... I get a similar error with recent git FFmpeg and I am unable to play with MPlayer. To make the code more readable simple enclose with a code tag:

```

Like this!!!

```

Hopefully somebody else can guide you here...

---

