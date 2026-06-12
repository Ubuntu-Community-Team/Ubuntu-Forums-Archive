---
title: "mp4ize... unknown codec... converting an avi... help?"
date: 2008-11-09
forum: Multimedia Software
---

### Post by fINTiP on 2008-11-09
I'm trying to use mp4ize... here's my current status:

```
kajo@dasg:~/Desktop/Multimedia/movie/Born.Into.Brothels.2004.DVDRip.XviD_ENG.PT-BR$ mp4ize Born.Into.Brothels.2004.DVDRip.XviD_ENG.PT-BR.avi
0.00% | FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

Seems stream 0 codec frame rate differs from container frame rate: 29.98 (65535/2186) -> 29.97 (2997/100)
Input #0, avi, from 'Born.Into.Brothels.2004.DVDRip.XviD_ENG.PT-BR.avi':
  Duration: 01:23:21.0, start: 0.000000, bitrate: 1166 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 608x448, 29.97 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 32 kb/s
Unknown codec 'xvid'
0.00% | FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

Seems stream 0 codec frame rate differs from container frame rate: 29.98 (65535/2186) -> 29.97 (2997/100)
Input #0, avi, from 'Born.Into.Brothels.2004.DVDRip.XviD_ENG.PT-BR.avi':
  Duration: 01:23:21.0, start: 0.000000, bitrate: 1166 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 608x448, 29.97 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 32 kb/s
Unknown codec 'libxvid'
0.00% | FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

Seems stream 0 codec frame rate differs from container frame rate: 29.98 (65535/2186) -> 29.97 (2997/100)
Input #0, avi, from 'Born.Into.Brothels.2004.DVDRip.XviD_ENG.PT-BR.avi':
  Duration: 01:23:21.0, start: 0.000000, bitrate: 1166 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 608x448, 29.97 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 32 kb/s
Unknown codec 'libxvid'
```

Any ideas? I'm in 8.04, and I have the medibuntu FFMPEG installed

K

---

### Post by xebix on 2008-12-16
I am having the same problem. It was working at one time. I did an update a few days ago and it is no longer working.

---

### Post by FakeOutdoorsman on 2008-12-16
Give the output of:
```
ffmpeg -formats | grep xvid
```
If you are using (8.04) Hardy with Medibuntu's ffmpeg then mp4ize should work with no issues.

---

### Post by driven1 on 2009-01-25
I'm having the exact same issue

```
ubuntu-amd:~$ ffmpeg -formats | grep xvid
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Sep 26 2008 12:58:24, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu1)

```

---

### Post by FakeOutdoorsman on 2009-01-25
> **driven1 said:**
> I'm having the exact same issue

```
ubuntu-amd:~$ ffmpeg -formats | grep xvid
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Sep 26 2008 12:58:24, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu1)

```
Do you still have issues if you install the **libavcodec-unstripped-51** package?  This will enable restricted encoders such as libxvid in ffmpeg.

---

### Post by driven1 on 2009-01-26
Do you know which repository is that in? It came back with package not found. thanks

---

### Post by wolfen69 on 2009-01-26
ive never used mp4ize, but [Handbrake]("http://handbrake.fr/rotation.php?file=HandBrake-0.9.3-Ubuntu_GUI_i386.deb") is a 2 click deal to convert to mp4. doesn't get much easier. plus there's presets to fine tune things. (psp mode, etc. )

---

### Post by FakeOutdoorsman on 2009-01-27
> **driven1 said:**
> Do you know which repository is that in? It came back with package not found. thanks
I assumed you were using Intrepid.  Are you using Hardy?  The libavcodec-unstripped-51 package is new and is for Intrepid.  For Hardy, you have two choices to gain access to restricted formats in ffmpeg: use a third-party repository or compile ffmpeg yourself.  [Medibuntu](http://medibuntu.org/) is usually the recommended third-party repository and it's version of ffmpeg usually works fine.  If you want more control, more features, or a much more current version then refer to this guide:
[url=http://ubuntuforums.org/showthread.php?t=786095]
HOWTO: Compile the latest ffmpeg and x264 from source[/url]

---

### Post by driven1 on 2009-01-27
> **wolfen69 said:**
> ive never used mp4ize, but [Handbrake]("http://handbrake.fr/rotation.php?file=HandBrake-0.9.3-Ubuntu_GUI_i386.deb") is a 2 click deal to convert to mp4. doesn't get much easier. plus there's presets to fine tune things. (psp mode, etc. )

I need to convert  .avi to mp4 for iPod viewing. I haven't been able I do that in HandBrake.

---

### Post by driven1 on 2009-01-27
> **FakeOutdoorsman said:**
> I assumed you were using Intrepid.  Are you using Hardy?  The libavcodec-unstripped-51 package is new and is for Intrepid.  For Hardy, you have two choices to gain access to restricted formats in ffmpeg: use a third-party repository or compile ffmpeg yourself.  [Medibuntu](http://medibuntu.org/) is usually the recommended third-party repository and it's version of ffmpeg usually works fine.  If you want more control, more features, or a much more current version then refer to this guide:
[url=http://ubuntuforums.org/showthread.php?t=786095]
HOWTO: Compile the latest ffmpeg and x264 from source[/url]

I was using Intrepid but went back to hardy because my display gets stuck at a gray screen of death. I had this working prior to my upgrade but now I can't sort it out for some reason. Thanks for the tips. I'll see if I can get it working tomorrow. Maybe I'll give Intrepid another shot.

---

