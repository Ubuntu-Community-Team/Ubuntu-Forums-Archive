---
title: "WinFF fails to convert to XviD on Karmic"
date: 2009-10-30
forum: Multimedia Software
---

### Post by krippa on 2009-10-30
Just installed Karmic final release and liking it a lot so far. However, I was trying to encode some raw videos from my camera to XVID so that my video editing program will open it but I ran in to the following problem:

```

FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:35:00, gcc: 4.4.1
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/kristofer/P1020886.MOV':
  Duration: 00:02:27.50, start: 0.000000, bitrate: 13103 kb/s
    Stream #0.0(eng): Video: mjpeg, yuvj420p, 848x480, 30 tbr, 30 tbn, 30 tbc
    Stream #0.1(eng): Audio: pcm_u8, 8000 Hz, mono, s16, 64 kb/s
Unknown encoder 'libxvid'

```

I tried installing all the GStream packages and the ubuntu-restricted-extras but still no go.

Any ideas?

/Kristofer

---

### Post by mc4man on 2009-10-30
I don't use the repo shared ffmpeg libs in karmic so can't say for sure, ... but try searching ffmpeg in synaptic and if you don't have the 'extra' versions of the ffmpeg libs installed then install them .
(don't remove the current ones, just mark the extra versions for install and apply (libavcodec-extra-52, libavformat-extra-52, ect., 7 are available.


Atm installing ubuntu-restricted-extras will install the stripped ffmpeg libs and if you had the extra versions installed prior to, it  would remove them in favour of the stripped ones (libavcodec52, ect.


This is totally meaningless as to the reality of what's enabled

 > configuration: [COLOR="Red"]--extra-version=[/COLOR]4:0.5+svn20090706-2ubuntu2 

---

### Post by ghostborg on 2009-11-11
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Did you add the Medibuntu repo and install codecs?

---

### Post by FakeOutdoorsman on 2009-11-11
> **ghostborg said:**
> [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Did you add the Medibuntu repo and install codecs?

[s]I see this once in a while as a suggested solution, but Medibuntu has nothing that will resolve the original poster's question (which is also a common question on these forums).[/s] This is no longer true as Medibuntu recently released a version of **libavcodec-extra-52** that will allow encoding to restricted formats.

As mc4man has mentioned, the restricted encoders need to be enabled to encode with libxvid via FFmpeg via WinFF.  More info:
[url=http://ubuntuforums.org/showpost.php?p=8298012&postcount=20]
HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in WinFF[/url]

---

### Post by StratosL on 2010-01-03
actually, the suggestion worked!! 

after installing the codecs from medibuntu (libavcodec-extra-52), winff managed to convert .mov to .avi, without the "libxvid" error message!!

---

