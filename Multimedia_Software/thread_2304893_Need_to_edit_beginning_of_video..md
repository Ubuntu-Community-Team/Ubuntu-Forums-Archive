---
title: "Need to edit beginning of video."
date: 2015-11-30
forum: Multimedia Software
---

### Post by oygle on 2015-11-30
I have a video that is 5:47 long and the first 11 seconds need to be cut out. Is it simply a matter of installing ffmpeg and running a command ?

---

### Post by oygle on 2015-12-01
Installed ffmpeg and chacked on some samples here and there ..

```
$ ffmpeg -ss 00:00:11 -i VideoClip1.mp4 -t 00:05:36 -c copy VideoClip2.mp4
```

> ffmpeg version N-76944-g15206ff Copyright (c) 2000-2015 the FFmpeg developers
  built with gcc 4.8 (Ubuntu 4.8.4-2ubuntu1~14.04)
  configuration: --extra-libs=-ldl --prefix=/opt/ffmpeg --enable-avresample --disable-debug --enable-nonfree --enable-gpl --enable-version3 --enable-libopencore-amrnb --enable-libopencore-amrwb --disable-decoder=amrnb --disable-decoder=amrwb --enable-libpulse --enable-libdcadec --enable-libfreetype --enable-libx264 --enable-libx265 --enable-libfdk-aac --enable-libvorbis --enable-libmp3lame --enable-libopus --enable-libvpx --enable-libspeex --enable-libass --enable-avisynth --enable-libsoxr --enable-libxvid --enable-libvo-aacenc --enable-libvidstab
  libavutil      55.  9.100 / 55.  9.100
  libavcodec     57. 16.101 / 57. 16.101
  libavformat    57. 19.100 / 57. 19.100
  libavdevice    57.  0.100 / 57.  0.100
  libavfilter     6. 17.100 /  6. 17.100
  libavresample   3.  0.  0 /  3.  0.  0
  libswscale      4.  0.100 /  4.  0.100
  libswresample   2.  0.101 /  2.  0.101
  libpostproc    54.  0.100 / 54.  0.100
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=614700, dts=618390, size=3322
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=644670, dts=648360, size=3415                                                                      
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=652140, dts=655830, size=2845                                                                      
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=659700, dts=663390, size=2740                                                                      
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=712170, dts=715860, size=1532                                                                      
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=719640, dts=723330, size=860                                                                       
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=727110, dts=730800, size=802                                                                       
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=734670, dts=738360, size=2019                                                                      
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=749610, dts=753300, size=1215                                                                      
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=757170, dts=760860, size=1023                                                                      
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=764640, dts=768330, size=1244                                                                      
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=772110, dts=775800, size=764                                                                       
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=779580, dts=783270, size=1109                                                                      
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=787140, dts=790830, size=953                                                                       
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=794610, dts=798300, size=811                                                                       
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=802080, dts=805770, size=604                                                                       
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=809640, dts=813330, size=682                                                                       
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=817110, dts=820800, size=673                                                                       
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=824580, dts=828270, size=750                                                                       
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=832050, dts=835740, size=709                                                                       
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=839610, dts=843300, size=836                                                                       
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=847080, dts=850770, size=740                                                                       
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=854550, dts=858240, size=810                                                                       
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=862110, dts=865800, size=753                                                                       
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=869580, dts=873270, size=1309                                                                      
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=884520, dts=888210, size=537                                                                       
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=892080, dts=895770, size=617                                                                       
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=899550, dts=903240, size=604                                                                       
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=907020, dts=910710, size=636                                                                       
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=914580, dts=918270, size=539                                                                       
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=922050, dts=925740, size=543                                                                       
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=929520, dts=933210, size=803                                                                       
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=937080, dts=940770, size=769                                                                       
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=944550, dts=948240, size=944                                                                       
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=952020, dts=955710, size=878                                                                       
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=959490, dts=963180, size=711                                                                       
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=967050, dts=970740, size=747                                                                       
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=974520, dts=978210, size=667                                                                       
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=981990, dts=985680, size=536                                                                       
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=989550, dts=993240, size=593
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=997020, dts=1000710, size=543
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=1004490, dts=1008180, size=590
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=1019520, dts=1023210, size=528
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=1026990, dts=1030680, size=610
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=1034460, dts=1038150, size=722
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=1042020, dts=1045710, size=635
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=1049490, dts=1053180, size=900
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=1056960, dts=1060650, size=713
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=614700, dts=618390, size=3322
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=31913460, dts=31916970, size=751
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=1487340, dts=1490850, size=1537
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=1570140, dts=1573650, size=911
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=1591740, dts=1595250, size=667
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=1584540, dts=1588050, size=749
    Last message repeated 1 times
Input #0, mpegts, from 'VideoClip1.mp4':
  Duration: 00:05:47.95, start: 6.766167, bitrate: 579 kb/s
  Program 1 
    Stream #0:0[0x102]: Data: timed_id3 (ID3  / 0x20334449)
    Stream #0:1[0x100]: Video: h264 (Main) ([27][0][0][0] / 0x001B), yuv420p, 320x568, 24 tbr, 90k tbn, 180k tbc
    Stream #0:2[0x101]: Audio: aac (LC) ([15][0][0][0] / 0x000F), 44100 Hz, mono, fltp, 98 kb/s
[mp4 @ 0x3360080] Codec for stream 0 does not use global headers but container format requires global headers
[mp4 @ 0x3360080] Codec for stream 1 does not use global headers but container format requires global headers
Output #0, mp4, to 'VideoClip2.mp4':
  Metadata:
    encoder         : Lavf57.19.100
    Stream #0:0: Video: h264 ([33][0][0][0] / 0x0021), yuv420p, 320x568, q=2-31, 24 tbr, 90k tbn, 90k tbc
    Stream #0:1: Audio: aac (LC) ([64][0][0][0] / 0x0040), 44100 Hz, mono, 98 kb/s
Stream mapping:
  Stream #0:1 -> #0:0 (copy)
  Stream #0:2 -> #0:1 (copy)
Press [q] to stop, [?] for help
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=1584540, dts=1588050, size=749
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=1591740, dts=1595250, size=667
[mpegts @ 0x33583e0] Invalid timestamps stream=1, pts=1598940, dts=1602450, size=615
[mp4 @ 0x3360080] Malformed AAC bitstream detected: use the audio bitstream filter 'aac_adtstoasc' to fix it ('-bsf:a aac_adtstoasc' option with ffmpeg)
av_interleaved_write_frame(): Operation not permitted
[mp4 @ 0x3360080] Malformed AAC bitstream detected: use the audio bitstream filter 'aac_adtstoasc' to fix it ('-bsf:a aac_adtstoasc' option with ffmpeg)
Error writing trailer of VideoClip2.mp4: Operation not permittedframe=    1 fps=0.0 q=-1.0 Lsize=       0kB time=00:00:00.16 bitrate=  12.7kbits/s    
video:15kB audio:3kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: unknown
Conversion failed!

---

### Post by Bucky Ball on 2015-12-01
Kino will probably do that in a jiff. It's in the repos. Should drag in whatever you need.

---

### Post by oygle on 2015-12-01
Thanks, tried that. It gave me a 1.2 Gb file with a .DV extension - sourced from a 24 Mb MP4 file as input. Thought I was driving it properly, but nope.  lol

---

### Post by Bucky Ball on 2015-12-01
*Post(s) moved to own thread. *

---

### Post by oygle on 2015-12-01
[shantiq]("http://ubuntuforums.org/member.php?u=870500") - I used your example below ..

> **shantiq said:**
> 

OR MORE ACCURATE BUT SLOWER -ss AS OUTPUT OPTION 
```
ffmpeg -i video.mp4 -c:a -c:v copy 5minutevideo.mp4 -ss 00:00:00 -t 00:05:00

```

to construct this ..

```
ffmpeg -i VideoClip1.mp4 -c:a -c:v copy VideoClip2.mp4 -ss 00:00:11 -t 00:05:36
```

> ffmpeg version 2.5.8-0ubuntu0.15.04.1 Copyright (c) 2000-2015 the FFmpeg developers
  built with gcc 4.9.2 (Ubuntu 4.9.2-10ubuntu13)
  configuration: --prefix=/usr --extra-version=0ubuntu0.15.04.1 --build-suffix=-ffmpeg --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --shlibdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --enable-shared --disable-stripping --enable-avresample --enable-avisynth --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmodplug --enable-libmp3lame --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-libschroedinger --enable-libshine --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libwavpack --enable-libwebp --enable-libxvid --enable-opengl --enable-x11grab --enable-libdc1394 --enable-libiec61883 --enable-libzvbi --enable-libzmq --enable-frei0r --enable-libvpx --enable-libx264 --enable-libsoxr --enable-gnutls --enable-openal --enable-libopencv --enable-librtmp --enable-libx265
  libavutil      54. 15.100 / 54. 15.100
  libavcodec     56. 13.100 / 56. 13.100
  libavformat    56. 15.102 / 56. 15.102
  libavdevice    56.  3.100 / 56.  3.100
  libavfilter     5.  2.103 /  5.  2.103
  libavresample   2.  1.  0 /  2.  1.  0
  libswscale      3.  1.101 /  3.  1.101
  libswresample   1.  1.100 /  1.  1.100
  libpostproc    53.  3.100 / 53.  3.100
Trailing options were found on the commandline.                                                                                                                                                 
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=614700, dts=618390, size=3322                                                                                                              
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=644670, dts=648360, size=3415                                                                                                              
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=652140, dts=655830, size=2845                                                                                                              
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=659700, dts=663390, size=2740                                                                                                              
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=712170, dts=715860, size=1532                                                                                                              
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=719640, dts=723330, size=860                                                                                                               
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=727110, dts=730800, size=802                                                                                                               
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=734670, dts=738360, size=2019                                                                                                              
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=749610, dts=753300, size=1215                                                                                                              
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=757170, dts=760860, size=1023                                                                                                              
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=764640, dts=768330, size=1244                                                                                                              
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=772110, dts=775800, size=764                                                                                                               
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=779580, dts=783270, size=1109                                                                                                              
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=787140, dts=790830, size=953                                                                                                               
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=794610, dts=798300, size=811                                                                                                               
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=802080, dts=805770, size=604                                                                                                               
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=809640, dts=813330, size=682
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=817110, dts=820800, size=673
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=824580, dts=828270, size=750
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=832050, dts=835740, size=709
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=839610, dts=843300, size=836
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=847080, dts=850770, size=740
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=854550, dts=858240, size=810
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=862110, dts=865800, size=753
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=869580, dts=873270, size=1309
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=884520, dts=888210, size=537
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=892080, dts=895770, size=617
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=899550, dts=903240, size=604
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=907020, dts=910710, size=636
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=914580, dts=918270, size=539
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=922050, dts=925740, size=543
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=929520, dts=933210, size=803
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=937080, dts=940770, size=769
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=944550, dts=948240, size=944
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=952020, dts=955710, size=878
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=959490, dts=963180, size=711
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=967050, dts=970740, size=747
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=974520, dts=978210, size=667
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=981990, dts=985680, size=536
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=989550, dts=993240, size=593
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=997020, dts=1000710, size=543
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=1004490, dts=1008180, size=590
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=1019520, dts=1023210, size=528
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=1026990, dts=1030680, size=610
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=1034460, dts=1038150, size=722
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=1042020, dts=1045710, size=635
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=1049490, dts=1053180, size=900
[mpegts @ 0x7a0220] Invalid timestamps stream=1, pts=1056960, dts=1060650, size=713
Input #0, mpegts, from 'VideoClip1.mp4':
  Duration: 00:05:47.95, start: 6.766167, bitrate: 579 kb/s
  Program 1 
    Stream #0:0[0x102]: Data: timed_id3 (ID3  / 0x20334449)
    Stream #0:1[0x100]: Video: h264 (Main) ([27][0][0][0] / 0x001B), yuv420p, 320x568, 24 tbr, 90k tbn, 180k tbc
    Stream #0:2[0x101]: Audio: aac (LC) ([15][0][0][0] / 0x000F), 44100 Hz, mono, fltp, 91 kb/s
[NULL @ 0x7a74a0] Unable to find a suitable output format for 'copy'
copy: Invalid argument

Can you assist please ?

---

### Post by shantiq on 2015-12-01
ok oygle i had made a mistake in syntax as it has changed in recent times   so here:


```
[COLOR=#000000]ffmpeg -i VideoClip1.mp4 [/COLOR][COLOR=#800000]c copy[/COLOR][COLOR=#000000] -ss 00:00:11 [/COLOR][COLOR=#800000]-to[/COLOR][COLOR=#000000] 00:05:36  VideoClip2.mp4 

[/COLOR]
```

---

### Post by FakeOutdoorsman on 2015-12-01
> **oygle said:**
> ```
$ ffmpeg -ss 00:00:11 -i VideoClip1.mp4 -t 00:05:36 -c copy VideoClip2.mp4
...
[mp4 @ 0x3360080] Malformed AAC bitstream detected: use the audio bitstream filter 'aac_adtstoasc' to fix it ('-bsf:a aac_adtstoasc' option with ffmpeg)
```

The console output is indicating that an additional option is needed:

```
ffmpeg -ss 00:00:11 -i VideoClip1.mp4 -t 00:05:36 -c copy -bsf:a aac_adtstoasc VideoClip2.mp4
```

[Bitstream filters](http://ffmpeg.org/ffmpeg-bitstream-filters.html#aac_005fadtstoasc) are usually not needed for most uses, but this is one case. Has the file name extension of the input been arbitrarily renamed? ffmpeg is using the mpegts demuxer although the input file extension is .mp4.

---

### Post by oygle on 2015-12-01
> **shantiq said:**
> ok oygle i had made a mistake in syntax as it has changed in recent times   so here:

```
[COLOR=#000000]ffmpeg -i VideoClip1.mp4 [/COLOR][COLOR=#800000]c copy[/COLOR][COLOR=#000000] -ss 00:00:11 [/COLOR][COLOR=#800000]-to[/COLOR][COLOR=#000000] 00:05:36  VideoClip2.mp4 

[/COLOR]
```

Thanks - I tried that, got a syntax error. Did try to fix it, but was unable to work out what it needed.

> **FakeOutdoorsman said:**
> The console output is indicating that an additional option is needed:

```
ffmpeg -ss 00:00:11 -i VideoClip1.mp4 -t 00:05:36 -c copy -bsf:a aac_adtstoasc VideoClip2.mp4
```

[Bitstream filters](http://ffmpeg.org/ffmpeg-bitstream-filters.html#aac_005fadtstoasc) are usually not needed for most uses, but this is one case. Has the file name extension of the input been arbitrarily renamed? ffmpeg is using the mpegts demuxer although the input file extension is .mp4.

Wow, thanks, that worked, and the output MP4 is just how I need it. There were a lot of 'invalid timestamps stream" messages, but I guess that is more what may be missing from the input MP4. Here is the tail end of the output logs ..

> 
[mp4 @ 0x2872ee0] Invalid DTS: 30231705 PTS: 30228195 in output stream 0:0, replacing by guess
[mpegts @ 0x286b420] Invalid timestamps stream=1, pts=31834350, dts=31837860, size=650
[mp4 @ 0x2872ee0] Invalid DTS: 30238905 PTS: 30235395 in output stream 0:0, replacing by guess
[mpegts @ 0x286b420] Invalid timestamps stream=1, pts=31841550, dts=31845060, size=706
frame= 8401 fps=0.0 q=-1.0 Lsize=   21772kB time=00:05:36.01 bitrate= 530.8kbits/s    
video:18724kB audio:2716kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: 1.549065%

Am not concerned about those messages, as the MP4 created looks and sounds fine, and starts just after that 11 second marker.

You asked about the filename extension being renamed. No, it hasn't. The original file was recorded from a phone and up on periscope, and as we don't know how long Periscope keep the videos for, we needed to convert and 'cut' at the start. The person who did the periscope video will be very pleased, thanks.  :)

---

### Post by Bucky Ball on 2015-12-01
If you're happy that your initial issue is solved could you please mark the thread (first link in my signature). This won't close the thread but it will help others. Thanks. :)

---

### Post by oygle on 2015-12-01
?

---

### Post by vasa1 on 2015-12-02
> **oygle said:**
> ?
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

