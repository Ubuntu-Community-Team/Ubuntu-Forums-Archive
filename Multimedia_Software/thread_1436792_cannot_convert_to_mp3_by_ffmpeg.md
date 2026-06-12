---
title: "cannot convert to mp3 by ffmpeg"
date: 2010-03-23
forum: Multimedia Software
---

### Post by rahilm on 2010-03-23
i cannot convert to mp3 using ffmpeg. when i do:

```
ffmpeg -i input.flac -acodec mp3 output.mp3
```

i get:
```
Unknown encoder 'mp3'
``` at the end the media info.

what codecs should i install? basically, this is linux mint so i guess everything should have been installed by default...

---

### Post by l.billon on 2010-03-23
Hi!
You do not have to specify -acodec mp3, ffmpeg uses the output filename to choose the appropropriate codec.

---

### Post by rahilm on 2010-03-23
I did:
```
ffmpeg -i loop.flac loop.mp3
```
i get this output:
```
ffmpeg -i loop.flac loop.mp3
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1
Input #0, flac, from 'loop.flac':
  Duration: N/A, bitrate: N/A
    Stream #0.0: Audio: flac, 44100 Hz, stereo, s16
Output #0, mp3, to 'loop.mp3':
    Stream #0.0: Audio: 0x0000, 44100 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Unsupported codec for output stream #0.0


```

---

### Post by l.billon on 2010-03-23
Does activating the Medibuntu repository and dist-upgrade does any help?

---

### Post by rahilm on 2010-03-23
I already have medibuntu enabled..

---

### Post by andrew.46 on 2010-03-23
Hi rahilm,

Some encoders are disabled in Ubuntu because of licensing issues. To enable mp3 encoding, and a few others, have a look at this page:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

After you have followed the steps recommended by this guide you may find that if you are using Karmic Koala and you wish to specify the mp3 encoder, and possibly add a few options, you will need to use *-acodec libmp3lame*, rather than *-acodec mp3*, followed by the options of your choice...

All the best,

Andrew

---

### Post by MoarningSun on 2010-03-23
On Mint mp3 should be supported out of the box I believe. But as andrew pointed out, try 'libmp3lame' as the codec, as this is the correct name in the new ffmpeg syntax. To see which codecs are supported in your version of ffmpeg type:
```
ffmpeg -codecs
```
Good luck:D

---

### Post by rahilm on 2010-03-23
> **MoarningSun said:**
> On Mint mp3 should be supported out of the box I believe. But as andrew pointed out, try 'libmp3lame' as the codec, as this is the correct name in the new ffmpeg syntax. To see which codecs are supported in your version of ffmpeg type:
```
ffmpeg -codecs
```Good luck:D
```

ffmpeg -codecs
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1
ffmpeg: missing argument for option '-codecs'

```

---

### Post by FakeOutdoorsman on 2010-03-23
> **rahilm said:**
> ```

ffmpeg -codecs
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1
ffmpeg: missing argument for option '-codecs'

```

FFmpeg option names change once in a while.  FFmpeg from the Ubuntu repository lists available codecs with *ffmpeg -formats*.

---

### Post by rahilm on 2010-03-23
I am trying to find if i am missing any dependencies..

---

### Post by rahilm on 2010-03-23
installed libavcodec-extra-52.. now everything is okay.
i can run:
```
ffmpeg -i loop.flac -acodec libmp3lame -ab 128k loop.mp3
```

thanx guys!!

---

### Post by andrew.46 on 2010-03-23
Hi rahilm,

Excellent news :). I wish you all the best with a continued exploration of this great program.

All the best,

Andrew

---

