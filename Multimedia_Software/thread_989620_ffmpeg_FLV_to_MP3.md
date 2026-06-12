---
title: "ffmpeg FLV to MP3"
date: 2008-11-21
forum: Multimedia Software
---

### Post by Arctic_Fox on 2008-11-21
Hey guys I'm trying to convert the audio from an FLV file to MP3. Here's my console output.

```
$ ffmpeg -i vid.flv -acodec mp3 -ac 2 -ab 128 -vn -y filename.mp3
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Input #0, flv, from 'vid.flv':
  Duration: 00:03:47.0, start: 0.000000, bitrate: 128 kb/s
  Stream #0.0: Audio: mp3, 44100 Hz, stereo, 128 kb/s
Output #0, mp2, to 'filename.mp3':
  Stream #0.0: Audio: 0x0000, 44100 Hz, stereo, 0 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Unsupported codec for output stream #0.0
```

as you can see libmp3lame is enabled.

Any help is appreciated, thanks guys!

---

### Post by FakeOutdoorsman on 2008-11-21
Are on on Hardy using the Medibuntu ffmpeg?  I'm guessing using "-ab 128" instead of "-ab 128k" might be an issue.  Try this to copy the mp3 audio stream (no encoding required because your original file already has mp3 audio):
```
ffmpeg -i vid.flv -acodec copy output.mp3
```

---

### Post by Arctic_Fox on 2008-11-21
> **FakeOutdoorsman said:**
> Are on on Hardy using the Medibuntu ffmpeg?  I'm guessing using "-ab 128" instead of "-ab 128k" might be an issue.  Try this to copy the mp3 audio stream (no encoding required because your original file already has mp3 audio):
```
ffmpeg -i vid.flv -acodec copy output.mp3
```

Thanks this worked.

---

### Post by HotForLinux on 2010-03-03
> **FakeOutdoorsman said:**
> Are on on Hardy using the Medibuntu ffmpeg?  I'm guessing using "-ab 128" instead of "-ab 128k" might be an issue.  Try this to copy the mp3 audio stream (no encoding required because your original file already has mp3 audio):
```
ffmpeg -i vid.flv -acodec copy output.mp3
```

It's not working for me. I have the Medibuntu ffmpeg installed in Hardy Heron.
```
ffmpeg -i cannonball.flv -acodec copy cannonball.mp3 2>&1 |head
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 17 2009 21:37:49, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
[flv @ 0xb7f55110]Unsupported video codec (7)
[flv @ 0xb7f55110]Unsupported audio codec (a)
[flv @ 0xb7f55110]Unsupported video codec (7)
[flv @ 0xb7f55110]Unsupported video codec (7)
......
```

the output file:
```
$file cannonball.mp3
cannonball.mp3: data
```

---

### Post by tiguco on 2010-06-30
just change -acodec mp3 to -acodec libmp3lame

---

