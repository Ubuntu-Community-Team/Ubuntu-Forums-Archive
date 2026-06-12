---
title: "Gotta Stream DV input to YouTube for an Event This Weekend!"
date: 2014-05-19
forum: Multimedia Software
---

### Post by redbikemaster on 2014-05-19
Hey guys, I've been asked by a close friend to stream her wedding to out-of-state grandparents this weekend. The camera I have available is a Panasonic AG-DVX100A connected to my laptop via 1394. I already have a YouTube account with Live Events enabled, so that is what I will be streaming TO.

What I need help with is how to take the video and audio from the camera, and shoot it to YouTube. 

The camera works with Kino well, but I don't get any audio. The video is great though, so I know the video at least is working great. Kino 1. Is a dead project, and 2. doesn't seem to have an option to stream out. 

VLC seems like it would work, but I couldn't really figure out how to get the video IN correctly. The image was scrambled (but definitely coming from the camera), and the sound would randomly be loud static for a couple seconds, off and on.

dvgrab DOES work, and work beautifully. Both video and sound were stellar, but I don't know how to stream from it. I think I read somewhere about dvgrab grabbing video, and using ffmpeg to shoot it to the server, but I was really confused as it was written far above my level.

ffmpeg seems like it should be able to do everything by itself, but I can't figure out how to tell it to do it. 

I'm sure the solution is right in front of me, but I need help. :P

---

### Post by FakeOutdoorsman on 2014-05-20
I have that camera too. I haven't used it in years, but it was a workhorse.

Do you like the command line? If yes, then you can use dvgrab to pipe to ffmpeg, and from ffmpeg to YouTube via RTMP. I'm going to assume you're using NTSC instead of PAL.

First do some preliminary stuff:

1. Get ffmpeg. The version in the older Ubuntu releases (but not the not real old ones) is a [buggy counterfeit](http://stackoverflow.com/a/9477756/1109017), and avconv is not worth using in my opinion. Also, [FFmpeg development is very active](http://git.videolan.org/?p=ffmpeg.git;a=shortlog) and it is best to use a recent build with possible. You have two main options:

[list]
[*]Download a build. This is easy. Just [download](http://ffmpeg.org/download.html#LinuxBuilds), extract, and execute.
[*]Compile. This allows you to customize your build to your liking. It takes longer than simply downloading, but there is a step-by-step [FFmpeg compile guide](http://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu).
[/list]

2. Figure out your upload speed. Go to speedtest.net. For example, I have an anemic 0.5 Mbps (or 512 kilobits/s) upload rate, but lets assume I have something usable like 1 Mbps (1024 Kbps). You will need your number to optimize your encoding. Also keep in mind the download rate of your viewers. If their download is slower than your upload that may cause buffering on their end (I'm assuming YouTube doesn't re-encode your video, but I'm not sure if it does or not for live stuff).

3. Capture and encode (I didn't test this example):

```
dvgrab -size 0 -noavc - | ffmpeg -i - -vcodec libx264 -preset medium -maxrate 742k -bufsize 2970k -vf "yadif,format=yuv420p" -g 60 -acodec libmp3lame -b:a 128k -ac 2 -ar 44100 -f flv rtmp://output
```

You have to do some simple math to figure out your numbers:
[list]
[*](1024 upload rate * 0.85 since you can probably consistently utilize 85%) - 128 desired audio rate = ~742 maxrate. Good enough for standard def.
[*]742 maxrate * 4 second buffer = ~2970 bufsize.
[/list]

Other notes:
[list]
[*]DV is interlaced. The [yadif video filter](http://ffmpeg.org/ffmpeg-filters.html#yadif) is a deinterlacer.
[*]NTSC-DV uses 4:1:1 chroma subsampling. ffmpeg attempts to reduce or avoid chroma subsampling with this encoder, but that means the output can be unplayable by non-FFmpeg based players. The [format video filter](http://ffmpeg.org/ffmpeg-filters.html#format) fixes that.
[*]"-g" is your Group of Pictures. For streaming we'll use a ~2 second GOP, which means multiply your output framerate by 2. NTSC will use ~60, and PAL will use 50.
[*]If you want to stream and capture to a local file at the same time see the [tee muxer](http://ffmpeg.org/ffmpeg-formats.html#tee) and [Creating multiple outputs with FFmpeg](https://trac.ffmpeg.org/wiki/Creating%20multiple%20outputs#Teepseudo-muxer).
[*]Also see [Encoding for streaming sites with FFmpeg](http://trac.ffmpeg.org/wiki/EncodingForStreamingSites).
[/list]

---

### Post by redbikemaster on 2014-05-21
OK, so the streaming server address is rtmp://a.youtube.com/live2. So I put that in. I am also given a "Stream Name" to use. Where do I insert that? It looks like a Twitch stream key.

---

### Post by redbikemaster on 2014-05-21
```

ffmpeg version 0.8.10-4:0.8.10-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Feb  6 2014 20:59:08 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
Found AV/C device with GUID 0x00804582109c2046
libiec61883 error: Failed to get channels available.
Waiting for DV...
Capture Started
[dv @ 0x9242aa0] Estimating duration from bitrate, this may be inaccurate
Input #0, dv, from 'pipe:':
  Duration: N/A, start: 0.000000, bitrate: 28771 kb/s
    Stream #0.0: Video: dvvideo, yuv411p, 720x480, 28771 kb/s, PAR 8:9 DAR 4:3, 29.97 tbr, 29.97 tbn, 29.97 tbc
    Stream #0.1: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
Unrecognized option 'preset'
Failed to set value 'medium' for option 'preset'

```

Here is what my terminal looks like so far.

---

### Post by redbikemaster on 2014-05-21
OK, so I've been tweaking a bit. Here's the command now:

```

#!/bin/sh


dvgrab -size 0 -noavc - | ffmpeg -i - -vcodec h264 -preset fast -maxrate 742k -bufsize 2970k -vf "yadif,format=yuv420p" -g 60 -acodec libmp3lame -b:a 128k -ac 2 -ar 44100 -f flv rtmp://a.rtmp.youtube.com/live2/theredbikemaste-5173.stfp-3p18-2h53-d650

```
(Got lazy and stuck it in a script)

Here's the result:
```

ffmpeg version 0.8.10-4:0.8.10-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Feb  6 2014 20:59:08 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
Found AV/C device with GUID 0x00804582109c2046
libiec61883 error: Failed to get channels available.
Waiting for DV...
Capture Started
[dv @ 0x9b92aa0] Estimating duration from bitrate, this may be inaccurate
Input #0, dv, from 'pipe:':
  Duration: N/A, start: 0.000000, bitrate: 28771 kb/s
    Stream #0.0: Video: dvvideo, yuv411p, 720x480, 28771 kb/s, PAR 8:9 DAR 4:3, 29.97 tbr, 29.97 tbn, 29.97 tbc
    Stream #0.1: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
Unrecognized option 'preset'
Failed to set value 'fast' for option 'preset'

```

I've not been able to figure out what
```

libiec61883 error: Failed to get channels available.

```

and

```

Unrecognized option 'preset'
Failed to set value 'fast' for option 'preset'

```

mean.

---

### Post by FakeOutdoorsman on 2014-05-21
> **redbikemaster said:**
> 
Here's the result:
```

ffmpeg version 0.8.10-4:0.8.10-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Feb  6 2014 20:59:08 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.

```
This is the fake ffmpeg. I don't recommend using it.

> **redbikemaster said:**
> 
I've not been able to figure out what
```

libiec61883 error: Failed to get channels available.

```

This is from dvgrab. You can ignore this message.

> **redbikemaster said:**
> 
```

Unrecognized option 'preset'
Failed to set value 'fast' for option 'preset'

```

You're using the counterfeit ffmpeg. Use the real thing as described in my first post. Just download it and then either:

[list]
[*]put the new ffmpeg binary you downloaded in the same directory as the script, and in the script change "ffmpeg" to "./ffmpeg"
[*]or in the script provide the full path to the new ffmpeg by changing "ffmpeg" to, for example, "/home/redbike/ffmpeg"
[*]or put the new binary somewhere in your PATH, such as "sudo mv ffmpeg /usr/local/bin" then run "hash ffmpeg" to unremember the old binary location
[/list]

---

### Post by redbikemaster on 2014-05-21
OK, I added /home/redbikemaster/ffmpeg, and stuff really happened.

```

ffmpeg version N-63351-gd1a32c3 Copyright (c) 2000-2014 the FFmpeg developers
  built on May 21 2014 05:15:34 with gcc 4.6 (Debian 4.6.3-1)
  configuration: --prefix=/root/ffmpeg-static/32bit --arch=x86_32 --extra-cflags='-m32 -I/root/ffmpeg-static/32bit/include -static' --extra-ldflags='-m32 -L/root/ffmpeg-static/32bit/lib -static' --extra-libs='-lxml2 -lexpat -lfreetype' --enable-static --disable-shared --disable-ffserver --disable-doc --enable-bzlib --enable-zlib --enable-postproc --enable-runtime-cpudetect --enable-libx264 --enable-gpl --enable-libtheora --enable-libvorbis --enable-libmp3lame --enable-gray --enable-libass --enable-libfreetype --enable-libopenjpeg --enable-libspeex --enable-libvo-aacenc --enable-libvo-amrwbenc --enable-version3 --enable-libvpx
  libavutil      52. 86.100 / 52. 86.100
  libavcodec     55. 63.100 / 55. 63.100
  libavformat    55. 39.100 / 55. 39.100
  libavdevice    55. 13.101 / 55. 13.101
  libavfilter     4.  5.100 /  4.  5.100
  libswscale      2.  6.100 /  2.  6.100
  libswresample   0. 19.100 /  0. 19.100
  libpostproc    52.  3.100 / 52.  3.100
Found AV/C device with GUID 0x00804582109c2046
libiec61883 error: Failed to get channels available.
Waiting for DV...
Capture Started
Input #0, dv, from 'pipe:':
  Duration: N/A, start: 0.000000, bitrate: 28771 kb/s
    Stream #0:0: Video: dvvideo, yuv411p, 720x480 [SAR 8:9 DAR 4:3], 28771 kb/s, 29.97 fps, 29.97 tbr, 29.97 tbn, 29.97 tbc
    Stream #0:1: Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s
[libx264 @ 0xb741980] using SAR=8/9
[libx264 @ 0xb741980] using cpu capabilities: MMX2 SSE2Fast SSSE3 Cache64
[libx264 @ 0xb741980] profile High, level 3.0
[libx264 @ 0xb741980] 264 - core 129 r2230 1cffe9f - H.264/MPEG-4 AVC codec - Copyleft 2003-2012 - http://www.videolan.org/x264.html - options: cabac=1 ref=2 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=6 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=3 lookahead_threads=1 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=0 weightp=1 keyint=60 keyint_min=6 scenecut=40 intra_refresh=0 rc_lookahead=30 rc=crf mbtree=1 crf=23.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 vbv_maxrate=742 vbv_bufsize=2970 crf_max=0.0 nal_hrd=none ip_ratio=1.40 aq=1:1.00
Output #0, flv, to 'rtmp://a.rtmp.youtube.com/live2/theredbikemaste-5173.stfp-3p18-2h53-d650':
  Metadata:
    encoder         : Lavf55.39.100
    Stream #0:0: Video: h264 (libx264) ([7][0][0][0] / 0x0007), yuv420p, 720x480 [SAR 8:9 DAR 4:3], q=-1--1, max. 742 kb/s, 29.97 fps, 1k tbn, 29.97 tbc
    Metadata:
      encoder         : Lavc55.63.100 libx264
    Stream #0:1: Audio: mp3 (libmp3lame) ([2][0][0][0] / 0x0002), 44100 Hz, stereo, s16p, 128 kb/s
    Metadata:
      encoder         : Lavc55.63.100 libmp3lame
Stream mapping:
  Stream #0:0 -> #0:0 (dvvideo -> libx264)
  Stream #0:1 -> #0:1 (pcm_s16le -> libmp3lame)
frame=   31 fps=0.0 q=0.0 size=       0kB time=00:00:00.94 bitrate=   3.3kbits/sframe=   43 fps= 41 q=32.0 size=      30kB time=00:00:01.35 bitrate= 182.5kbits/frame=   59 fps= 38 q=29.0 size=      58kB time=00:00:01.88 bitrate= 253.5kbits/frame=   76 fps= 37 q=29.0 size=      84kB time=00:00:02.43 bitrate= 281.9kbits/frame=   92 fps= 36 q=29.0 size=     107kB time=00:00:02.97 bitrate= 293.9kbits/frame=  105 fps= 34 q=29.0 size=     158kB time=00:00:03.42 bitrate= 377.3kbits/frame=  119 fps= 33 q=29.0 size=     183kB time=00:00:03.89 bitrate= 384.6kbits/frame=  135 fps= 33 q=29.0 size=     207kB time=00:00:04.41 bitrate= 384.6kbits/frame=  152 fps= 33 q=29.0 size=     232kB time=00:00:04.99 bitrate= 380.7kbits/frame=  166 fps= 32 q=29.0 size=     284kB time=00:00:05.46 bitrate= 426.0kbits/frame=  182 fps= 32 q=29.0 size=     311kB time=00:00:05.98 bitrate= 425.5kbits/frame=  199 fps= 32 q=29.0 size=     339kB time=00:00:06.55 bitrate= 423.0kbits/frame=  217 fps= 32 q=29.0 size=     361kB time=00:00:07.15 bitrate= 413.1kbits/frame=  231 fps= 32 q=29.0 size=     420kB time=00:00:07.62 bitrate= 450.8kbits/frame=  248 fps= 32 q=29.0 size=     446kB time=00:00:08.15 bitrate= 448.2kbits/frame=  264 fps= 32 q=29.0 size=     470kB time=00:00:08.72 bitrate= 441.1kbits/frame=  281 fps= 32 q=29.0 size=     525kB time=00:00:09.30 bitrate= 462.6kbits/frame=  295 fps= 32 q=29.0 size=     551kB time=00:00:09.77 bitrate= 462.3kbits/frame=  312 fps= 32 q=29.0 size=     577kB time=00:00:10.31 bitrate= 458.2kbits/frame=  329 fps= 32 q=29.0 size=     602kB time=00:00:10.89 bitrate= 452.3kbits/frame=  344 fps= 32 q=29.0 size=     658kB time=00:00:11.39 bitrate= 473.1kbits/frame=  361 fps= 32 q=29.0 size=     685kB time=00:00:11.93 bitrate= 469.9kbits/frame=  377 fps= 32 q=29.0 size=     710kB time=00:00:12.48 bitrate= 465.6kbits/frame=  394 fps= 32 q=29.0 size=     734kB time=00:00:13.03 bitrate= 461.1kbits/frame=  408 fps= 32 q=29.0 size=     790kB time=00:00:13.53 bitrate= 478.1kbits/frame=  423 fps= 32 q=29.0 size=     815kB time=00:00:14.02 bitrate= 475.8kbits/frame=  440 fps= 32 q=29.0 size=     840kB time=00:00:14.57 bitrate= 471.8kbits/frame=  458 fps= 32 q=29.0 size=     894kB time=00:00:15.20 bitrate= 481.5kbits/frame=  471 fps= 32 q=29.0 size=     921kB time=00:00:15.62 bitrate= 483.0kbits/frame=  488 fps= 32 q=29.0 size=     947kB time=00:00:16.17 bitrate= 479.9kbits/frame=  504 fps= 32 q=29.0 size=     971kB time=00:00:16.74 bitrate= 474.9kbits/frame=  521 fps= 32 q=29.0 size=    1027kB time=00:00:17.26 bitrate= 487.1kbits/frame=  535 fps= 32 q=29.0 size=    1053kB time=00:00:17.76 bitrate= 485.8kbits/frame=  552 fps= 32 q=29.0 size=    1079kB time=00:00:18.33 bitrate= 481.8kbits/frame=  569 fps= 32 q=29.0 size=    1103kB time=00:00:18.91 bitrate= 477.8kbits/frame=  584 fps= 32 q=29.0 size=    1159kB time=00:00:19.35 bitrate= 490.5kbits/frame=  599 fps= 32 q=29.0 size=    1184kB time=00:00:19.90 bitrate= 487.2kbits/frame=  616 fps= 32 q=29.0 size=    1209kB time=00:00:20.48 bitrate= 483.7kbits/frame=  632 fps= 32 q=29.0 size=    1233kB time=00:00:21.00 bitrate= 481.1kbits/frame=  647 fps= 32 q=29.0 size=    1289kB time=00:00:21.50 bitrate= 491.3kbits/frame=  662 fps= 31 q=29.0 size=    1311kB time=00:00:21.99 bitrate= 488.3kbits/frame=  679 fps= 31 q=29.0 size=    1340kB time=00:00:22.57 bitrate= 486.2kbits/frame=  697 fps= 32 q=29.0 size=    1362kB time=00:00:23.14 bitrate= 482.2kbits/frame=  711 fps= 31 q=29.0 size=    1422kB time=00:00:23.64 bitrate= 492.7kbits/frame=  727 fps= 31 q=29.0 size=    1447kB time=00:00:24.16 bitrate= 490.5kbits/frame=  744 fps= 31 q=29.0 size=    1472kB time=00:00:24.73 bitrate= 487.5kbits/frame=  760 fps= 31 q=29.0 size=    1526kB time=00:00:25.28 bitrate= 494.5kbits/frame=  776 fps= 31 q=29.0 size=    1555kB time=00:00:25.78 bitrate= 493.9kbits/frame=  791 fps= 31 q=29.0 size=    1578kB time=00:00:26.30 bitrate= 491.5kbits/frame=  808 fps= 31 q=29.0 size=    1603kB time=00:00:26.85 bitrate= 488.9kbits/frame=  823 fps= 31 q=29.0 size=    1658kB time=00:00:27.37 bitrate= 496.3kbits/frame=  838 fps= 31 q=29.0 size=    1681kB time=00:00:27.87 bitrate= 494.2kbits/frame=  855 fps= 31 q=29.0 size=    1710kB time=00:00:28.42 bitrate= 492.8kbits/frame=  870 fps= 31 q=29.0 size=    1730kB time=00:00:28.94 bitrate= 489.7kbits/frame=  886 fps= 31 q=29.0 size=    1787kB time=00:00:29.44 bitrate= 497.3kbits/frame=  900 fps= 31 q=29.0 size=    1813kB time=00:00:29.93 bitrate= 496.0kbits/frame=  915 fps= 31 q=29.0 size=    1836kB time=00:00:30.40 bitrate= 494.6kbits/frame=  931 fps= 31 q=29.0 size=    1859kB time=00:00:30.98 bitrate= 491.6kbits/frame=  947 fps= 31 q=29.0 size=    1917kB time=00:00:31.50 bitrate= 498.4kbits/frame=  963 fps= 31 q=29.0 size=    1943kB time=00:00:32.05 bitrate= 496.5kbits/frame=  979 fps= 31 q=29.0 size=    1967kB time=00:00:32.57 bitrate= 494.7kbits/frame=  995 fps= 31 q=29.0 size=    1988kB time=00:00:33.12 bitrate= 491.7kbits/frame= 1009 fps= 31 q=29.0 size=    2044kB time=00:00:33.59 bitrate= 498.6kbits/frame= 1025 fps= 31 q=29.0 size=    2070kB time=00:00:34.11 bitrate= 497.2kbits/frame= 1040 fps= 31 q=29.0 size=    2094kB time=00:00:34.61 bitrate= 495.6kbits/frame= 1055 fps= 31 q=29.0 size=    2114kB time=00:00:35.11 bitrate= 493.3kbits/frame= 1071 fps= 31 q=29.0 size=    2175kB time=00:00:35.60 bitrate= 500.5kbits/frame= 1084 fps= 31 q=29.0 size=    2196kB time=00:00:36.05 bitrate= 499.0kbits/frame= 1100 fps= 31 q=29.0 size=    2220kB time=00:00:36.62 bitrate= 496.5kbits/frame= 1116 fps= 31 q=26.0 size=    2241kB time=00:00:37.14 bitrate= 494.3kbits/frame= 1131 fps= 31 q=29.0 size=    2301kB time=00:00:37.64 bitrate= 500.7kbits/frame= 1148 fps= 31 q=29.0 size=    2327kB time=00:00:38.19 bitrate= 499.2kbits/frame= 1163 fps= 31 q=29.0 size=    2351kB time=00:00:38.68 bitrate= 497.7kbits/frame= 1178 fps= 31 q=29.0 size=    2399kB time=00:00:39.21 bitrate= 501.3kbits/frame= 1195 fps= 31 q=29.0 size=    2433kB time=00:00:39.78 bitrate= 500.9kbits/frame= 1211 fps= 31 q=29.0 size=    2457kB time=00:00:40.33 bitrate= 499.0kbits/frame= 1227 fps= 31 q=29.0 size=    2480kB time=00:00:40.85 bitrate= 497.4kbits/frame= 1242 fps= 31 q=29.0 size=    2532kB time=00:00:41.32 bitrate= 501.8kbits/frame= 1256 fps= 31 q=29.0 size=    2558kB time=00:00:41.82 bitrate= 501.0kbits/frame= 1272 fps= 31 q=29.0 size=    2582kB time=00:00:42.37 bitrate= 499.2kbits/frame= 1288 fps= 31 q=29.0 size=    2606kB time=00:00:42.89 bitrate= 497.7kbits/frame= 1303 fps= 31 q=29.0 size=    2661kB time=00:00:43.36 bitrate= 502.8kbits/frame= 1318 fps= 31 q=29.0 size=    2685kB time=00:00:43.88 bitrate= 501.1kbits/frame= 1334 fps= 31 q=29.0 size=    2710kB time=00:00:44.43 bitrate= 499.5kbits/frame= 1350 fps= 31 q=29.0 size=    2734kB time=00:00:44.93 bitrate= 498.4kbits/frame= 1361 fps= 31 q=29.0 size=    2781kB time=00:00:45.32 bitrate= 502.7kbits/frame= 1377 fps= 31 q=29.0 size=    2809kB time=00:00:45.87 bitrate= 501.7kbits/frame= 1394 fps= 31 q=29.0 size=    2835kB time=00:00:46.42 bitrate= 500.3kbits/frame= 1409 fps= 31 q=29.0 size=    2858kB time=00:00:46.94 bitrate= 498.7kbits/frame= 1423 fps= 31 q=29.0 size=    2912kB time=00:00:47.38 bitrate= 503.4kbits/frame= 1439 fps= 31 q=29.0 size=    2938kB time=00:00:47.93 bitrate= 502.2kbits/frame= 1454 fps= 31 q=29.0 size=    2959kB time=00:00:48.43 bitrate= 500.5kbits/frame= 1471 fps= 31 q=29.0 size=    2986kB time=00:00:49.00 bitrate= 499.1kbits/frame= 1487 fps= 31 q=29.0 size=    3044kB time=00:00:49.52 bitrate= 503.4kbits/frame= 1503 fps= 31 q=29.0 size=    3070kB time=00:00:50.07 bitrate= 502.1kbits/frame= 1518 fps= 31 q=29.0 size=    3090kB time=00:00:50.57 bitrate= 500.6kbits/frame= 1534 fps= 31 q=29.0 size=    3115kB time=00:00:51.09 bitrate= 499.4kbits/frame= 1549 fps= 31 q=29.0 size=    3172kB time=00:00:51.59 bitrate= 503.6kbits/frame= 1564 fps= 31 q=29.0 size=    3197kB time=00:00:52.08 bitrate= 502.7kbits/frame= 1580 fps= 31 q=29.0 size=    3221kB time=00:00:52.61 bitrate= 501.5kbits/frame= 1595 fps= 31 q=29.0 size=    3241kB time=00:00:53.13 bitrate= 499.7kbits/frame= 1610 fps= 31 q=29.0 size=    3298kB time=00:00:53.60 bitrate= 504.0kbits/frame= 1625 fps= 31 q=29.0 size=    3322kB time=00:00:54.12 bitrate= 502.8kbits/frame= 1641 fps= 31 q=29.0 size=    3346kB time=00:00:54.64 bitrate= 501.6kbits/frame= 1656 fps= 31 q=26.0 size=    3366kB time=00:00:55.17 bitrate= 499.9kbits/frame= 1671 fps= 31 q=29.0 size=    3427kB time=00:00:55.64 bitrate= 504.5kbits/frame= 1686 fps= 31 q=29.0 size=    3448kB time=00:00:56.16 bitrate= 503.0kbits/frame= 1702 fps= 31 q=29.0 size=    3473kB time=00:00:56.66 bitrate= 502.1kbits/frame= 1717 fps= 31 q=29.0 size=    3493kB time=00:00:57.18 bitrate= 500.4kbits/frame= 1731 fps= 31 q=29.0 size=    3551kB time=00:00:57.67 bitrate= 504.4kbits/frame= 1747 fps= 31 q=29.0 size=    3577kB time=00:00:58.20 bitrate= 503.4kbits/frame= 1763 fps= 31 q=29.0 size=    3601kB time=00:00:58.75 bitrate= 502.1kbits/frame= 1779 fps= 31 q=29.0 size=    3656kB time=00:00:59.24 bitrate= 505.5kbits/frame= 1793 fps= 31 q=29.0 size=    3679kB time=00:00:59.74 bitrate= 504.5kbits/frame= 1809 fps= 31 q=29.0 size=    3705kB time=00:01:00.26 bitrate= 503.6kbits/frame= 1825 fps= 31 q=29.0 size=    3728kB time=00:01:00.78 bitrate= 502.5kbits/frame= 1839 fps= 31 q=29.0 size=    3782kB time=00:01:01.28 bitrate= 505.5kbits/frame= 1855 fps= 31 q=29.0 size=    3810kB time=00:01:01.80 bitrate= 505.0kbits/frame= 1871 fps= 31 q=29.0 size=    3834kB time=00:01:02.35 bitrate= 503.8kbits/frame= 1887 fps= 31 q=29.0 size=    3858kB time=00:01:02.87 bitrate= 502.7kbits/frame= 1903 fps= 31 q=29.0 size=    3914kB time=00:01:03.40 bitrate= 505.8kbits/frame= 1919 fps= 31 q=29.0 size=    3942kB time=00:01:03.94 bitrate= 505.0kbits/frame= 1935 fps= 31 q=29.0 size=    3966kB time=00:01:04.47 bitrate= 504.0kbits/frame= 1951 fps= 31 q=29.0 size=    3990kB time=00:01:05.02 bitrate= 502.7kbits/frame= 1966 fps= 31 q=29.0 size=    4044kB time=00:01:05.51 bitrate= 505.7kbits/frame= 1983 fps= 31 q=29.0 size=    4074kB time=00:01:06.03 bitrate= 505.4kbits/frame= 1998 fps= 31 q=29.0 size=    4095kB time=00:01:06.58 bitrate= 503.8kbits/frame= 2013 fps= 31 q=29.0 size=    4118kB time=00:01:07.08 bitrate= 502.9kbits/frame= 2027 fps= 31 q=29.0 size=    4174kB time=00:01:07.55 bitrate= 506.1kbits/frame= 2043 fps= 31 q=29.0 size=    4200kB time=00:01:08.07 bitrate= 505.4kbits/frame= 2058 fps= 31 q=29.0 size=    4221kB time=00:01:08.57 bitrate= 504.3kbits/frame= 2073 fps= 31 q=29.0 size=    4244kB time=00:01:09.09 bitrate= 503.1kbits/frame= 2088 fps= 31 q=29.0 size=    4300kB time=00:01:09.59 bitrate= 506.2kbits/frame= 2104 fps= 31 q=29.0 size=    4326kB time=00:01:10.11 bitrate= 505.4kbits/frame= 2119 fps= 31 q=29.0 size=    4349kB time=00:01:10.61 bitrate= 504.5kbits/frame= 2135 fps= 31 q=29.0 size=    4370kB time=00:01:11.15 bitrate= 503.1kbits/frame= 2150 fps= 31 q=29.0 size=    4428kB time=00:01:11.65 bitrate= 506.2kbits/frame= 2166 fps= 31 q=29.0 size=    4453kB time=00:01:12.15 bitrate= 505.6kbits/frame= 2181 fps= 31 q=29.0 size=    4477kB time=00:01:12.70 bitrate= 504.4kbits/frame= 2196 fps= 31 q=26.0 size=    4497kB time=00:01:13.19 bitrate= 503.3kbits/frame= 2211 fps= 30 q=29.0 size=    4558kB time=00:01:13.69 bitrate= 506.7kbits/frame= 2227 fps= 30 q=29.0 size=    4583kB time=00:01:14.21 bitrate= 505.9kbits/frame= 2243 fps= 30 q=29.0 size=    4607kB time=00:01:14.76 bitrate= 504.8kbits/frame= 2258 fps= 30 q=29.0 size=    4656kB time=00:01:15.26 bitrate= 506.8kbits/frame= 2275 fps= 30 q=29.0 size=    4690kB time=00:01:15.83 bitrate= 506.6kbits/frame= 2291 fps= 30 q=29.0 size=    4715kB time=00:01:16.35 bitrate= 505.8kbits/frame= 2307 fps= 30 q=29.0 size=    4738kB time=00:01:16.90 bitrate= 504.7kbits/frame= 2322 fps= 30 q=29.0 size=    4790kB time=00:01:17.40 bitrate= 506.9kbits/frame= 2337 fps= 30 q=29.0 size=    4816kB time=00:01:17.89 bitrate= 506.5kbits/frame= 2353 fps= 30 q=29.0 size=    4841kB time=00:01:18.42 bitrate= 505.7kbits/frame= 2368 fps= 30 q=29.0 size=    4864kB time=00:01:18.91 bitrate= 504.9kbits/frame= 2383 fps= 30 q=29.0 size=    4920kB time=00:01:19.43 bitrate= 507.3kbits/frame= 2399 fps= 30 q=29.0 size=    4946kB time=00:01:19.96 bitrate= 506.7kbits/frame= 2415 fps= 30 q=29.0 size=    4970kB time=00:01:20.45 bitrate= 506.1kbits/frame= 2430 fps= 30 q=29.0 size=    4991kB time=00:01:21.00 bitrate= 504.7kbits/frame= 2445 fps= 30 q=29.0 size=    5046kB time=00:01:21.50 bitrate= 507.2kbits/frame= 2460 fps= 30 q=29.0 size=    5072kB time=00:01:21.99 bitrate= 506.8kbits/frame= 2476 fps= 30 q=29.0 size=    5097kB time=00:01:22.52 bitrate= 505.9kbits/frame= 2491 fps= 30 q=29.0 size=    5120kB time=00:01:23.04 bitrate= 505.1kbits/frame= 2507 fps= 30 q=29.0 size=    5178kB time=00:01:23.56 bitrate= 507.6kbits/frame= 2523 fps= 30 q=29.0 size=    5204kB time=00:01:24.08 bitrate= 507.0kbits/frame= 2539 fps= 30 q=29.0 size=    5228kB time=00:01:24.63 bitrate= 506.0kbits/frame= 2555 fps= 30 q=29.0 size=    5249kB time=00:01:25.13 bitrate= 505.1kbits/frame= 2570 fps= 30 q=29.0 size=    5307kB time=00:01:25.65 bitrate= 507.5kbits/frame= 2586 fps= 30 q=29.0 size=    5332kB time=00:01:26.17 bitrate= 506.9kbits/frame= 2601 fps= 30 q=29.0 size=    5355kB time=00:01:26.70 bitrate= 506.0kbits/frame= 2616 fps= 30 q=26.0 size=    5376kB time=00:01:27.19 bitrate= 505.0kbits/frame= 2631 fps= 30 q=29.0 size=    5436kB time=00:01:27.69 bitrate= 507.8kbits/frame= 2647 fps= 30 q=29.0 size=    5461kB time=00:01:28.24 bitrate= 507.0kbits/frame= 2663 fps= 30 q=29.0 size=    5485kB time=00:01:28.76 bitrate= 506.2kbits/frame= 2678 fps= 30 q=29.0 size=    5534kB time=00:01:29.26 bitrate= 507.9kbits/frame= 2694 fps= 30 q=29.0 size=    5564kB time=00:01:29.78 bitrate= 507.7kbits/frame= 2709 fps= 30 q=29.0 size=    5589kB time=00:01:30.30 bitrate= 507.0kbits/frame= 2724 fps= 30 q=29.0 size=    5612kB time=00:01:30.80 bitrate= 506.3kbits/frame= 2739 fps= 30 q=29.0 size=    5666kB time=00:01:31.29 bitrate= 508.4kbits/frame= 2755 fps= 30 q=29.0 size=    5694kB time=00:01:31.84 bitrate= 507.8kbits/frame= 2771 fps= 30 q=29.0 size=    5719kB time=00:01:32.37 bitrate= 507.2kbits/frame= 2787 fps= 30 q=29.0 size=    5742kB time=00:01:32.86 bitrate= 506.5kbits/frame= 2801 fps= 30 q=29.0 size=    5793kB time=00:01:33.33 bitrate= 508.5kbits/frame= 2815 fps= 30 q=29.0 size=    5820kB time=00:01:33.83 bitrate= 508.1kbits/frame= 2832 fps= 30 q=29.0 size=    5845kB time=00:01:34.40 bitrate= 507.2kbits/frame= 2850 fps= 30 q=29.0 size=    5870kB time=00:01:35.00 bitrate= 506.2kbits/frame= 2865 fps= 30 q=29.0 size=    5926kB time=00:01:35.50 bitrate= 508.3kbits/frame= 2879 fps= 30 q=29.0 size=    5951kB time=00:01:35.97 bitrate= 507.9kbits/frame= 2897 fps= 30 q=29.0 size=    5977kB time=00:01:36.57 bitrate= 507.0kbits/frame= 2911 fps= 30 q=29.0 size=    5999kB time=00:01:37.04 bitrate= 506.4kbits/frame= 2927 fps= 30 q=29.0 size=    6056kB time=00:01:37.56 bitrate= 508.5kbits/frame= 2943 fps= 30 q=29.0 size=    6082kB time=00:01:38.11 bitrate= 507.8kbits/frame= 2959 fps= 30 q=29.0 size=    6106kB time=00:01:38.61 bitrate= 507.3kbits/frame= 2974 fps= 30 q=29.0 size=    6126kB time=00:01:39.16 bitrate= 506.1kbits/frame= 2985 fps= 30 q=29.0 size=    6176kB time=00:01:39.52 bitrate= 508.4kbits/frame= 3002 fps= 30 q=29.0 size=    6203kB time=00:01:40.07 bitrate= 507.8kbits/frame= 3019 fps= 30 q=29.0 size=    6231kB time=00:01:40.65 bitrate= 507.2kbits/frame= 3036 fps= 30 q=26.0 size=    6253kB time=00:01:41.22 bitrate= 506.0kbits/frame= 3051 fps= 30 q=29.0 size=    6313kB time=00:01:41.72 bitrate= 508.4kbits/frame= 3067 fps= 30 q=29.0 size=    6338kB time=00:01:42.24 bitrate= 507.8kbits/frame= 3084 fps= 30 q=29.0 size=    6363kB time=00:01:42.81 bitrate= 506.9kbits/frame= 3100 fps= 30 q=29.0 size=    6417kB time=00:01:43.34 bitrate= 508.7kbits/frame= 3116 fps= 30 q=29.0 size=    6445kB time=00:01:43.86 bitrate= 508.3kbits/frame= 3131 fps= 30 q=29.0 size=    6469kB time=00:01:44.38 bitrate= 507.7kbits/frame= 3147 fps= 30 q=29.0 size=    6492kB time=00:01:44.90 bitrate= 507.0kbits/frame= 3162 fps= 30 q=29.0 size=    6544kB time=00:01:45.43 bitrate= 508.5kbits/frame= 3178 fps= 30 q=29.0 size=    6572kB time=00:01:45.95 bitrate= 508.1kbits/frame= 3194 fps= 30 q=29.0 size=    6596kB time=00:01:46.45 bitrate= 507.6kbits/frame= 3209 fps= 30 q=29.0 size=    6614kB time=00:01:46.94 bitrate= 506.7kbits/frame= 3219 fps= 30 q=29.0 size=    6665kB time=00:01:47.31 bitrate= 508.8kbits/frame= 3230 fps= 30 q=29.0 size=    6719kB time=00:01:47.67 bitrate= 511.2kbits/frame= 3241 fps= 30 q=29.0 size=    6775kB time=00:01:48.07 bitrate= 513.6kbits/frame= 3255 fps= 30 q=29.0 size=    6827kB time=00:01:48.48 bitrate= 515.5kbits/frame= 3270 fps= 30 q=29.0 size=    6849kB time=00:01:49.03 bitrate= 514.6kbits/frame= 3286 fps= 30 q=29.0 size=    6906kB time=00:01:49.55 bitrate= 516.4kbits/frame= 3303 fps= 30 q=29.0 size=    6936kB time=00:01:50.13 bitrate= 515.9kbits/frame= 3320 fps= 30 q=29.0 size=    6960kB time=00:01:50.68 bitrate= 515.1kbits/frame= 3337 fps= 30 q=29.0 size=    6981kB time=00:01:51.25 bitrate= 514.0kbits/frame= 3351 fps= 30 q=29.0 size=    7041kB time=00:01:51.72 bitrate= 516.2kbits/frame= 3367 fps= 30 q=29.0 size=    7066kB time=00:01:52.24 bitrate= 515.7kbits/frame= 3385 fps= 30 q=29.0 size=    7091kB time=00:01:52.82 bitrate= 514.9kbits/frame= 3400 fps= 30 q=29.0 size=    7145kB time=00:01:53.32 bitrate= 516.5kbits/frame= 3415 fps= 30 q=29.0 size=    7172kB time=00:01:53.86 bitrate= 515.9kbits/frame= 3432 fps= 30 q=29.0 size=    7197kB time=00:01:54.44 bitrate= 515.2kbits/frame= 3449 fps= 30 q=29.0 size=    7221kB time=00:01:54.99 bitrate= 514.4kbits/frame= 3464 fps= 30 q=29.0 size=    7277kB time=00:01:55.48 bitrate= 516.2kbits/frame= 3480 fps= 30 q=29.0 size=    7303kB time=00:01:56.03 bitrate= 515.6kbits/frame= 3497 fps= 30 q=29.0 size=    7329kB time=00:01:56.61 bitrate= 514.9kbits/frame= 3514 fps= 30 q=29.0 size=    7353kB time=00:01:57.13 bitrate= 514.2kbits/frame= 3529 fps= 30 q=29.0 size=    7409kB time=00:01:57.65 bitrate= 515.9kbits/frame= 3546 fps= 30 q=29.0 size=    7436kB time=00:01:58.20 bitrate= 515.3kbits/frame= 3562 fps= 30 q=29.0 size=    7459kB time=00:01:58.78 bitrate= 514.5kbits/^C[flv @ 0xb7411a0] Failed to update header with correct duration.
[flv @ 0xb7411a0] Failed to update header with correct filesize.
frame= 3564 fps= 30 q=-1.0 Lsize=    7544kB time=00:01:58.90 bitrate= 519.7kbits/s    
video:5544kB audio:1858kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: 1.906750%
[libx264 @ 0xb741980] frame I:60    Avg QP:21.81  size: 31933
[libx264 @ 0xb741980] frame P:899   Avg QP:24.36  size:  3312
[libx264 @ 0xb741980] frame B:2605  Avg QP:25.31  size:   301
[libx264 @ 0xb741980] consecutive B-frames:  1.7%  0.8%  5.2% 92.3%
[libx264 @ 0xb741980] mb I  I16..4: 11.1% 66.0% 23.0%
[libx264 @ 0xb741980] mb P  I16..4:  0.1%  0.1%  0.0%  P16..4: 35.0%  4.8%  4.6%  0.0%  0.0%    skip:55.4%
[libx264 @ 0xb741980] mb B  I16..4:  0.4%  0.3%  0.0%  B16..8:  4.5%  0.3%  0.0%  direct: 3.2%  skip:91.3%  L0:47.8% L1:50.3% BI: 1.9%
[libx264 @ 0xb741980] 8x8 transform intra:59.9% inter:70.4%
[libx264 @ 0xb741980] coded y,uvDC,uvAC intra: 68.6% 67.9% 30.1% inter: 4.3% 6.7% 0.0%
[libx264 @ 0xb741980] i16 v,h,dc,p: 13% 31% 19% 37%
[libx264 @ 0xb741980] i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 12% 30% 23%  5%  6%  5%  7%  5%  8%
[libx264 @ 0xb741980] i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 18% 31% 12%  6%  8%  6%  8%  5%  6%
[libx264 @ 0xb741980] i8c dc,h,v,p: 48% 33% 16%  3%
[libx264 @ 0xb741980] Weighted P-Frames: Y:0.0% UV:0.0%
[libx264 @ 0xb741980] ref P L0: 44.9% 55.1%
[libx264 @ 0xb741980] ref B L0: 57.0% 43.0%
[libx264 @ 0xb741980] ref B L1: 85.5% 14.5%
[libx264 @ 0xb741980] kb/s:381.87
Received signal 2: terminating.

```

Sorry, it's massive. OK, so YouTube started to see something, but video or audio never came up. Will keep tweaking.

I could've sworn I uninstalled the fake ffmpeg. Will fix that.

---

### Post by redbikemaster on 2014-05-21
```

frame= 2111 fps= 30 q=29.0 size=    4383kB time=00:01:10.34 bitrate= 510.3kbits/frame= 2127 fps= 30 q=29.0 size=    4405kB time=00:01:10.89 bitrate= 509.0kbits/frame= 2143 fps= 30 q=29.0 size=    4462kB time=00:01:11.39 bitrate= 512.0kbits/frame= 2158 fps= 30 q=29.0 size=    4485kB time=00:01:11.91 bitrate= 510.9kbits/frame= 2174 fps= 30 q=29.0 size=    4509kB time=00:01:12.41 bitrate= 510.1kbits/^C   
pipe:: Input/output error
[flv @ 0xb9f81c0] Failed to update header with correct duration.
[flv @ 0xb9f81c0] Failed to update header with correct filesize.
frame= 2176 fps= 23 q=-1.0 Lsize=    4592kB time=00:01:12.62 bitrate= 518.0kbits/s    
video:3371kB audio:1135kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: 1.916490%

```

Ran it for a bit, then got this.

Here's YouTube's page on recommended settings:[https://support.google.com/youtube/answer/2853702?hl=en](https://support.google.com/youtube/answer/2853702?hl=en)

---

### Post by FakeOutdoorsman on 2014-05-22
Can you show the command you used? I'll give it a try tomorrow too.

You don't need to uninstall the fake ffmpeg if you have other programs that depend on it. It can co-exist with your new one since the new one will not interfere with anything.

---

### Post by redbikemaster on 2014-05-22
[ATTACH]253359[/ATTACH]

Here's my script

---

### Post by FakeOutdoorsman on 2014-05-22
I streamed a Hi8 tape via dvgrab for 10 minutes with no issues.

You simply copied my example numbers for -maxrate and -bufsize. You should to come up with your own numbers. Get your upload rate from speedtest.net and then see "You have to do some simple math to figure out your numbers" in my first post for instructions.

---

### Post by redbikemaster on 2014-05-22
My problem with that is I don't have access to the site until the event tomorrow. I may even have to run through a 4G hotspot, rather than broadband. I simply don't know what speed I will have to work with.

---

### Post by redbikemaster on 2014-05-22
Just found out the place has no Wi-Fi. No available Internet connection. I'm going to have to try a 4G hotspot, which according to what I've found so far, should be able to support 360p video. Worst case scenario, I just record and upload elsewhere.

---

### Post by redbikemaster on 2014-05-22
We've officially given up on the streaming. I'll just record via dvgrab to a file. Thanks so much for the help though!

---

