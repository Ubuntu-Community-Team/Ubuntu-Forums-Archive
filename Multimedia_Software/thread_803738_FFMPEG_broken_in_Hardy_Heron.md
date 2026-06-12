---
title: "FFMPEG broken in Hardy Heron?"
date: 2008-05-22
forum: Multimedia Software
---

### Post by paulbawon on 2008-05-22
Just attempting to install ffmpeg. When I go to install the dependencies libfaad2-dev is not available in the repositories, and when I change it to libfaad-dev and then attempt to transcode a video file with AAC audio I get the following error message

```

[aac @ 0xb7eac2a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
```

My ffmpeg version is below 

```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on May 22 2008 19:51:38, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
```

Any help greatly appreciated - I've been banging my head against a brick wall for hours on this now!

---

### Post by garyedwardjohnston on 2008-05-22
I simply install "Ubuntu Restricted Extras"

---

### Post by mc4man on 2008-05-22
_maybe_ ck. here
[http://lists.medibuntu.org/pipermail/bugs/2008-May/001080.html](http://lists.medibuntu.org/pipermail/bugs/2008-May/001080.html)

---

### Post by cor2y on 2008-05-22
thats definitely an old version of ffmpeg the svn versions now refer to xvid etc as libxvid libx264, if you have no wish to compile your own use the more recent version from the medibuntu repos.

---

### Post by FakeOutdoorsman on 2008-05-22
However, if you with to compile your own see this thread:
[HOWTO: Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095")

What is the exact ffmpeg command you used?  What is the full output ffmpeg gave you after your command?  Which version of ffmpeg did you use (svn, Ubuntu repo, medibuntu)?

---

