---
title: "ffmpeg stream mapping not working"
date: 2008-04-06
forum: Multimedia Production
---

### Post by mailbox on 2008-04-06
Running **ffmpeg -i rec.vob -vn -map 0:1 -acodec flac -ab 1024kbps rec.audio.flac** gives me this:```
FFmpeg version SVN-r12758, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-nonfree --enable-pthreads --enable-libx264 --enable-libamr-nb --enable-libamr-wb --enable-shared --enable-libvorbis --enable-libtheora --enable-libgsm --disable-debug --enable-libxvid --enable-libmp3lame --enable-libamr_nb --prefix=/usr --enable-postproc --enable-liba52 --enable-libdc1394 --enable-libfaad --enable-libfaac
  libavutil version: 49.6.0
  libavcodec version: 51.54.0
  libavformat version: 52.13.0
  libavdevice version: 52.0.0
  built on Apr  6 2008 16:22:10, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Input #0, mpeg, from 'rec.vob':
  Duration: 01:15:13.9, start: 0.367267, bitrate: 6151 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x576 [PAR 64:45 DAR 16:9], 8000 kb/s, 25.00 tb(r)
    Stream #0.1[0x89]: Audio: dca
File 'rec.audio.flac' already exists. Overwrite ? [y/N] y
Output #0, flac, to 'rec.audio.flac':
    Stream #0.0: Audio: flac, 1024 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
```What am I doing wrong?

---

### Post by mailbox on 2008-04-06
bump.

---

### Post by Creative2 on 2008-04-07
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

try
 
ffmpeg -i rec.vob -vn -map 0:1  -ab 1024k rec.audio.flac

 or try this


 
ffmpeg -i rec.vob -vn -map 0:1  -ab 384k rec.audio.flac

---

### Post by mailbox on 2008-04-13
> **Creative2 said:**
> Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

try
 
ffmpeg -i rec.vob -vn -map 0:1  -ab 1024k rec.audio.flac

 or try this


 
ffmpeg -i rec.vob -vn -map 0:1  -ab 384k rec.audio.flac
Nope, neither of those worked, **mplayer -vc null -vo null -ao pcm -benchmark rec.vob** was the only thing i've found so far that did.

---

