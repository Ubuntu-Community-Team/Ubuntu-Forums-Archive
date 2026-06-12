---
title: "ffmpeg, making .avi from .vob"
date: 2008-05-11
forum: Multimedia Software
---

### Post by gerben1 on 2008-05-11
Hi,

I am trying to make an .avi from an .vob file. I made the .vob file with dvd-slideshow, I did not add any music so dvd-slideshow just added a silent audio stream. When I try to convert with ffmpeg, using simply
```
ffmpeg -i GBRtest.vob GBRtest.avi
```
I get this error:
```

gerben@CC1184274-A:~/Videos/Slide shows/test$ ffmpeg -i GBRtest.vob GBRtest.avi
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 23 2008 22:28:54, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu6)
Input #0, mpeg, from 'GBRtest.vob':
  Duration: 00:00:13.2, start: 0.184656, bitrate: 2848 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x576, 7500 kb/s, 25.00 fps(r)
  Stream #0.1[0x80]: Audio: ac3, 48000 Hz, 5:1, 192 kb/s
Output #0, avi, to 'GBRtest.avi':
  Stream #0.0: Video: mpeg4, yuv420p, 720x576, q=2-31, 200 kb/s, 25.00 fps(c)
  Stream #0.1: Audio: mp2, 48000 Hz, 5:1, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height

```

As the stream giving me problems is the audio stream, I tried adding information about the audio stream, like this:
```

ffmpeg -i GBRtest.vob GBRtest.avi -ab 192k -acodec ac3 -ar 48000 -ac 6

```

so I told ffmpeg what the audio bitrate, codec, sampling rate and number of channels are, but I still get the same error:

```

gerben@CC1184274-A:~/Videos/Slide shows/test$ ffmpeg -i GBRtest.vob GBRtest.avi -ab 192k -acodec ac3 -ar 48000 -ac 6
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 23 2008 22:28:54, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu6)
Input #0, mpeg, from 'GBRtest.vob':
  Duration: 00:00:13.2, start: 0.184656, bitrate: 2848 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x576, 7500 kb/s, 25.00 fps(r)
  Stream #0.1[0x80]: Audio: ac3, 48000 Hz, 5:1, 192 kb/s
File 'GBRtest.avi' already exists. Overwrite ? [y/N] y
Output #0, avi, to 'GBRtest.avi':
  Stream #0.0: Video: mpeg4, yuv420p, 720x576, q=2-31, 200 kb/s, 25.00 fps(c)
  Stream #0.1: Audio: mp2, 48000 Hz, 5:1, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height

```

Any ideas on how to try to get this working?

---

