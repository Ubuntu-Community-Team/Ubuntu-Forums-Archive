---
title: "Problem With FFMPEG AVI to FLV"
date: 2010-05-26
forum: Multimedia Software
---

### Post by spygm on 2010-05-26
hi, i need some help regarding FFMPEG with ubuntu 10.4 that i install via apt-get,
im trying to convert avi to flv but have error "Invalid and inefficient vfw-avi packed B frames detected"

im already try many thing and follow some solution from this forum but still no luck

anybody can help me? below i put the result

--------------------------------------------------------------------------------------------------------
spygm@ubuntu10:/var/shared/input$ ffmpeg -i 'test.avi' -y -s 320x240 -ar 44100 -acodec libmp3lame 'test.flv' 
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
[NULL @ 0x9d41d20]Invalid and inefficient vfw-avi packed B frames detected

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (12570329/524288)
Input #0, avi, from 'Fate stay night - 01.avi':
  Duration: 00:24:09.82, start: 0.000000, bitrate: 986 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 704x396 [PAR 1:1 DAR 16:9], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 128 kb/s
Output #0, flv, to 'Fate stay night - 01.flv':
    Stream #0.0: Video: flv, yuv420p, 320x240 [PAR 4:3 DAR 16:9], q=2-31, 200 kb/s, 90k tbn, 23.98 tbc
    Stream #0.1: Audio: libmp3lame, 44100 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1

Press [q] to stop encoding
[mpeg4 @ 0x9d41d20]Invalid and inefficient vfw-avi packed B frames detected

--------------------------------------------------------------------------------------------------------
here my ffmpeg version

spygm@ubuntu10:/var/shared/input$ ffmpeg -version
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
FFmpeg SVN-r0.5.1-4:0.5.1-1ubuntu1
libavutil     49.15. 0 / 49.15. 0
libavcodec    52.20. 1 / 52.20. 1
libavformat   52.31. 0 / 52.31. 0
libavdevice   52. 1. 0 / 52. 1. 0
libavfilter    0. 4. 0 /  0. 4. 0
libswscale     0. 7. 1 /  0. 7. 1
libpostproc   51. 2. 0 / 51. 2. 0

---

### Post by nothingspecial on 2010-05-26
It doesn`t look like you have libmp3lame compiled in to ffmpeg.

```
sudo apt-get install libavcodec-extra-52
```

---

### Post by spygm on 2010-05-26
i think the problem with MPEG4 maybe
actually i already try this but still no luck

[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)


> **nothingspecial said:**
> It doesn`t look like you have libmp3lame compiled in to ffmpeg.

```
sudo apt-get install libavcodec-extra-52
```

---

### Post by nothingspecial on 2010-05-26
You still need libmp3lame.

Your command is correct, I just tried it myself.
```

ffmpeg -i Its_Flashbeagle_Charlie_Brown.avi -y -s 320x240 -ar 44100 -acodec libmp3lame test.flv 
FFmpeg version SVN-r22991, Copyright (c) 2000-2010 the FFmpeg developers
  built on Apr 30 2010 12:36:06 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad [COLOR="Red"]--enable-libmp3lame[/COLOR] --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.15. 0 / 50.15. 0
  libavcodec    52.66. 0 / 52.66. 0
  libavformat   52.61. 0 / 52.61. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0.10. 0 /  0.10. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Input #0, avi, from 'Its_Flashbeagle_Charlie_Brown.avi':
  Metadata:
    ISFT            : transcode-1.1.5
  Duration: 00:23:18.92, start: 0.000000, bitrate: 6583 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 640x480 [PAR 1:1 DAR 4:3], 25 tbr, 25 tbn, 25 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, 2 channels, s16, 128 kb/s
Output #0, flv, to 'test.flv':
  Metadata:
    encoder         : Lavf52.61.0
    Stream #0.0: Video: flv, yuv420p, 320x240 [PAR 1:1 DAR 4:3], q=2-31, 200 kb/s, 1k tbn, 25 tbc
    Stream #0.1: Audio: libmp3lame, 44100 Hz, 2 channels, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame= 1526 fps=182 q=12.8 Lsize=    2203kB time=61.05 bitrate= 295.6kbits/s    
video:1665kB audio:477kB global headers:0kB muxing overhead 2.831106%
```

You can see in my version there is --enable-libmp3lame. (In red)

I always compile ffmpeg myself. Use the instructions [[COLOR="Magenta"]here[/COLOR]]("http://ubuntuforums.org/showpost.php?p=4907079&postcount=1")

It`s just copy and paste.

---

### Post by spygm on 2010-05-26
still same.. any idea? are u using ubuntu 10.4?

```

spygm@ubuntu10:/var/shared/input$ ffmpeg -i 'Fate stay night - 01.avi' -y -s 320x240 -ar 44100 -acodec libmp3lame 'Fate stay night - 01.flv' 
FFmpeg version SVN-r23334, Copyright (c) 2000-2010 the FFmpeg developers
  built on May 26 2010 20:32:23 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.16. 0 / 50.16. 0
  libavcodec    52.70. 0 / 52.70. 0
  libavformat   52.66. 0 / 52.66. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.20. 0 /  1.20. 0
  libswscale     0.10. 0 /  0.10. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[mpeg4 @ 0x9a7c750]Invalid and inefficient vfw-avi packed B frames detected

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (12570329/524288)
Input #0, avi, from 'Fate stay night - 01.avi':
  Metadata:
    ISFT            : VirtualDubMod 1.5.10.1 (build 2439/release)
  Duration: 00:24:09.82, start: 0.000000, bitrate: 986 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 704x396 [PAR 1:1 DAR 16:9], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, 2 channels, s16, 128 kb/s
[scale @ 0x9ab0ac0]w:704 h:396 fmt:yuv420p -> w:320 h:240 fmt:yuv420p flags:0xa0000004
Output #0, flv, to 'Fate stay night - 01.flv':
  Metadata:
    encoder         : Lavf52.66.0
    Stream #0.0: Video: flv, yuv420p, 320x240 [PAR 4:3 DAR 16:9], q=2-31, 200 kb/s, 1k tbn, 23.98 tbc
    Stream #0.1: Audio: libmp3lame, 44100 Hz, 2 channels, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
[mpeg4 @ 0x9a7c750]Invalid and inefficient vfw-avi packed B frames detected
[COLOR=Red]**[mp3 @ 0x9a7d170]overread, skip -9 enddists: -7 -7.06 bitrate= 279.9kbits/s  <-- now got this error**[/COLOR]

```

> **nothingspecial said:**
> You still need libmp3lame.

Your command is correct, I just tried it myself.
```

ffmpeg -i Its_Flashbeagle_Charlie_Brown.avi -y -s 320x240 -ar 44100 -acodec libmp3lame test.flv 
FFmpeg version SVN-r22991, Copyright (c) 2000-2010 the FFmpeg developers
  built on Apr 30 2010 12:36:06 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad [COLOR=Red]--enable-libmp3lame[/COLOR] --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.15. 0 / 50.15. 0
  libavcodec    52.66. 0 / 52.66. 0
  libavformat   52.61. 0 / 52.61. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0.10. 0 /  0.10. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Input #0, avi, from 'Its_Flashbeagle_Charlie_Brown.avi':
  Metadata:
    ISFT            : transcode-1.1.5
  Duration: 00:23:18.92, start: 0.000000, bitrate: 6583 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 640x480 [PAR 1:1 DAR 4:3], 25 tbr, 25 tbn, 25 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, 2 channels, s16, 128 kb/s
Output #0, flv, to 'test.flv':
  Metadata:
    encoder         : Lavf52.61.0
    Stream #0.0: Video: flv, yuv420p, 320x240 [PAR 1:1 DAR 4:3], q=2-31, 200 kb/s, 1k tbn, 25 tbc
    Stream #0.1: Audio: libmp3lame, 44100 Hz, 2 channels, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame= 1526 fps=182 q=12.8 Lsize=    2203kB time=61.05 bitrate= 295.6kbits/s    
video:1665kB audio:477kB global headers:0kB muxing overhead 2.831106%
```You can see in my version there is --enable-libmp3lame. (In red)

I always compile ffmpeg myself. Use the instructions [[COLOR=Magenta]here[/COLOR]]("http://ubuntuforums.org/showpost.php?p=4907079&postcount=1")

It`s just copy and paste.

---

