---
title: "[ffmpeg] cannot split avi!!"
date: 2008-09-17
forum: Multimedia Software
---

### Post by kakyoism on 2008-09-17
I tried to use ffmpeg to split an .avi file (DivX or sth), with the command
```
ffmpeg -i input.avi -ss 00:00:10 -t 00:00:30 output.avi
```

Then I got this error:
```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Input #0, ogg, from 'input.avi':
  Duration: 01:58:38.0, start: 0.533867, bitrate: 1707 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 640x480, 29.97 fps(r)
  Stream #0.1: Audio: vorbis, 48000 Hz, stereo, 192 kb/s
Output #0, avi, to 'out1.avi':
  Stream #0.0: Video: mpeg4, yuv420p, 640x480, q=2-31, 200 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: mp2, 48000 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mpeg4 @ 0xb7e7f9a8]timebase not supported by mpeg 4 standard
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
```

Any idea what was wrong??
Was it because I used wrong parameters?
Thanks!

---

### Post by aeiah on 2008-09-17
does this work with a bigger clip size? there may be no keyframe in between 00:00:10 and 00:00:30 and perhaps another option needs to be put in the command. is there a reason why you cant use mencoder? this does splitting in a similar way but may not produce similar errors.

i think i use mencoder for splitting in an app im writing but i cant check the command i use until i get home from work.

---

