---
title: "ffmpeg fail to convert to AMR format"
date: 2011-06-29
forum: Multimedia Software
---

### Post by cloto3000 on 2011-06-29
I have installed corretly the ffmpeg using medibuntu repository. 
But the result is:
 ffmpeg -i prova.wav pippo.amr
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Apr  8 2011 20:48:55, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Input #0, wav, from 'prova.wav':
  Duration: 00:00:01.0, start: 0.000000, bitrate: 1411 kb/s
  Stream #0.0: Audio: pcm_s16le, 44100 Hz, stereo, 1411 kb/s
File 'pippo.amr' already exists. Overwrite ? [y/N] y
Output #0, amr, to 'pippo.amr':
  Stream #0.0: Audio: 0x0000, 44100 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Unsupported codec for output stream #0.0

You can see that --enable-amr_nb and wb are in using.
Why this error ?
Thanks

---

### Post by andrew.46 on 2011-06-29
Which version of Ubuntu are you using? Looks like quite an old version of FFmpeg....

---

