---
title: "FFMPEG conversion error av_interleaved_write_frame()"
date: 2009-10-27
forum: Multimedia Software
---

### Post by jimmah6786 on 2009-10-27
Any ideas why i get this:

```

user@computer:~/Videos$ ffmpeg -i VTS_01_1.VOB -acodec copy -vcodec libxvid -qscale 7 -map 0.0 -map 0.7 -f avi out.avi

Output #0, avi, to 'out.avi':
    Stream #0.0: Video: libxvid, yuv420p, 720x480 [PAR 32:27 DAR 16:9], q=2-31, 200 kb/s, 59.94 tbn, 59.94 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.7 -> #0.1
Press [q] to stop encoding
[NULL @ 0x2f407d0]error, non monotone timestamps 827 >= 827e= 891.4kbits/s    
av_interleaved_write_frame(): Error while opening file

```

FFMPEG info:
```
FFmpeg version SVN-r20383, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  built on Oct 27 2009 13:53:55 with gcc 4.4.1
  configuration: --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.37. 1 / 52.37. 1
  libavformat   52.39. 2 / 52.39. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1

```

My System:
Ubuntu 9.10 rc1 x86_64

---

### Post by vinutux on 2009-10-27
Try handbarke for conversion (my fav)

---

