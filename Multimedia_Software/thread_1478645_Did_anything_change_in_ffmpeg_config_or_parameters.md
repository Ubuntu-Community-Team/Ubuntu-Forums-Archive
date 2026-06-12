---
title: "Did anything change in ffmpeg config or parameters since karmic?"
date: 2010-05-09
forum: Multimedia Software
---

### Post by MKdx on 2010-05-09
Hello

As topic title says; wondering if any parameters or default configurations have been changed in Lucid. I've been using ffmpeg to convert video files to mobile format and it always worked fine in Karmic and Hardy before that. 
Now I receive errors such as mismatching frame rate and unknown encoder aac - for videos that worked before.

libfaac0 is installed :confused:

```
$ ffmpeg -formats | grep aac
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3
 D  aac             raw ADTS AAC
 D A    aac             Advanced Audio Coding
  EA    libfaac         libfaac AAC (Advanced Audio Codec)
```

Any idea what might be the reason? Thanks

---

### Post by dtfinch on 2010-05-10
ffmpeg options seem to change all the time. Have you tried specifying "libfaac" instead of "aac"?

---

### Post by FakeOutdoorsman on 2010-05-10
*libfaac* has been removed from the repository FFmpeg due to some license issues.  Fortunately, the Medibuntu repository has provided a package that will enable libfaac in FFmpeg.  See **Option C: Medibuntu** in the following link:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by MKdx on 2010-05-13
> **FakeOutdoorsman said:**
> *libfaac* has been removed from the repository FFmpeg due to some license issues.  Fortunately, the Medibuntu repository has provided a package that will enable libfaac in FFmpeg.  See **Option C: Medibuntu** in the following link:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

I have Medibuntu, and libfaac was installed :)

> **dtfinch said:**
> ffmpeg options seem to change all the time. Have you tried specifying "libfaac" instead of "aac"?

'was about to type "yes and it didn't work", but wanted to check if different error message.. and it actually worked!!
I thought I did try it :-?

Thanks :P

---

