---
title: "Convert MP4 file to avi"
date: 2012-04-09
forum: Multimedia Software
---

### Post by volkerbradley on 2012-04-09
I used my camera to make at video.  The video is in the MP4 format. I would like to convert this file to an avi file. What command would you suggest to make the avi file using ffmpeg and lame?
(I know how to do this with mencoder but I would prefer to have more control with ffmpeg and lame).

The details of the file that I would like to convert are:
ffmpeg -i M4H00846.MP4
ffmpeg version git-2012-01-06-ed14b72 Copyright (c) 2000-2012 the FFmpeg developers
built on Jan 6 2012 10:54:37 with gcc 4.6.1
configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-nonfree --enable-postproc --enable-version3 --enable-x11grab
libavutil 51. 34.100 / 51. 34.100
libavcodec 53. 54.100 / 53. 54.100
libavformat 53. 29.100 / 53. 29.100
libavdevice 53. 4.100 / 53. 4.100
libavfilter 2. 57.101 / 2. 57.101
libswscale 2. 1.100 / 2. 1.100
libswresample 0. 5.100 / 0. 5.100
libpostproc 51. 2.100 / 51. 2.100
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'M4H00846.MP4':
Metadata:
major_brand : MSNV
minor_version : 19595353
compatible_brands: MSNVmp42isom
creation_time : 2012-04-04 12:22:47
Duration: 00:00:36.03, start: 0.000000, bitrate: 9093 kb/s
Stream #0:0(und): Video: mpeg4 (Advanced Coding Profile) (mp4v / 0x7634706D), yuv420p, 1280x720 [SAR 1:1 DAR 16:9], 9026 kb/s, 29.97 fps, 29.97 tbr, 30k tbn, 30k tbc
Metadata:
creation_time : 2012-04-04 12:22:47
handler_name : Video Media Handler
Stream #0:1(und): Audio: aac (mp4a / 0x6134706D), 24000 Hz, mono, s16, 64 kb/s
Metadata:
creation_time : 2012-04-04 12:22:47
handler_name : Sound Media Handler
Thanks

---

### Post by ron999 on 2012-04-09
> **volkerbradley said:**
> What command would you suggest to make the avi file using ffmpeg and lame?
This is the command I suggest:-

```
ffmpeg -i M4H00846.MP4 -c:v copy -c:a libmp3lame -b:a 64k -ac 1 M4H00846.avi
```

---

### Post by volkerbradley on 2012-04-09
> **ron999 said:**
> This is the command I suggest:-

```
ffmpeg -i M4H00846.MP4 -c:v copy -c:a libmp3lame -b:a 64k -ac 1 M4H00846.avi
```

Perfect!  Thank you.
Gives me an idea on how to use ffmpeg options as well.

---

### Post by sallymc on 2012-10-07
This worked for me :

1. Install ffmpeg
  [COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**apt-get install**[/COLOR] [COLOR=#c20cb9]**ffmpeg**[/COLOR]
  2. Convert your video
  [COLOR=#c20cb9]**ffmpeg**[/COLOR] [COLOR=#660033]-i[/COLOR] myvideo.mp4 [COLOR=#660033]-vcodec[/COLOR] mpeg4 [COLOR=#660033]-acodec[/COLOR] ac3 [COLOR=#660033]-ar[/COLOR] [COLOR=#000000]48000[/COLOR] [COLOR=#660033]-ab[/COLOR] 192k myvideo.avi

Good luck

---

