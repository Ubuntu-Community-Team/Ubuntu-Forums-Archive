---
title: "Convert M4A to MP3 using FFMPEG"
date: 2010-11-06
forum: Multimedia Software
---

### Post by FinalShot on 2010-11-06
How can I convert M4A to MP3 using FFMPEG?

Why? So I can listen to the audio on my 360.

---

### Post by jfed on 2010-11-06
Honestly, I'm not too sure, but look up some tutorials about Mencoder. That might help some.

---

### Post by andrew.46 on 2010-11-06
You will need yo make sure that you have mp encoding enabled:

```

andrew@skamandros~$ **[COLOR="Red"]ffmpeg -codecs help | grep 'mp3'[/COLOR]**
FFmpeg version SVN-r25679, Copyright (c) 2000-2010 the FFmpeg developers
  built on Nov  5 2010 10:58:20 with gcc 4.3.3
  configuration: --prefix=/usr --mandir=/usr/man --enable-postproc --enable-avfilter --enable-pthreads --enable-shared --disable-static --disable-ffserver --enable-libtheora --enable-libvorbis --enable-x11grab --enable-libmp3lame --enable-libx264 --enable-libfaac --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-zlib --enable-libvpx --enable-libxvid --enable-nonfree --enable-gpl
  libavutil     50.32. 6 / 50.32. 6
  libavcore      0.12. 0 /  0.12. 0
  libavcodec    52.94. 3 / 52.94. 3
  libavformat   52.84. 0 / 52.84. 0
  libavdevice   52. 2. 2 / 52. 2. 2
  libavfilter    1.56. 0 /  1.56. 0
  libswscale     0.12. 0 /  0.12. 0
  libpostproc   51. 2. 0 / 51. 2. 0
**[COLOR="Red"]  EA    libmp3lame      libmp3lame MP3 (MPEG audio layer 3)[/COLOR]**
 D A    mp3             MP3 (MPEG audio layer 3)
 D A    mp3adu          ADU (Application Data Unit) MP3 (MPEG audio layer 3)
 D A    mp3adufloat     ADU (Application Data Unit) MP3 (MPEG audio layer 3)
 D A    mp3float        MP3 (MPEG audio layer 3)
 D A    mp3on4          MP3onMP4
 D A    mp3on4float     MP3onMP4

```

and then something like the following could furnish at least a starting point:

```
ffmpeg -i input.m4a -acodec libmp3lame -ab 128k output.mp3
```

Andrew

---

### Post by FinalShot on 2010-11-06
That codec is installed ( libmp3lame0 and libmpelame-dev are installed in the package manager ) but it doesn't appear in the list after I run:

```
[COLOR=Black]ffmpeg -codecs help | grep 'mp3'[/COLOR]
```

Output:
```
scott@scott-desktop:~$ ffmpeg -codecs help | grep 'mp3'
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
ffmpeg: unrecognized option '-codecs'
```

And it appears you have a later version ( based on the build date ).

Anyway the file still converted, but it doesn't appear on the 360. Maybe because it used some default codec, instead of libmp3lame.

---

### Post by shantiq on 2010-11-06
and the same as a batch-convertion (all files in folder at once) should look like this



first    cd to the folder where you m4a files are then enter:


```
for f in *.m4a; do ffmpeg -i "$f" -acodec libmp3lame -ab 256k "${f%.m4a}.mp3"; done
```


of course change 256k to whatever you want it to be. Andrew suggested 128, you can pick that or go all the way to 320     check what your kbps was on your m4a first and maybe pick the same    

if your m4a were alac definitely pick 320

---

### Post by FinalShot on 2010-11-06
All good now, and thanks shantiq that should make this easier and faster.

---

### Post by FakeOutdoorsman on 2010-11-06
> **FinalShot said:**
> That codec is installed ( libmp3lame0 and libmpelame-dev are installed in the package manager ) but it doesn't appear in the list...

It's unintuitive, but installing the *lame* packages won't add mp3 encoding to FFmpeg.  See:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

I see you marked this thread as solved, but I added this for others who may find this thread and are wondering about the same.


> **shantiq said:**
> of course change 256k to whatever you want it to be. Andrew suggested 128, you can pick that or go all the way to 320

Alternatively, you can use *-aq* instead of *-ab* to encode VBR audio.  The values for *-aq* vary per encoder. For example, *-aq 4* would be the same as *lame -V4*.

---

### Post by Coretj on 2010-11-21
Really hoping this works... The terminal window says time: 14,000 ... and it keeps going up.. I really hope that is seconds and not minutes.

---

