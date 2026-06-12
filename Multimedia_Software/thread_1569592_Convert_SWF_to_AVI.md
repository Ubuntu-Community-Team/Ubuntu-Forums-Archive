---
title: "Convert SWF to AVI?"
date: 2010-09-07
forum: Multimedia Software
---

### Post by PDA1 on 2010-09-07
I want to be able to convert SWF files to AVI.....or MP4.

FFMPEG will not do it so don't even mention it.

WinFF won't work either.



How do I do it?

---

### Post by andrew.46 on 2010-09-07
Hi PDA,

> **PDA1 said:**
> I want to be able to convert SWF files to AVI.....or MP4. FFMPEG will not do it so don't even mention it.

Well, I hate to go against direction but FFmpeg will convert *some *swf files. This sample file for example:

```
wget http://samples.mplayerhq.hu/SWF/zeldaADPCM5bit.swf
```

This converts quite neatly with FFmpeg to mp4:

```

andrew@skamandros~/Desktop$ [B][COLOR="Red"]ffmpeg -i zeldaADPCM5bit.swf \
>        -acodec libfaac -ab 64k -ac 1 \
>        -vcodec libx264 -vpre slow -crf 18 \
>        -threads 0 zelda.mp4[/COLOR][/B]
FFmpeg version SVN-r25047, Copyright (c) 2000-2010 the FFmpeg developers
  built on Sep  6 2010 14:24:55 with gcc 4.4.4
  configuration: --prefix=/usr --mandir=/usr/man --enable-postproc --enable-avfilter --enable-pthreads --enable-shared --disable-static --disable-ffserver --enable-libtheora --enable-libvorbis --enable-x11grab --enable-libmp3lame --enable-libx264 --enable-libfaac --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-zlib --enable-libvpx --enable-libgsm --enable-nonfree --enable-gpl
  libavutil     50.25. 0 / 50.25. 0
  libavcore      0. 6. 0 /  0. 6. 0
  libavcodec    52.87. 1 / 52.87. 1
  libavformat   52.78. 3 / 52.78. 3
  libavdevice   52. 2. 1 / 52. 2. 1
  libavfilter    1.38. 1 /  1.38. 1
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[swf @ 0x807b470] max_analyze_duration reached
[swf @ 0x807b470] Estimating duration from bitrate, this may be inaccurate
[B][COLOR="Red"]Input #0, swf, from 'zeldaADPCM5bit.swf':
  Duration: N/A, start: 0.000000, bitrate: N/A
    Stream #0.0: Audio: adpcm_swf, 22050 Hz, 1 channels, s16
    Stream #0.1: Video: flv, yuv420p, 160x120, 12 fps, 12 tbr, 12 tbn, 12 tbc[/COLOR][/B]
[buffer @ 0x8084330] w:160 h:120 pixfmt:yuv420p
[libx264 @ 0x807ec00] using cpu capabilities: MMX2 SSE2Fast SSSE3 Cache64
[libx264 @ 0x807ec00] profile High, level 1.1
[libx264 @ 0x807ec00] 264 - core 104 r244 c276662 - H.264/MPEG-4 AVC codec - Copyleft 2003-2010 - http://www.videolan.org/x264.html - options: cabac=1 ref=5 deblock=1:0:0 analyse=0x3:0x113 me=umh subme=8 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=3 sliced_threads=0 nr=0 decimate=1 interlaced=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=2 b_bias=0 direct=3 weightb=1 open_gop=0 weightp=2 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=50 rc=crf mbtree=1 crf=18.0 qcomp=0.60 qpmin=10 qpmax=51 qpstep=4 ip_ratio=1.41 aq=1:1.00
Output #0, mp4, to 'zelda.mp4':
  Metadata:
    encoder         : Lavf52.78.3
    Stream #0.0: Video: libx264, yuv420p, 160x120, q=10-51, 200 kb/s, 3072 tbn, 12 tbc
    Stream #0.1: Audio: libfaac, 22050 Hz, 1 channels, s16, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
Press [q] to stop encoding
frame=  358 fps= 90 q=-1.0 Lsize=     947kB time=29.67 bitrate= 261.6kbits/s    
video:798kB audio:138kB global headers:0kB muxing overhead 1.255074%
[libx264 @ 0x807ec00] frame I:17    Avg QP:19.18  size:  5393
[libx264 @ 0x807ec00] frame P:102   Avg QP:23.04  size:  3318
[libx264 @ 0x807ec00] frame B:239   Avg QP:25.44  size:  1616
[libx264 @ 0x807ec00] consecutive B-frames:  2.6%  6.5% 15.8% 75.1%
[libx264 @ 0x807ec00] mb I  I16..4:  1.5% 88.8%  9.7%
[libx264 @ 0x807ec00] mb P  I16..4:  0.2% 21.9%  3.4%  P16..4: 25.5% 27.8% 21.1%  0.0%  0.0%    skip: 0.2%
[libx264 @ 0x807ec00] mb B  I16..4:  0.1%  7.6%  0.9%  B16..8: 30.7% 22.0% 10.4%  direct:18.5%  skip: 9.7%  L0:35.9% L1:27.2% BI:36.9%
[libx264 @ 0x807ec00] 8x8 transform intra:87.4% inter:69.8%
[libx264 @ 0x807ec00] direct mvs  spatial:96.7% temporal:3.3%
[libx264 @ 0x807ec00] coded y,uvDC,uvAC intra: 96.7% 98.5% 84.5% inter: 78.2% 72.7% 29.1%
[libx264 @ 0x807ec00] i16 v,h,dc,p:  0% 71%  5% 24%
[libx264 @ 0x807ec00] i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 23% 27% 15%  4%  6%  6%  6%  5%  8%
[libx264 @ 0x807ec00] i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 21% 18%  6%  6% 11% 10%  9%  8% 11%
[libx264 @ 0x807ec00] i8c dc,h,v,p: 45% 26% 17% 11%
[libx264 @ 0x807ec00] Weighted P-Frames: Y:17.6%
[libx264 @ 0x807ec00] ref P L0: 36.6% 12.8% 21.9% 12.9% 10.6%  4.6%  0.6%
[libx264 @ 0x807ec00] ref B L0: 61.3% 24.4% 11.3%  3.1%
[libx264 @ 0x807ec00] ref B L1: 89.7% 10.3%
[libx264 @ 0x807ec00] kb/s:218.94

```

I gather that there are several different types of swf files, some of which FFmpeg will not convert, but certainly there are others that it converts easily...

Andrew

---

### Post by PDA1 on 2010-09-07
Doesn't work. Some SWF files are vector graphics (sounds like I know what I'm talking about?) and won't convert.

I tried SWFEXTRACT and that'll let you get some stuff out of SWF but not all.

Thanks for trying.

---

### Post by howefield on 2010-09-07
For the occasional file conversion, you might try something like this online file conversion site.

[http://www.media-convert.com/](http://www.media-convert.com/)

---

### Post by PDA1 on 2010-09-07
I can't win.

That's a good site.  

As you'd expect it doesn't convert- anything.  At least it didn't for me.

---

### Post by dancook79 on 2010-10-05
You might like to try

[http://sourceforge.net/projects/convertswf/](http://sourceforge.net/projects/convertswf/)

Dan Cook

---

