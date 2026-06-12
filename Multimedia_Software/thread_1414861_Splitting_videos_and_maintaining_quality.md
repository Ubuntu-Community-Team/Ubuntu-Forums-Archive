---
title: "Splitting videos and maintaining quality"
date: 2010-02-24
forum: Multimedia Software
---

### Post by garion42 on 2010-02-24
I am trying to use ffmpeg to split a number of videos of different types (WMV, MPG, AVI). I do not want to change anything else, just split them into smaller chunks. The video is split, but the quality of the output file is terrible. I would describe it as "blocky" (I think the correct term is "pixelated"). When I make the player (KMPlayer) much smaller the problem naturally goes away. 

The command I am using:

ffmpeg -i  original_vid.wmv -ss 00:00:00 -t 00:05:00 first_vid.wmv

The output:

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

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, asf, from 'original_vid.wmv':
  Duration: 00:12:12.09, start: 3.100000, bitrate: 3230 kb/s
    Stream #0.0: Video: wmv2, yuv420p, 800x600, 25 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: wmav2, 44100 Hz, stereo, s16, 160 kb/s
Output #0, asf, to 'first_vid.wmv':
    Stream #0.0: Video: msmpeg4, yuv420p, 800x600, q=2-31, 200 kb/s, 90k tbn, 25 tbc
    Stream #0.1: Audio: mp2, 44100 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame= 6773 fps= 67 q=31.0 Lsize=   24662kB time=270.92 bitrate= 745.7kbits/s    
video:21970kB audio:2117kB global headers:0kB muxing overhead 2.388148%


The line

"Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 25.00 (25/1)

Seems to mean something, but I couldn't find anything saying that this is the problem or what O should do to correct it.

Any help is appreaciated.

---

### Post by FakeOutdoorsman on 2010-02-24
> **garion42 said:**
> 
The command I am using:
```
ffmpeg -i  original_vid.wmv -ss 00:00:00 -t 00:05:00 first_vid.wmv
```

Your command is re-encoding the video.  You can avoid re-encoding by using the *-vcodec copy* and *-acodec copy* options:
```
ffmpeg -ss 00:00:00 -t 00:05:00 -i original_vid.wmv -acodec copy -vcodec copy first_vid.wmv
```
It's usually faster to place *-ss* and *-t* before the input because FFmpeg will seek first and then decode the input, but of course any potential speed difference depends on your source.  Also, -*ss* by default is 0, but it left it there for demonstration purposes.

---

### Post by Voorhees1979 on 2010-02-24
For a job like this you are better of using avidemux, very easy to split and it keeps the video exactly the same. Also only takes a few seconds to save the split file.

---

