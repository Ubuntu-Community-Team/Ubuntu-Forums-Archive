---
title: "mp3-files on nokia cell phone"
date: 2009-05-13
forum: Multimedia Software
---

### Post by denzlein on 2009-05-13
Hello there, I bought a new cell phone, a nokia 5310. All mp3-files that either came with the cell phone, that I downloaded from lastfm or that I bought at amazon sound just fine. But all the mp3-files that I rip myself sound awful. Whenever the bass frequencies get louder all other frequencies seem to be muffled. When the drums or bass pause, everything else gets louder again.

I tried different frontends and encoders: sound juicer + lame, rythmbox + lame, grip + lame and grip + gogo. The files sound just fine on my computer and on my mp3-player, but still terrible on my cell phone. 

Does that sound familiar to anyone? Did anyone ever encounter a problem like that? Does anyone know what causes the problem or has a solution for it?

Thanks
Peter Denzlein

---

### Post by andrew.46 on 2009-05-13
Hi denzlein,

Can I suggest that you have a look at the files you have downloaded, or those that have come with the phone and find their exact makeup? One method is with FFmpeg:

```
ffmpeg -i my_file.mp3
```

But any application that gives information on media files will do. Once you have found the bitrate, number of channels, frequency etc of the 'successful' mp3s it should be an easy matter to duplicate these settings with your own mp3s.

All the best,

Andrew

---

### Post by denzlein on 2009-05-14
Hi andrew.46,

here is the output of ffmpeg. First a file that I bought at amazon and that works fine:

> peter@peter-laptop:~/Musik/Flyleaf/Flyleaf$ ffmpeg -i 01\ -\ I\'m\ So\ Sick.mp3 
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3
[mp3 @ 0x984cd40]mdb:68, lastbuf:0 skipping granule 0
    Last message repeated 1 times
[mp3 @ 0x984cd40]mdb:68, lastbuf:0 skipping granule 1
    Last message repeated 1 times
Input #0, mp3, from '01 - I'm So Sick.mp3':
  Duration: 00:03:49.60, start: 0.000000, bitrate: 192 kb/s
    Stream #0.0: Audio: mp3, 44100 Hz, stereo, s16, 192 kb/s
At least one output file must be specifiedNext a file I ripped with grip that doesn't work on my cell phone:

> peter@peter-laptop:~/Musik/wir sind helden/soundso$ ffmpeg -i 06\ -\ labyrinth.mp3 
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3
Input #0, mp3, from '06 - labyrinth.mp3':
  Duration: 00:04:15.87, start: 0.000000, bitrate: 256 kb/s
    Stream #0.0: Audio: mp3, 44100 Hz, stereo, s16, 256 kb/s
At least one output file must be specifiedThe only important difference seems to be the two lines starting with [mp3 @ ..., but I have no idea what that means. By the way, Nautilus gives me a different bitrate for the first file, 247 kb/s and not 192 kb/s, but I don't think that is a major problem. 

Peter Denzlein

---

### Post by andrew.46 on 2009-05-14
Hi denzlein,

Hmmmm.... I was hoping for a greater difference there :-). You may have to wait or somebody to answer here who has more experience with these phones unfortunately :confused:.

A small thing to try might be to encode *directly* with lame. You could try something like:

```
lame -V 2 input.wav output.mp3
```

which would give high quality vbr with a range between 170 and 210 kbs. If the bitrate *could* be a problem try -V 4 and this should generate between 140 and 180 kbs.

This may not help at all in which case my apologies.

Andrew

---

