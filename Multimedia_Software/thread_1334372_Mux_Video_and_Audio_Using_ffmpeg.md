---
title: "Mux Video and Audio Using ffmpeg"
date: 2009-11-22
forum: Multimedia Software
---

### Post by Hirsute on 2009-11-22
Hi,

Currently using karmic x64.

I'm trying to mux an AVI video file (which has no audio) with an AC3 audio file using ffmpeg.

here's what I'm doing...

```
ffmpeg -i movie.avi -vcodec copy -i audio.ac3 -acodec copy movieMuxed.avi 
```On their own the file sizes are:
    movie.avi   9.2G
    audio.ac3   1.5G

However after running the above command I've got the movieMuxed.avi file, but this has a file size of 32G. I'm not sure where I have went wrong here as I was expecting the size to be ~10.7G (adding the two file sizes together?).

Also this new file (movieMuxed.avi) does not play in either mplayer or Totem.

So basically I'm wondering how to do this correctly so that I have a movie with audio.

Any help appreciated.

Thanks.

---

### Post by FakeOutdoorsman on 2009-11-22
Show the complete FFmpeg output that you get after running your command.

---

### Post by Hirsute on 2009-11-22
Okay here's what was at the end.

video:9611060kB audio:1511994kB global headers:0kB muxing overhead 227.377124%

---

### Post by FakeOutdoorsman on 2009-11-22
Show the **complete** FFmpeg output.

---

### Post by Hirsute on 2009-11-23
Apologies I think I was half asleep when I sent that reply.

Anyway here is the full output once ffmpeg has done its thing:

FFmpeg version SVN-r20570, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  built on Nov 22 2009 01:03:03 with gcc 4.4.1
  configuration: --enable-gpl --enable-libmp3lame --enable-libxvid --enable-libfaac --enable-nonfree
  libavutil     50. 4. 0 / 50. 4. 0
  libavcodec    52.41. 0 / 52.41. 0
  libavformat   52.39. 2 / 52.39. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
Input #0, avi, from 'movie.avi':
  Duration: 02:16:48.24, start: 0.000000, bitrate: 9595 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 23.98 tbr, 23.98 tbn, 23.98 tbc
[dts @ 0x14f9fb0]max_analyze_duration reached
Input #1, dts, from 'audio.ac3':
  Duration: 02:14:23.96, bitrate: 1536 kb/s
    Stream #1.0: Audio: dca, 48000 Hz, 5.1, s16, 1536 kb/s
Output #0, avi, to 'movieMuxed.avi':
    Stream #0.0: Video: mpeg4, yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], q=2-31, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: 0x2001, 48000 Hz, 5.1, s16, 1536 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #1.0 -> #0.1
frame=196801 fps= 58 q=-1.0 Lsize=36414334kB time=8062.90 bitrate=36997.4kbits/s    
video:9611060kB audio:1511994kB global headers:0kB muxing overhead 227.377124% 

I have noticed this line

```
Input #1, dts, from 'audio.ac3':
```Which I assume means that audio.ac3 is actually dts audio? (Sorry i'm completely new to this so not sure if this is a daft question).

Could this be causing a problem?

Thanks again.

---

