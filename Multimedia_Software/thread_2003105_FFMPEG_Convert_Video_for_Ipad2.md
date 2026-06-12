---
title: "FFMPEG Convert Video for Ipad2"
date: 2012-06-13
forum: Multimedia Software
---

### Post by RichardC400 on 2012-06-13
I have this Ipad, I have video files on my laptop;
 .flv , .avi , .mp4 , .mkv
I tried simply converting a movie trailer (.flv) to mp4 by doing


ffmpeg -i trailer.flv output.mp4
It transfered but once I tried to drag it and drop it into iTunes(on a windows7 virtualbox) it wouldn't put it onto the iPad

So, for the past 6 hours i have been going through the internets for either software or a commandline to transfer them for me.

I've been through about 6 pieces of software which constantly failed. 

I also tried using..
```
ffmpeg -i INPUT -acodec aac -ab 160000 -s 1024x768 -vcodec libx264 -vpre slow -vpre ipod640 -b 1200kb -threads 0 -f mp4 OUTPUT.mp4
```
but my ffmpeg didn't understand -vpre, slow, ipod640, -b 1200kb
so I got rid of them and put in "-strictly experimental"
after.. a long time it didn't transfer to the Ipad.

At the minute I am trying one last piece of software and:

```

ffmpeg -i trailer.flv -s 320x240 -r 30000/1001 -b 200k -bt 240k -vcodec libx264 -coder 0 -bf 0 -refs 1 -flags2 -wpred-dct8x8 -level 30 -maxrate 10M -bufsize 10M -acodec libfaac -ac 2 -ar 48000 -ab 192k OUTPUT.mp4

```

I just have to wait for an iTunes update because it's throwing up errors and not even connecting to my iPad now.

I'll update after i've tried them both but I am not holding my breath.

My question to you guys is:
What is the commandline, or, what is good software to do this convert?

~~ffmpeg failed and the other software failed~~

---

### Post by RichardC400 on 2012-06-14
Bump?

---

### Post by FakeOutdoorsman on 2012-06-15
> **RichardC400 said:**
> I also tried using..
```
ffmpeg -i INPUT -acodec aac -ab 160000 -s 1024x768 -vcodec libx264 -vpre slow -vpre ipod640 -b 1200kb -threads 0 -f mp4 OUTPUT.mp4
```
This command should not work with ffmpeg from the repository:
```
[NULL @ 0x72c400] [Eval @ 0x7fffd626bfd0] Invalid chars 'b' at the end of expression '1200kb'
[NULL @ 0x72c400] Unable to parse option value "1200kb"
Invalid value '1200kb' for option 'b'
```
Meaning that the user would need to replace "kb" with "k". So, I assume you're using some other version or perhaps compiled it yourself. Or is this the problem you encountered?

> **RichardC400 said:**
> but my ffmpeg didn't understand -vpre, slow, ipod640, -b 1200kb
Showing the complete console output that you get from your ffmpeg command is always recommended with ffmpeg usage questions. It will show exactly why ffmpeg, "didn't understand -vpre, slow, ipod640, -b 1200kb", otherwise it's a guessing game.

> **RichardC400 said:**
> At the minute I am trying one last piece of software and:
```

ffmpeg -i trailer.flv -s 320x240 -r 30000/1001 -b 200k -bt 240k -vcodec libx264 -coder 0 -bf 0 -refs 1 -flags2 -wpred-dct8x8 -level 30 -maxrate 10M -bufsize 10M -acodec libfaac -ac 2 -ar 48000 -ab 192k OUTPUT.mp4

```
Declaring a variety of libx264 options is the old method of using this encoder and is not recommended. Stick with the presets; it's easier and will provide proper settings.

---

### Post by RichardC400 on 2012-06-16
```

:~$
ffmpeg -i INPUT.flv -acodec aac -ab 160000 -s 1024x768 -vcodec libx264 -vpre slow -vpre ipod640 -b 1200kb -threads 0 -f mp4 OUTPUT.mp4


ffmpeg version N-31140-g3074f03, Copyright (c) 2000-2011 the FFmpeg developers
  built on Jul  2 2011 07:31:42 with gcc 4.5.2
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil    51. 11. 0 / 51. 11. 0
  libavcodec   53.  7. 0 / 53.  7. 0
  libavformat  53.  5. 0 / 53.  5. 0
  libavdevice  53.  2. 0 / 53.  2. 0
  libavfilter   2. 24. 1 /  2. 24. 1
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  51.  2. 0 / 51.  2. 0
[flv @ 0xa974340] Estimating duration from bitrate, this may be inaccurate
Input #0, flv, from 'INPUT.flv':
  Metadata:
    duration        : 70
    starttime       : 0
    totalduration   : 70
    width           : 480
    height          : 360
    videodatarate   : 135
    audiodatarate   : 97
    totaldatarate   : 241
    framerate       : 30
    bytelength      : 2104748
    canseekontime   : true
    sourcedata      : B4A7D6104HH1326599994454481
    purl            : 
    pmsg            : 
  Duration: 00:01:09.96, start: 0.000000, bitrate: 237 kb/s
    Stream #0.0: Video: h264 (Main), yuv420p, 480x360 [PAR 1:1 DAR 4:3], 138 kb/s, 30 tbr, 1k tbn, 60 tbc
    Stream #0.1: Audio: aac, 44100 Hz, stereo, s16, 99 kb/s
File for preset 'slow' not found

```

and so, I remove slow

```

:~$ ffmpeg -i INPUT.flv -acodec aac -ab 160000 -s 1024x768 -vcodec libx264  -vpre ipod640 -b 1200kb -threads 0 -f mp4 OUTPUT.mp4
ffmpeg version N-31140-g3074f03, Copyright (c) 2000-2011 the FFmpeg developers
  built on Jul  2 2011 07:31:42 with gcc 4.5.2
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil    51. 11. 0 / 51. 11. 0
  libavcodec   53.  7. 0 / 53.  7. 0
  libavformat  53.  5. 0 / 53.  5. 0
  libavdevice  53.  2. 0 / 53.  2. 0
  libavfilter   2. 24. 1 /  2. 24. 1
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  51.  2. 0 / 51.  2. 0
[flv @ 0x9c80340] Estimating duration from bitrate, this may be inaccurate
Input #0, flv, from 'INPUT.flv':
  Metadata:
    duration        : 70
    starttime       : 0
    totalduration   : 70
    width           : 480
    height          : 360
    videodatarate   : 135
    audiodatarate   : 97
    totaldatarate   : 241
    framerate       : 30
    bytelength      : 2104748
    canseekontime   : true
    sourcedata      : B4A7D6104HH1326599994454481
    purl            : 
    pmsg            : 
  Duration: 00:01:09.96, start: 0.000000, bitrate: 237 kb/s
    Stream #0.0: Video: h264 (Main), yuv420p, 480x360 [PAR 1:1 DAR 4:3], 138 kb/s, 30 tbr, 1k tbn, 60 tbc
    Stream #0.1: Audio: aac, 44100 Hz, stereo, s16, 99 kb/s
[NULL @ 0x9c84d60] [Eval @ 0xbfda439c] Invalid chars 'b' at the end of expression '1200kb'
[NULL @ 0x9c84d60] Unable to parse option value "1200kb"
Invalid value '1200kb' for option 'b'

```

and so, I shall change kb to k.. as suggested.

```


:~$ ffmpeg -i INPUT.flv -acodec aac -ab 160000 -s 1024x768 -vcodec libx264  -vpre ipod640 -b 1200k -threads 0 -f mp4 OUTPUT.mp4
ffmpeg version N-31140-g3074f03, Copyright (c) 2000-2011 the FFmpeg developers
  built on Jul  2 2011 07:31:42 with gcc 4.5.2
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil    51. 11. 0 / 51. 11. 0
  libavcodec   53.  7. 0 / 53.  7. 0
  libavformat  53.  5. 0 / 53.  5. 0
  libavdevice  53.  2. 0 / 53.  2. 0
  libavfilter   2. 24. 1 /  2. 24. 1
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  51.  2. 0 / 51.  2. 0
[flv @ 0xaba6340] Estimating duration from bitrate, this may be inaccurate
Input #0, flv, from 'INPUT.flv':
  Metadata:
    duration        : 70
    starttime       : 0
    totalduration   : 70
    width           : 480
    height          : 360
    videodatarate   : 135
    audiodatarate   : 97
    totaldatarate   : 241
    framerate       : 30
    bytelength      : 2104748
    canseekontime   : true
    sourcedata      : B4A7D6104HH1326599994454481
    purl            : 
    pmsg            : 
  Duration: 00:01:09.96, start: 0.000000, bitrate: 237 kb/s
    Stream #0.0: Video: h264 (Main), yuv420p, 480x360 [PAR 1:1 DAR 4:3], 138 kb/s, 30 tbr, 1k tbn, 60 tbc
    Stream #0.1: Audio: aac, 44100 Hz, stereo, s16, 99 kb/s
encoder 'aac' is experimental and might produce bad results.
Add '-strict experimental' if you want to use it.
Or use the non experimental encoder 'libfaac'.

```

so, following instruction of this I will insert: -strict experimental
which throws out no errors. 

// on reflection the -vpre issue is my own misunderstanding. the first time I removed 'slow' i only got rid of the word 'slow' so I was left with an empty "-vpre" (which i'm guessing is a preset) so when i ran that it said something about -vpre not being understood so I got rid of both, including the one infront of... ipod640.. which in turn threw up an error about... ipod640 so I removed it. //


```

:~$ ffmpeg -i INPUT.flv -acodec aac -ab 160000 -s 1024x768 -vcodec libx264  -vpre ipod640 -b 1200k -strict experimental -threads 0 -f mp4 OUTPUT.mp4

ffmpeg version N-31140-g3074f03, Copyright (c) 2000-2011 the FFmpeg developers
  built on Jul  2 2011 07:31:42 with gcc 4.5.2
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil    51. 11. 0 / 51. 11. 0
  libavcodec   53.  7. 0 / 53.  7. 0
  libavformat  53.  5. 0 / 53.  5. 0
  libavdevice  53.  2. 0 / 53.  2. 0
  libavfilter   2. 24. 1 /  2. 24. 1
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  51.  2. 0 / 51.  2. 0
[flv @ 0x8f1a340] Estimating duration from bitrate, this may be inaccurate
Input #0, flv, from 'INPUT.flv':
  Metadata:
    duration        : 70
    starttime       : 0
    totalduration   : 70
    width           : 480
    height          : 360
    videodatarate   : 135
    audiodatarate   : 97
    totaldatarate   : 241
    framerate       : 30
    bytelength      : 2104748
    canseekontime   : true
    sourcedata      : B4A7D6104HH1326599994454481
    purl            : 
    pmsg            : 
  Duration: 00:01:09.96, start: 0.000000, bitrate: 237 kb/s
    Stream #0.0: Video: h264 (Main), yuv420p, 480x360 [PAR 1:1 DAR 4:3], 138 kb/s, 30 tbr, 1k tbn, 60 tbc
    Stream #0.1: Audio: aac, 44100 Hz, stereo, s16, 99 kb/s
[buffer @ 0x8f1b3a0] w:480 h:360 pixfmt:yuv420p tb:1/1000000 sar:1/1 sws_param:
[scale @ 0x8f1f220] w:480 h:360 fmt:yuv420p -> w:1024 h:768 fmt:yuv420p flags:0x4
[libx264 @ 0x8f1f320] Default settings detected, using medium profile
[libx264 @ 0x8f1f320] using SAR=1/1
[libx264 @ 0x8f1f320] frame MB size (64x48) > level limit (1620)
[libx264 @ 0x8f1f320] DPB size (4 frames, 4718592 bytes) > level limit (2 frames, 3110400 bytes)
[libx264 @ 0x8f1f320] MB rate (92160) > level limit (40500)
[libx264 @ 0x8f1f320] using cpu capabilities: MMX2 SSE2Fast SSSE3 FastShuffle Cache64
[libx264 @ 0x8f1f320] profile High, level 3.0
[libx264 @ 0x8f1f320] 264 - core 115 r2008 4c552d8 - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - http://www.videolan.org/x264.html - options: cabac=1 ref=3 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=7 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=3 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=0 weightp=0 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=abr mbtree=1 bitrate=1200 ratetol=1.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 vbv_maxrate=10000 vbv_bufsize=10000 nal_hrd=none ip_ratio=1.40 aq=1:1.00
Output #0, mp4, to 'OUTPUT.mp4':
  Metadata:
    duration        : 70
    starttime       : 0
    totalduration   : 70
    width           : 480
    height          : 360
    videodatarate   : 135
    audiodatarate   : 97
    totaldatarate   : 241
    framerate       : 30
    bytelength      : 2104748
    canseekontime   : true
    sourcedata      : B4A7D6104HH1326599994454481
    purl            : 
    pmsg            : 
    encoder         : Lavf53.5.0
    Stream #0.0: Video: libx264, yuv420p, 1024x768 [PAR 1:1 DAR 4:3], q=2-31, 1200 kb/s, 30 tbn, 30 tbc
    Stream #0.1: Audio: libfaac, 44100 Hz, stereo, s16, 160 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop, [?] for help
frame=   46 fps=  0 q=0.0 size=       0kB time=00:00:00.00 bitrate=   0.0kbits/sframe=   56 fps= 47 q=34.0 size=      42kB time=00:00:00.23 bitrate=1489.0kbits/frame=   70 fps= 41 q=30.0 size=      92kB time=00:00:00.70 bitrate=1077.8kbits/frame=   83 fps= 37 q=29.0 size=     143kB time=00:00:01.13 bitrate=1035.3kbits/frame=   97 fps= 35 q=25.0 size=     173kB time=00:00:01.60 bitrate= 887.6kbits/frame=  108 fps= 32 q=23.0 size=     256kB time=00:00:01.96 bitrate=1066.7kbits/frame=  126 fps= 33 q=23.0 size=     280kB time=00:00:02.56 bitrate= 893.4kbits/frame=  137 fps= 31 q=22.0 size=     312kB time=00:00:02.93 bitrate= 872.0kbits/frame=  151 fps= 30 q=18.0 size=     330kB time=00:00:03.40 bitrate= 795.8kbits/frame=  165 fps= 29 q=18.0 size=     445kB time=00:00:03.86 bitrate= 942.9kbits/frame=  181 fps= 29 q=19.0 size=     483kB time=00:00:04.40 bitrate= 899.9kbits/frame=  197 fps= 29 q=17.0 size=     520kB time=00:00:04.93 bitrate= 863.8kbits/frame=  207 fps= 29 q=15.0 size=     543kB time=00:00:05.26 bitrate= 844.4kbits/frame=  222 fps= 29 q=15.0 size=     561kB time=00:00:05.76 bitrate= 796.4kbits/frame=  230 fps= 28 q=15.0 size=     712kB time=00:00:06.03 bitrate= 967.4kbits/frame=  245 fps= 28 q=15.0 size=     730kB time=00:00:06.53 bitrate= 915.4kbits/frame=  262 fps= 28 q=15.0 size=     742kB time=00:00:07.10 bitrate= 856.5kbits/frame=  277 fps= 28 q=13.0 size=     763kB time=00:00:07.60 bitrate= 822.6kbits/frame=  288 fps= 27 q=13.0 size=     872kB time=00:00:07.96 bitrate= 896.9kbits/frame=  299 fps= 27 q=13.0 size=    1112kB time=00:00:08.33 bitrate=1093.6kbits/frame=  317 fps= 27 q=15.0 size=    1128kB time=00:00:08.93 bitrate=1034.4kbits/frame=  335 fps= 28 q=15.0 size=    1140kB time=00:00:09.53 bitrate= 979.6kbits/frame=  348 fps= 27 q=12.0 size=    1261kB time=00:00:09.96 bitrate=1036.7kbits/frame=  364 fps= 27 q=13.0 size=    1299kB time=00:00:10.50 bitrate=1013.1kbits/frame=  375 fps= 27 q=13.0 size=    1306kB time=00:00:10.86 bitrate= 984.9kbits/frame=  393 fps= 27 q=13.0 size=    1319kB time=00:00:11.46 bitrate= 942.3kbits/frame=  406 fps= 27 q=13.0 size=    1455kB time=00:00:11.90 bitrate=1001.3kbits/frame=  422 fps= 27 q=12.0 size=    1483kB time=00:00:12.43 bitrate= 977.0kbits/frame=  436 fps= 27 q=11.0 size=    1497kB time=00:00:12.90 bitrate= 950.9kbits/frame=  447 fps= 27 q=11.0 size=    1505kB time=00:00:13.26 bitrate= 929.6kbits/frame=  463 fps= 27 q=11.0 size=    1517kB time=00:00:13.80 bitrate= 900.3kbits/frame=  472 fps= 27 q=11.0 size=    1671kB time=00:00:14.10 bitrate= 971.1kbits/frame=  487 fps= 27 q=11.0 size=    1692kB time=00:00:14.60 bitrate= 949.2kbits/frame=  499 fps= 27 q=11.0 size=    1826kB time=00:00:15.00 bitrate= 997.4kbits/frame=  514 fps= 27 q=10.0 size=    1940kB time=00:00:15.50 bitrate=1025.3kbits/frame=  527 fps= 27 q=10.0 size=    1969kB time=00:00:15.93 bitrate=1012.5kbits/frame=  541 fps= 27 q=10.0 size=    2016kB time=00:00:16.40 bitrate=1006.8kbits/frame=  553 fps= 26 q=10.0 size=    2245kB time=00:00:16.80 bitrate=1094.8kbits/frame=  561 fps= 26 q=12.0 size=    2395kB time=00:00:17.06 bitrate=1149.4kbits/frame=  574 fps= 26 q=12.0 size=    2454kB time=00:00:17.50 bitrate=1148.7kbits/frame=  590 fps= 26 q=12.0 size=    2487kB time=00:00:18.03 bitrate=1129.8kbits/frame=  601 fps= 26 q=11.0 size=    2498kB time=00:00:18.40 bitrate=1112.2kbits/frame=  617 fps= 26 q=10.0 size=    2513kB time=00:00:18.93 bitrate=1087.2kbits/frame=  625 fps= 26 q=10.0 size=    2689kB time=00:00:19.20 bitrate=1147.2kbits/frame=  642 fps= 26 q=11.0 size=    2720kB time=00:00:19.76 bitrate=1127.2kbits/frame=  660 fps= 26 q=11.0 size=    2732kB time=00:00:20.36 bitrate=1099.0kbits/frame=  676 fps= 26 q=11.0 size=    2743kB time=00:00:20.90 bitrate=1075.3kbits/frame=  683 fps= 26 q=10.0 size=    2904kB time=00:00:21.13 bitrate=1125.6kbits/frame=  697 fps= 26 q=10.0 size=    2939kB time=00:00:21.60 bitrate=1114.7kbits/frame=  713 fps= 26 q=9.0 size=    2957kB time=00:00:22.13 bitrate=1094.4kbits/sframe=  727 fps= 26 q=9.0 size=    2970kB time=00:00:22.60 bitrate=1076.4kbits/sframe=  737 fps= 26 q=9.0 size=    3104kB time=00:00:22.93 bitrate=1108.8kbits/sframe=  751 fps= 26 q=9.0 size=    3127kB time=00:00:23.40 bitrate=1094.8kbits/sframe=  762 fps= 26 q=9.0 size=    3197kB time=00:00:23.76 bitrate=1102.0kbits/sframe=  779 fps= 26 q=9.0 size=    3216kB time=00:00:24.33 bitrate=1082.6kbits/sframe=  795 fps= 26 q=9.0 size=    3228kB time=00:00:24.86 bitrate=1063.4kbits/sframe=  803 fps= 26 q=8.0 size=    3571kB time=00:00:25.13 bitrate=1163.8kbits/sframe=  820 fps= 26 q=10.0 size=    3592kB time=00:00:25.70 bitrate=1145.1kbits/frame=  834 fps= 26 q=10.0 size=    3602kB time=00:00:26.16 bitrate=1127.8kbits/frame=  854 fps= 26 q=8.0 size=    3618kB time=00:00:26.83 bitrate=1104.6kbits/sframe=  866 fps= 26 q=8.0 size=    3727kB time=00:00:27.23 bitrate=1121.1kbits/sframe=  882 fps= 26 q=8.0 size=    3755kB time=00:00:27.76 bitrate=1107.7kbits/sframe=  895 fps= 26 q=8.0 size=    3764kB time=00:00:28.20 bitrate=1093.4kbits/sframe=  910 fps= 26 q=8.0 size=    3774kB time=00:00:28.70 bitrate=1077.3kbits/sframe=  922 fps= 26 q=8.0 size=    3887kB time=00:00:29.10 bitrate=1094.2kbits/sframe=  938 fps= 26 q=8.0 size=    3905kB time=00:00:29.63 bitrate=1079.5kbits/sframe=  950 fps= 26 q=8.0 size=    4013kB time=00:00:30.03 bitrate=1094.6kbits/sframe=  966 fps= 26 q=8.0 size=    4032kB time=00:00:30.56 bitrate=1080.5kbits/sframe=  980 fps= 26 q=7.0 size=    4164kB time=00:00:31.03 bitrate=1099.2kbits/sframe=  990 fps= 26 q=7.0 size=    4180kB time=00:00:31.36 bitrate=1091.6kbits/sframe= 1006 fps= 26 q=7.0 size=    4198kB time=00:00:31.90 bitrate=1078.1kbits/sframe= 1016 fps= 26 q=7.0 size=    4383kB time=00:00:32.23 bitrate=1113.9kbits/sframe= 1033 fps= 26 q=7.0 size=    4398kB time=00:00:32.80 bitrate=1098.4kbits/sframe= 1044 fps= 26 q=7.0 size=    4491kB time=00:00:33.16 bitrate=1109.2kbits/sframe= 1055 fps= 26 q=8.0 size=    4730kB time=00:00:33.53 bitrate=1155.6kbits/sframe= 1068 fps= 26 q=7.0 size=    4741kB time=00:00:33.96 bitrate=1143.4kbits/sframe= 1076 fps= 26 q=7.0 size=    4927kB time=00:00:34.23 bitrate=1179.0kbits/sframe= 1092 fps= 26 q=8.0 size=    4939kB time=00:00:34.76 bitrate=1163.7kbits/sframe= 1107 fps= 26 q=8.0 size=    4973kB time=00:00:35.26 bitrate=1155.2kbits/sframe= 1123 fps= 26 q=7.0 size=    4986kB time=00:00:35.80 bitrate=1141.0kbits/sframe= 1133 fps= 26 q=8.0 size=    5138kB time=00:00:36.13 bitrate=1164.8kbits/sframe= 1145 fps= 26 q=8.0 size=    5146kB time=00:00:36.53 bitrate=1154.0kbits/sframe= 1161 fps= 26 q=7.0 size=    5182kB time=00:00:37.06 bitrate=1145.3kbits/sframe= 1179 fps= 26 q=7.0 size=    5199kB time=00:00:37.66 bitrate=1130.7kbits/sframe= 1190 fps= 26 q=7.0 size=    5334kB time=00:00:38.03 bitrate=1148.9kbits/sframe= 1207 fps= 26 q=7.0 size=    5354kB time=00:00:38.60 bitrate=1136.3kbits/sframe= 1217 fps= 26 q=7.0 size=    5406kB time=00:00:38.93 bitrate=1137.6kbits/sframe= 1233 fps= 26 q=7.0 size=    5442kB time=00:00:39.46 bitrate=1129.7kbits/sframe= 1247 fps= 26 q=7.0 size=    5614kB time=00:00:39.93 bitrate=1151.7kbits/sframe= 1263 fps= 26 q=7.0 size=    5642kB time=00:00:40.46 bitrate=1142.2kbits/sframe= 1278 fps= 26 q=7.0 size=    5658kB time=00:00:40.96 bitrate=1131.4kbits/sframe= 1294 fps= 26 q=6.0 size=    5678kB time=00:00:41.50 bitrate=1120.9kbits/sframe= 1301 fps= 26 q=6.0 size=    5911kB time=00:00:41.73 bitrate=1160.2kbits/sframe= 1313 fps= 26 q=7.0 size=    6016kB time=00:00:42.13 bitrate=1169.7kbits/sframe= 1329 fps= 26 q=7.0 size=    6029kB time=00:00:42.66 bitrate=1157.5kbits/sframe= 1345 fps= 26 q=6.0 size=    6056kB time=00:00:43.20 bitrate=1148.5kbits/sframe= 1359 fps= 26 q=6.0 size=    6067kB time=00:00:43.66 bitrate=1138.1kbits/sframe= 1368 fps= 26 q=6.0 size=    6180kB time=00:00:43.96 bitrate=1151.5kbits/sframe= 1385 fps= 26 q=6.0 size=    6199kB time=00:00:44.53 bitrate=1140.3kbits/sframe= 1401 fps= 26 q=6.0 size=    6306kB time=00:00:45.06 bitrate=1146.3kbits/sframe= 1417 fps= 26 q=6.0 size=    6323kB time=00:00:45.60 bitrate=1135.9kbits/sframe= 1433 fps= 26 q=6.0 size=    6335kB time=00:00:46.13 bitrate=1124.9kbits/sframe= 1445 fps= 26 q=6.0 size=    6446kB time=00:00:46.53 bitrate=1134.8kbits/sframe= 1455 fps= 26 q=6.0 size=    6467kB time=00:00:46.86 bitrate=1130.4kbits/sframe= 1464 fps= 26 q=6.0 size=    6653kB time=00:00:47.16 bitrate=1155.6kbits/sframe= 1480 fps= 26 q=6.0 size=    6670kB time=00:00:47.70 bitrate=1145.5kbits/sframe= 1496 fps= 26 q=6.0 size=    6683kB time=00:00:48.23 bitrate=1135.0kbits/sframe= 1509 fps= 26 q=6.0 size=    6778kB time=00:00:48.66 bitrate=1141.0kbits/sframe= 1521 fps= 26 q=7.0 size=    6958kB time=00:00:49.06 bitrate=1161.6kbits/sframe= 1537 fps= 26 q=6.0 size=    6982kB time=00:00:49.60 bitrate=1153.2kbits/sframe= 1548 fps= 26 q=6.0 size=    7194kB time=00:00:49.96 bitrate=1179.5kbits/sframe= 1566 fps= 26 q=6.0 size=    7253kB time=00:00:50.56 bitrate=1175.0kbits/sframe= 1579 fps= 26 q=6.0 size=    7399kB time=00:00:51.00 bitrate=1188.4kbits/sframe= 1594 fps= 26 q=6.0 size=    7420kB time=00:00:51.50 bitrate=1180.3kbits/sframe= 1606 fps= 26 q=6.0 size=    7429kB time=00:00:51.90 bitrate=1172.6kbits/sframe= 1621 fps= 26 q=6.0 size=    7444kB time=00:00:52.40 bitrate=1163.8kbits/sframe= 1638 fps= 26 q=6.0 size=    7479kB time=00:00:52.96 bitrate=1156.7kbits/sframe= 1650 fps= 26 q=6.0 size=    7609kB time=00:00:53.36 bitrate=1168.1kbits/sframe= 1665 fps= 26 q=6.0 size=    7620kB time=00:00:53.86 bitrate=1158.8kbits/sframe= 1677 fps= 26 q=5.0 size=    7628kB time=00:00:54.26 bitrate=1151.6kbits/sframe= 1690 fps= 26 q=5.0 size=    7717kB time=00:00:54.70 bitrate=1155.7kbits/sframe= 1701 fps= 26 q=5.0 size=    7894kB time=00:00:55.06 bitrate=1174.3kbits/sframe= 1717 fps= 26 q=5.0 size=    7915kB time=00:00:55.60 bitrate=1166.2kbits/sframe= 1733 fps= 26 q=5.0 size=    7926kB time=00:00:56.13 bitrate=1156.7kbits/sframe= 1745 fps= 26 q=5.0 size=    7954kB time=00:00:56.53 bitrate=1152.6kbits/sframe= 1759 fps= 26 q=5.0 size=    7968kB time=00:00:57.00 bitrate=1145.1kbits/sframe= 1770 fps= 26 q=5.0 size=    8096kB time=00:00:57.36 bitrate=1156.1kbits/sframe= 1786 fps= 26 q=5.0 size=    8107kB time=00:00:57.90 bitrate=1147.1kbits/sframe= 1798 fps= 26 q=5.0 size=    8324kB time=00:00:58.30 bitrate=1169.7kbits/sframe= 1813 fps= 26 q=5.0 size=    8376kB time=00:00:58.80 bitrate=1167.0kbits/sframe= 1821 fps= 26 q=5.0 size=    8532kB time=00:00:59.06 bitrate=1183.3kbits/sframe= 1836 fps= 26 q=5.0 size=    8549kB time=00:00:59.56 bitrate=1175.7kbits/sframe= 1850 fps= 26 q=5.0 size=    8672kB time=00:01:00.03 bitrate=1183.4kbits/sframe= 1865 fps= 26 q=5.0 size=    8696kB time=00:01:00.53 bitrate=1176.9kbits/sframe= 1879 fps= 26 q=5.0 size=    8718kB time=00:01:01.00 bitrate=1170.7kbits/sframe= 1894 fps= 26 q=5.0 size=    8745kB time=00:01:01.50 bitrate=1164.9kbits/sframe= 1905 fps= 26 q=5.0 size=    8769kB time=00:01:01.86 bitrate=1161.1kbits/sframe= 1912 fps= 26 q=5.0 size=    8957kB time=00:01:02.10 bitrate=1181.6kbits/sframe= 1928 fps= 26 q=5.0 size=    8981kB time=00:01:02.63 bitrate=1174.7kbits/sframe= 1944 fps= 26 q=5.0 size=    8994kB time=00:01:03.16 bitrate=1166.4kbits/sframe= 1960 fps= 26 q=5.0 size=    9006kB time=00:01:03.70 bitrate=1158.2kbits/sframe= 1972 fps= 26 q=5.0 size=    9203kB time=00:01:04.10 bitrate=1176.1kbits/sframe= 1984 fps= 26 q=5.0 size=    9224kB time=00:01:04.50 bitrate=1171.6kbits/sframe= 2000 fps= 26 q=5.0 size=    9236kB time=00:01:05.03 bitrate=1163.4kbits/sframe= 2016 fps= 26 q=5.0 size=    9247kB time=00:01:05.56 bitrate=1155.3kbits/sframe= 2032 fps= 26 q=7.0 size=    9437kB time=00:01:06.10 bitrate=1169.5kbits/sframe= 2043 fps= 26 q=5.0 size=    9469kB time=00:01:06.46 bitrate=1167.0kbits/sframe= 2054 fps= 26 q=5.0 size=    9704kB time=00:01:06.83 bitrate=1189.5kbits/sframe= 2070 fps= 26 q=5.0 size=    9715kB time=00:01:07.36 bitrate=1181.4kbits/sframe= 2086 fps= 26 q=5.0 size=    9733kB time=00:01:07.90 bitrate=1174.3kbits/sframe= 2096 fps= 26 q=5.0 size=    9874kB time=00:01:08.23 bitrate=1185.4kbits/sframe= 2099 fps= 25 q=-1.0 Lsize=    9966kB time=00:01:09.90 bitrate=1167.9kbits/s    
video:8587kB audio:1322kB global headers:0kB muxing overhead 0.575495%
frame I:9     Avg QP: 5.80  size:165030
[libx264 @ 0x8f1f320] frame P:619   Avg QP: 3.53  size: 11309
[libx264 @ 0x8f1f320] frame B:1471  Avg QP: 7.99  size:   208
[libx264 @ 0x8f1f320] consecutive B-frames:  6.5%  0.2%  0.1% 93.2%
[libx264 @ 0x8f1f320] mb I  I16..4: 44.1% 20.8% 35.0%
[libx264 @ 0x8f1f320] mb P  I16..4:  1.0%  0.3%  0.4%  P16..4:  8.9%  0.5%  0.8%  0.0%  0.0%    skip:88.1%
[libx264 @ 0x8f1f320] mb B  I16..4:  0.0%  0.0%  0.0%  B16..8:  2.0%  0.0%  0.0%  direct: 0.5%  skip:97.5%  L0:28.2% L1:71.6% BI: 0.2%
[libx264 @ 0x8f1f320] final ratefactor: 4.43
[libx264 @ 0x8f1f320] 8x8 transform intra:19.1% inter:42.5%
[libx264 @ 0x8f1f320] coded y,uvDC,uvAC intra: 56.5% 74.9% 73.5% inter: 1.5% 2.7% 2.2%
[libx264 @ 0x8f1f320] i16 v,h,dc,p: 90%  7%  2%  1%
[libx264 @ 0x8f1f320] i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 52% 13% 14%  3%  3%  3%  3%  3%  5%
[libx264 @ 0x8f1f320] i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 50% 13% 13%  3%  5%  4%  4%  4%  4%
[libx264 @ 0x8f1f320] i8c dc,h,v,p: 14% 14% 66%  6%
[libx264 @ 0x8f1f320] ref P L0: 94.7%  4.1%  1.1%
[libx264 @ 0x8f1f320] ref B L0: 77.3% 21.8%  0.8%
[libx264 @ 0x8f1f320] ref B L1: 97.8%  2.2%
[libx264 @ 0x8f1f320] kb/s:1005.27


```

and since this is different, I shall attempt to transfer this to the iPad too via iTunes on a Windows 7 VirtualBox
And after i tried to move that over, It comes up saying that:
"OUTPUT.mp4" was not copied to the iPad because it cannot be played on this iPad.

---

### Post by ron999 on 2012-06-16
Hi
The video "**INPUT.flv**" already uses **h264** and **aac**.

> Stream #0.0: Video: h264 (Main), yuv420p, 480x360 
Stream #0.1: Audio: aac, 44100 Hz, stereo, s16, 99 kb/s

Will it play on iPad when you use this command:-

```
ffmpeg -i INPUT.flv -vcodec copy -acodec copy OUTPUT2.mp4
```

---

### Post by RichardC400 on 2012-06-16
That Code, didn't work.

```
:~$ ffmpeg -i INPUT.flv -vcodec copy -acodec copy OUTPUT2.mp4ffmpeg version N-31140-g3074f03, Copyright (c) 2000-2011 the FFmpeg developers
  built on Jul  2 2011 07:31:42 with gcc 4.5.2
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil    51. 11. 0 / 51. 11. 0
  libavcodec   53.  7. 0 / 53.  7. 0
  libavformat  53.  5. 0 / 53.  5. 0
  libavdevice  53.  2. 0 / 53.  2. 0
  libavfilter   2. 24. 1 /  2. 24. 1
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  51.  2. 0 / 51.  2. 0
[flv @ 0xab52340] Estimating duration from bitrate, this may be inaccurate
Input #0, flv, from 'INPUT.flv':
  Metadata:
    duration        : 70
    starttime       : 0
    totalduration   : 70
    width           : 480
    height          : 360
    videodatarate   : 135
    audiodatarate   : 97
    totaldatarate   : 241
    framerate       : 30
    bytelength      : 2104748
    canseekontime   : true
    sourcedata      : B4A7D6104HH1326599994454481
    purl            : 
    pmsg            : 
  Duration: 00:01:09.96, start: 0.000000, bitrate: 237 kb/s
    Stream #0.0: Video: h264 (Main), yuv420p, 480x360 [PAR 1:1 DAR 4:3], 138 kb/s, 30 tbr, 1k tbn, 60 tbc
    Stream #0.1: Audio: aac, 44100 Hz, stereo, s16, 99 kb/s
Output #0, mp4, to 'OUTPUT2.mp4':
  Metadata:
    duration        : 70
    starttime       : 0
    totalduration   : 70
    width           : 480
    height          : 360
    videodatarate   : 135
    audiodatarate   : 97
    totaldatarate   : 241
    framerate       : 30
    bytelength      : 2104748
    canseekontime   : true
    sourcedata      : B4A7D6104HH1326599994454481
    purl            : 
    pmsg            : 
    encoder         : Lavf53.5.0
    Stream #0.0: Video: libx264, yuv420p, 480x360 [PAR 1:1 DAR 4:3], q=2-31, 138 kb/s, 30 tbn, 30 tbc
    Stream #0.1: Audio: libfaac, 44100 Hz, stereo, 99 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop, [?] for help
[mp4 @ 0xab52a60] Application provided invalid, non monotonically increasing dts to muxer in stream 0: 905 >= 905
av_interleaved_write_frame(): Invalid argument

```

---

### Post by ron999 on 2012-06-16
Yes
FFmpeg does sometimes have "non-monotonical" problems with flv files.
Maybe **VLC** can handle it.
Like this:-
```
cvlc INPUT.flv --sout="#std{access=file,mux=mp4,dst='OUTPUT2.mp4'}" vlc://quit
```

---

### Post by RichardC400 on 2012-06-16
Not tried it, I finally got it to work.
What finally got it to work was something which I am kicking myself for.
On my Windows 7 VB I had iTunes, but I did not have Quicktime.
Once Quicktime was installed I had no problems whatsoever.

---

### Post by FakeOutdoorsman on 2012-06-16
Current syntax using your version of FFmpeg:

```
ffmpeg -i input -c:v libx264 -preset medium -vpre libx264-ipod640 -crf 24 -c:a libfaac -q:a 100 output.mp4
```

Adjust the crf value to control output quality. A sane range is 18-30ish and a lower value is a higher quality and therefore larger file size. Typical usage is to choose the highest value that still gives you an acceptable quality.

The iPad 2 may not even need *-vpre libx264-ipod640*, so try without it first. Add *-t 60* to encode just a minute long video just to test.

---

