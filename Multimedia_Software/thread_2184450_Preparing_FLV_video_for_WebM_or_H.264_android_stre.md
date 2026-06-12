---
title: "Preparing FLV video for WebM or H.264 android streaming (not live)"
date: 2013-10-29
forum: Multimedia Software
---

### Post by chaemil on 2013-10-29
Hi. I'm making server side conversion/archive application on Ubuntu server. I'm using FFMPEG to convert the flv input to webm/mp4 files for later streaming in my Android App. Problem is that on for example Nexus 4, 7, Asus Transformer Prime and so on the videos working. But on some devices like Galaxy S Duos GT-S7562 with ICS dont. 

This is the command for the conversion:

WebM:
```

avconv -i ./input.flv -y -c:v libvpx -b:v 350k -c:a libvorbis -b:a 96k -async 1 ./output.webm

```

MP4
```

avconv -i ./input.flv -y -c:v libx264 -b:v 400k -b:a 128k -async 1 -movflags faststart ./output.mp4

```

Anyone knows the solution?

---

### Post by FakeOutdoorsman on 2013-10-29
You're using avconv, not ffmpeg.

---

### Post by chaemil on 2013-10-29
Yes, what's the difference? The ffmpeg is deprecated command... And for i know it's the same packages as FFMPEG

---

### Post by FakeOutdoorsman on 2013-10-30
See:

[list]
[*][Who can tell me the difference and relation between ffmpeg, libav, and avconv?](http://stackoverflow.com/a/9477756/1109017)
[*][The FFmpeg/Libav situation](http://blog.pkh.me/p/13-the-ffmpeg-libav-situation.html)
[/list]

---

### Post by chaemil on 2013-10-30
Ok... Thanks... But how to solve this? Anyone?

---

### Post by FakeOutdoorsman on 2013-10-31
Please show the complete console output along with each of your commands. Do neither the webm or mp4 files work on the Galaxy S Duos GT-S7562?

---

### Post by chaemil on 2013-10-31
The avconv log is pretty long bcs it's almost 2 hours video. Neither of these two files working. Some shorter videos converted with these setting works. Shorter than 10 minutes i think. I've read about cutting the video to smaller pieces in one file will help it, but I dont know how to do that. So here's the log:


WEBM:
```

avconv version 0.8.6-4:0.8.6-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Apr  2 2013 17:00:59 with gcc 4.6.3
[flv @ 0x8ecf240] Estimating duration from bitrate, this may be inaccurate
Input #0, flv, from './db/2013-10-29-GHWIwt.flv':
  Metadata:
    audiochannels   : 1
    audiodevice     : Mic in at rear panel (Pink) (Re
    audioinputvolume: 82
    author          : Holy Ghost End Time MInistries Int.
    copyright       : Holy Ghost End Time MInistries Int.
    videokeyframe_frequency: 3
    description     : 
    lastkeyframetimestamp: 6114549
    keywords        : 
    creationdate    : Tue Oct 29 19:03:25 2013

    fmleversion     : 3.2.0.9932
    presetname      : Custom
    rating          : 
    title           : 
    videodevice     : 713x BDA Analog Capture
    lasttimestamp   : 6115574
  Duration: 01:41:55.57, start: 0.000000, bitrate: 868 kb/s
    Stream #0.0: Video: vp6f, yuv420p, 720x404, 737 kb/s, 1k tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 44100 Hz, mono, s16, 131 kb/s
[buffer @ 0x8ed32c0] w:720 h:404 pixfmt:yuv420p
[libvpx @ 0x8ed1e60] v1.0.0
Output #0, webm, to './db/2013-10-29-GHWIwt.webm':
  Metadata:
    audiochannels   : 1
    audiodevice     : Mic in at rear panel (Pink) (Re
    audioinputvolume: 82
    author          : Holy Ghost End Time MInistries Int.
    copyright       : Holy Ghost End Time MInistries Int.
    videokeyframe_frequency: 3
    description     : 
    lastkeyframetimestamp: 6114549
    keywords        : 
    creationdate    : Tue Oct 29 19:03:25 2013

    fmleversion     : 3.2.0.9932
    presetname      : Custom
    rating          : 
    title           : 
    videodevice     : 713x BDA Analog Capture
    lasttimestamp   : 6115574
    encoder         : Lavf53.21.1
    Stream #0.0: Video: libvpx, yuv420p, 720x404, q=-1--1, 300 kb/s, 1k tbn, 1k tbc
    Stream #0.1: Audio: libvorbis, 44100 Hz, mono, s16, 90 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (vp6f -> libvpx)
  Stream #0:1 -> #0:1 (mp3 -> libvorbis)
Press ctrl-c to stop encoding
frame=    8 fps=  0 q=0.0 size=       4kB time=0.38 bitrate=  86.7kbits/s dup=0 drop=1    
frame=   12 fps=  9 q=0.0 size=       4kB time=0.48 bitrate=  67.9kbits/s dup=0 drop=12    
frame=   18 fps=  8 q=0.0 size=       4kB time=0.71 bitrate=  45.7kbits/s dup=0 drop=12    
frame=   21 fps=  8 q=0.0 size=      36kB time=0.85 bitrate= 346.0kbits/s dup=0 drop=12    
frame=   25 fps=  7 q=0.0 size=      36kB time=0.99 bitrate= 297.4kbits/s dup=0 drop=12    

...



frame=152757 fps=  6 q=0.0 size=  284464kB time=6115.06 bitrate= 381.1kbits/s dup=0 drop=12    
frame=152768 fps=  6 q=0.0 Lsize=  284495kB time=6115.55 bitrate= 381.1kbits/s dup=0 drop=12    
video:224180kB audio:56965kB global headers:3kB muxing overhead 1.190008%

```


MP4
```


avconv version 0.8.6-4:0.8.6-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Apr  2 2013 17:00:59 with gcc 4.6.3
[flv @ 0x8ee7240] Estimating duration from bitrate, this may be inaccurate
Input #0, flv, from './db/2013-10-29-GHWIwt.flv':
  Metadata:
    audiochannels   : 1
    audiodevice     : Mic in at rear panel (Pink) (Re
    audioinputvolume: 82
    author          : Holy Ghost End Time MInistries Int.
    copyright       : Holy Ghost End Time MInistries Int.
    videokeyframe_frequency: 3
    description     : 
    lastkeyframetimestamp: 6114549
    keywords        : 
    creationdate    : Tue Oct 29 19:03:25 2013

    fmleversion     : 3.2.0.9932
    presetname      : Custom
    rating          : 
    title           : 
    videodevice     : 713x BDA Analog Capture
    lasttimestamp   : 6115574
  Duration: 01:41:55.57, start: 0.000000, bitrate: 868 kb/s
    Stream #0.0: Video: vp6f, yuv420p, 720x404, 737 kb/s, 1k tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 44100 Hz, mono, s16, 131 kb/s
[buffer @ 0x8eeaa60] w:720 h:404 pixfmt:yuv420p
[libx264 @ 0x8ee9e60] MB rate (1170000) > level limit (983040)
[libx264 @ 0x8ee9e60] using cpu capabilities: MMX2 SSE2 SSE3 Cache64
[libx264 @ 0x8ee9e60] profile Main, level 5.1
[libx264 @ 0x8ee9e60] 264 - core 120 r2151 a3f4407 - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - http://www.videolan.org/x264.html - options: cabac=1 ref=3 deblock=1:0:0 analyse=0x1:0x111 me=hex subme=7 psy=1 psy_rd=1.00:0.00 mixed_ref=0 me_range=16 chroma_me=1 trellis=1 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=3 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=0 b_adapt=1 b_bias=0 direct=1 weightb=0 open_gop=1 weightp=2 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=abr mbtree=1 bitrate=300 ratetol=1.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.25 aq=1:1.00
Output #0, mp4, to './db/2013-10-29-GHWIwt.mp4':
  Metadata:
    audiochannels   : 1
    audiodevice     : Mic in at rear panel (Pink) (Re
    audioinputvolume: 82
    author          : Holy Ghost End Time MInistries Int.
    copyright       : Holy Ghost End Time MInistries Int.
    videokeyframe_frequency: 3
    description     : 
    lastkeyframetimestamp: 6114549
    keywords        : 
    creationdate    : Tue Oct 29 19:03:25 2013

    fmleversion     : 3.2.0.9932
    presetname      : Custom
    rating          : 
    title           : 
    videodevice     : 713x BDA Analog Capture
    lasttimestamp   : 6115574
    encoder         : Lavf53.21.1
    Stream #0.0: Video: libx264, yuv420p, 720x404, q=-1--1, 300 kb/s, 1k tbn, 1k tbc
    Stream #0.1: Audio: libvo_aacenc, 44100 Hz, mono, s16, 128 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (vp6f -> libx264)
  Stream #0:1 -> #0:1 (mp3 -> libvo_aacenc)
Press ctrl-c to stop encoding
frame=  135 fps= 59 q=69.0 size=       0kB time=0.09 bitrate=   4.4kbits/s dup=132 drop=0    
frame=  175 fps= 54 q=69.0 size=       0kB time=0.13 bitrate=   3.0kbits/s dup=171 drop=0    
frame=  255 fps= 63 q=63.0 size=       0kB time=0.21 bitrate=   1.9kbits/s dup=249 drop=0    
frame=  335 fps= 70 q=62.0 size=       0kB time=0.29 bitrate=   1.3kbits/s dup=327 drop=0    
frame=  415 fps= 76 q=60.0 size=       0kB time=0.37 bitrate=   1.0kbits/s dup=405 drop=0    
frame=  490 fps= 80 q=59.0 size=      17kB time=0.44 bitrate= 308.0kbits/s dup=478 drop=11    
frame=  570 fps= 84 q=58.0 size=      20kB time=0.52 bitrate= 311.0kbits/s dup=556 drop=11    
frame=  650 fps= 86 q=58.0 size=      23kB time=0.60 bitrate= 306.2kbits/s dup=634 drop=11    
frame=  730 fps= 88 q=57.0 size=      26kB time=0.68 bitrate= 306.6kbits/s dup=712 drop=11    
frame=  810 fps= 89 q=56.0 size=      29kB time=0.76 bitrate= 306.5kbits/s dup=790 drop=11    
frame=  890 fps= 89 q=55.0 size=      32kB time=0.84 bitrate= 306.9kbits/s dup=868 drop=11    
frame=  971 fps= 89 q=55.0 size=      34kB time=0.92 bitrate= 303.9kbits/s dup=947 drop=11    
frame= 1050 fps= 89 q=54.0 size=      38kB time=1.00 bitrate= 309.7kbits/s dup=1024 drop=11    
frame= 1130 fps= 88 q=54.0 size=      41kB time=1.08 bitrate= 307.1kbits/s dup=1102 drop=11    
frame= 1171 fps= 88 q=54.0 size=      42kB time=1.12 bitrate= 307.0kbits/s dup=1142 drop=11    
frame= 1211 fps= 88 q=53.0 size=      44kB time=1.16 bitrate= 307.2kbits/s dup=1181 drop=11    

...

frame=6113109 fps= 75 q=56.0 size=  320234kB time=6113.05 bitrate= 429.1kbits/s dup=5960401 drop=11    
frame=6113149 fps= 75 q=56.0 size=  320237kB time=6113.10 bitrate= 429.1kbits/s dup=5960440 drop=11    
frame=6113189 fps= 75 q=56.0 size=  320239kB time=6113.14 bitrate= 429.1kbits/s dup=5960479 drop=11    
frame=6113229 fps= 75 q=56.0 size=  320241kB time=6113.18 bitrate= 429.1kbits/s dup=5960518 drop=11    
frame=6113269 fps= 75 q=56.0 size=  320242kB time=6113.21 bitrate= 429.1kbits/s dup=5960557 drop=11    
frame=6113349 fps= 75 q=56.0 size=  320244kB time=6113.28 bitrate= 429.1kbits/s dup=5960635 drop=11    
frame=6113389 fps= 75 q=56.0 size=  320247kB time=6113.34 bitrate= 429.1kbits/s dup=5960674 drop=11    
frame=6113429 fps= 75 q=56.0 size=  320248kB time=6113.37 bitrate= 429.1kbits/s dup=5960713 drop=11    
frame=6113509 fps= 75 q=56.0 size=  320252kB time=6113.44 bitrate= 429.1kbits/s dup=5960791 drop=11    
frame=6113549 fps= 75 q=56.0 size=  320254kB time=6113.49 bitrate= 429.1kbits/s dup=5960830 drop=11    
frame=6113629 fps= 75 q=56.0 size=  320257kB time=6113.58 bitrate= 429.1kbits/s dup=5960908 drop=11    
frame=6113669 fps= 75 q=56.0 size=  320260kB time=6113.62 bitrate= 429.1kbits/s dup=5960947 drop=11    
frame=6113749 fps= 75 q=56.0 size=  320263kB time=6113.70 bitrate= 429.1kbits/s dup=5961025 drop=11    
frame=6113829 fps= 75 q=56.0 size=  320266kB time=6113.78 bitrate= 429.1kbits/s dup=5961103 drop=11    
frame=6113909 fps= 75 q=56.0 size=  320269kB time=6113.86 bitrate= 429.1kbits/s dup=5961181 drop=11    
frame=6113989 fps= 75 q=56.0 size=  320273kB time=6113.94 bitrate= 429.1kbits/s dup=5961259 drop=11    
frame=6114069 fps= 75 q=56.0 size=  320275kB time=6114.02 bitrate= 429.1kbits/s dup=5961337 drop=11    
frame=6114149 fps= 75 q=56.0 size=  320278kB time=6114.09 bitrate= 429.1kbits/s dup=5961415 drop=11    
frame=6114229 fps= 75 q=56.0 size=  320282kB time=6114.18 bitrate= 429.1kbits/s dup=5961493 drop=11    
frame=6114309 fps= 75 q=56.0 size=  320285kB time=6114.26 bitrate= 429.1kbits/s dup=5961571 drop=11    
frame=6114389 fps= 75 q=56.0 size=  320287kB time=6114.32 bitrate= 429.1kbits/s dup=5961649 drop=11    
frame=6114469 fps= 75 q=56.0 size=  320291kB time=6114.42 bitrate= 429.1kbits/s dup=5961727 drop=11    
frame=6114549 fps= 75 q=56.0 size=  320293kB time=6114.49 bitrate= 429.1kbits/s dup=5961805 drop=11    
frame=6114629 fps= 75 q=56.0 size=  320297kB time=6114.58 bitrate= 429.1kbits/s dup=5961883 drop=11    
frame=6114709 fps= 75 q=56.0 size=  320300kB time=6114.65 bitrate= 429.1kbits/s dup=5961961 drop=11    
frame=6114789 fps= 75 q=56.0 size=  320303kB time=6114.72 bitrate= 429.1kbits/s dup=5962039 drop=11    
frame=6114869 fps= 75 q=56.0 size=  320306kB time=6114.81 bitrate= 429.1kbits/s dup=5962117 drop=11    
frame=6114949 fps= 75 q=56.0 size=  320308kB time=6114.88 bitrate= 429.1kbits/s dup=5962195 drop=11    
frame=6115029 fps= 75 q=56.0 size=  320311kB time=6114.95 bitrate= 429.1kbits/s dup=5962273 drop=11    
frame=6115109 fps= 75 q=56.0 size=  320315kB time=6115.06 bitrate= 429.1kbits/s dup=5962351 drop=11    
frame=6115189 fps= 75 q=56.0 size=  320318kB time=6115.14 bitrate= 429.1kbits/s dup=5962429 drop=11    
frame=6115269 fps= 75 q=56.0 size=  320321kB time=6115.22 bitrate= 429.1kbits/s dup=5962507 drop=11    
frame=6115349 fps= 75 q=56.0 size=  320323kB time=6115.30 bitrate= 429.1kbits/s dup=5962585 drop=11    
frame=6115429 fps= 75 q=56.0 size=  320326kB time=6115.37 bitrate= 429.1kbits/s dup=5962663 drop=11    
frame=6115509 fps= 75 q=56.0 size=  320329kB time=6115.46 bitrate= 429.1kbits/s dup=5962741 drop=11    
frame=6115549 fps= 75 q=-1.0 Lsize=  394341kB time=6115.55 bitrate= 528.2kbits/s dup=5962780 drop=11    
video:224753kB audio:95556kB global headers:0kB muxing overhead 23.112701%
[libx264 @ 0x8ee9e60] frame I:24480 Avg QP:43.84  size:  2723
[libx264 @ 0x8ee9e60] frame P:1534646 Avg QP:50.83  size:    43
[libx264 @ 0x8ee9e60] frame B:4556423 Avg QP:51.00  size:    22
[libx264 @ 0x8ee9e60] consecutive B-frames:  0.5%  0.4%  0.3% 98.8%
[libx264 @ 0x8ee9e60] mb I  I16..4: 82.4%  0.0% 17.6%
[libx264 @ 0x8ee9e60] mb P  I16..4:  0.1%  0.0%  0.0%  P16..4:  0.9%  0.0%  0.1%  0.0%  0.0%    skip:98.9%
[libx264 @ 0x8ee9e60] mb B  I16..4:  0.0%  0.0%  0.0%  B16..8:  1.8%  0.0%  0.0%  direct: 0.0%  skip:512.8%  L0:69.5% L1:30.5% BI: 0.0%
[libx264 @ 0x8ee9e60] final ratefactor: 44.99
[libx264 @ 0x8ee9e60] coded y,uvDC,uvAC intra: 16.3% 22.1% 0.0% inter: 0.0% 0.0% 0.0%
[libx264 @ 0x8ee9e60] i16 v,h,dc,p: 47% 30% 17%  7%
[libx264 @ 0x8ee9e60] i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 24% 16% 42%  4%  3%  3%  3%  3%  1%
[libx264 @ 0x8ee9e60] i8c dc,h,v,p: 93%  4%  3%  0%
[libx264 @ 0x8ee9e60] Weighted P-Frames: Y:0.0% UV:0.0%
[libx264 @ 0x8ee9e60] ref P L0: 93.4%  2.3%  4.0%  0.2%  0.0%
[libx264 @ 0x8ee9e60] ref B L0: 99.7%  0.3%
[libx264 @ 0x8ee9e60] kb/s:301.06

```

---

### Post by FakeOutdoorsman on 2013-10-31
Try this:
```
mkdir ffmpeg_static && cd ffmpeg_static
wget http://ffmpeg.gusari.org/static/32bit/ffmpeg.static.32bit.2013-10-25.tar.gz
tar xzvf ffmpeg.static.32bit.2013-10-25.tar.gz
./ffmpeg -i ~/input.flv -c:v libx264 -preset fast -profile:v baseline -level 3 -vf "scale=640:trunc(ow/a/2)*2,format=yuv420p" -c:a aac -strict -2 -b:a 192k -movflags faststart ~/output.mp4
```

---

### Post by chaemil on 2013-11-04
Thank you! This seems to work the best! But the 64bit binary on 64bit Ubuntu 12.04 is very slow. For now I'm using the old 32bit server for testing. Will test the 64bit later on new 8core AMD soon :)

---

### Post by FakeOutdoorsman on 2013-11-04
You could always use a faster preset. See the [FFmpeg and x264 Encoding Guide](https://trac.ffmpeg.org/wiki/x264EncodingGuide). I don't have an example command for the VP8/Vorbis in webm since I don't ever use that, but see the [vpx (WebM) Encoding Guide](https://trac.ffmpeg.org/wiki/vpxEncodingGuide) for more info on that.

---

### Post by chaemil on 2013-11-07
Ok thank you! Will try it.

---

