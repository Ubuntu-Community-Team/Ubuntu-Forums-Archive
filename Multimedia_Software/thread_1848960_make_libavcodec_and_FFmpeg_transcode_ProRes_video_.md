---
title: "make libavcodec and FFmpeg transcode ProRes video to H.264"
date: 2011-09-23
forum: Multimedia Software
---

### Post by philippe@telecine.ca on 2011-09-23
Hello,
 
I'm trying to make libavcodec and FFmpeg transcode ProRes video to H.264.
 
- Since September 15 2011, libavcodec supports ProRes.
- I enabled GPL 3 (--enable-gpl --enable-version3)
- I updated libavcodec (53.14.0)
- Libx264 is enabled (--enalbe-libx264)
 
I get > (buffer @ 0x393600) Invalide pixel format '-1' error.
 
Someone had that work? Can give full details of how you installed it?
 
Thanks!
 
Philippe
 
FFmpeg output:
 
```

[FONT=Courier New]ffmpeg version N-32577-ga30ef63, Copyright (c) 2000-2011 the FFmpeg developers[/FONT]
[FONT=Courier New]built on Sep 23 2011 10:58:29 with gcc 4.5.2[/FONT]
[FONT=Courier New]configuration: --enable-gpl --enable-version3 --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-nonfree --enable-postproc --enable-version3 --enable-x11grab[/FONT]
[FONT=Courier New]libavutil    51. 16. 0 / 51. 16. 0[/FONT]
[FONT=Courier New]libavcodec   53. 14. 0 / 53. 14. 0[/FONT]
[FONT=Courier New]libavformat  53. 12. 0 / 53. 12. 0[/FONT]
[FONT=Courier New]libavdevice  53.  3. 0 / 53.  3. 0[/FONT]
[FONT=Courier New]libavfilter   2. 40. 0 /  2. 40. 0[/FONT]
[FONT=Courier New]libswscale    2.  1. 0 /  2.  1. 0[/FONT]
[FONT=Courier New]libpostproc  51.  2. 0 / 51.  2. 0[/FONT]
[FONT=Courier New]Seems stream 0 codec frame rate differs from container frame rate: 2997.00 (2997/1) -> 29.97 (2997/100)[/FONT]
[FONT=Courier New]Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/administrator/Desktop/ProResTest.mov':[/FONT]
[FONT=Courier New]Metadata:[/FONT]
[FONT=Courier New]major_brand     : qt  [/FONT]
[FONT=Courier New]minor_version   : 537199360[/FONT]
[FONT=Courier New]compatible_brands: qt  [/FONT]
[FONT=Courier New]creation_time   : 2011-09-19 19:40:11[/FONT]
[FONT=Courier New]Duration: 00:00:15.08, start: 0.000000, bitrate: 59806 kb/s[/FONT]
[FONT=Courier New]Stream #0.0(eng): Video: prores (apcn / 0x6E637061), 1280x720, 59804 kb/s, 29.97 fps, 29.97 tbr, 2997 tbn, 2997 tbc[/FONT]
[FONT=Courier New]Metadata:[/FONT]
[FONT=Courier New]creation_time   : 2011-09-19 19:40:11[/FONT]
[FONT=Courier New]File '/home/administrator/Desktop/output.mp4' already exists. Overwrite ? (y/N) y[/FONT]
[FONT=Courier New](buffer @ 0xa393600) Invalid pixel format '-1'[/FONT]
[FONT=Courier New]Error opening filters![/FONT]

```

---

### Post by ajgreeny on 2011-09-23
Have you tried installing the **libavcodec-extra-52** package?

There are a number of -extra libav* packages that I always add in place of the standard packages as they add a number of additional actions when using ffmpeg.  They are the new equivalent of the older "unstripped" versions of the packages.  I have no idea if they will help, but they will certainly not cause you any problems, so must be worth trying.

---

### Post by FakeOutdoorsman on 2011-09-23
> **philippe@telecine.ca said:**
> Someone had that work? Can give full details of how you installed it?

I believe there are currently two ProRes decoders in FFmpeg. One requires that you compile FFmpeg with *--enable-version2*. I'm not sure if this will conflict with *--enable-version3* and anything that requires that (libopencore).

With *--enable-version2* you should end up with the prores_gpl and prores_lgpl decoders. I haven't actually tested any of this myself though.

---

### Post by andrew.46 on 2011-09-23
Thanks FakeOutdoorsman for solving this issue which also frustrated me a little :). I compiled with version2 *and* version3 options and saw the following:

```

Enabled decoders:

[...]
bfi			kgv1			pcm_u32be
bink			kmvc			pcm_u32le
binkaudio_dct		lagarith		pcm_u8
binkaudio_rdft		**[COLOR="Red"]libopencore_amrnb[/COLOR]**	pcm_zork
bintext			**[COLOR="Red"]libopencore_amrwb[/COLOR]**	pcx
bmp			libvpx			pgm
c93			loco			pgmyuv
cavs			mace3			pgssub
cdgraphics		mace6			pictor
cinepak			mdec			png
cljr			mimic			ppm
cook			mjpeg			**[COLOR="Red"]prores_gpl[/COLOR]**
cscd			mjpegb			**[COLOR="Red"]prores_lgpl[/COLOR]**
cyuv			mlp			ptx
dca			mmvideo			qcelp
dfa			motionpixels		qdm2
[...]

```

And then tried to convert an Apple prores video:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]ffmpeg -i AppleProRes422.mov -an -vcodec libx264 -preset fast -crf 22 -threads 0 test.mp4[/COLOR]**
ffmpeg version N-32821-g0bc5d4f, Copyright (c) 2000-2011 the FFmpeg developers
  built on Sep 24 2011 07:20:54 with gcc 4.5.2
  configuration: --prefix=/usr --mandir=/usr/man --enable-postproc --enable-avfilter --enable-pthreads --enable-shared --disable-static --disable-ffserver --enable-libvorbis --enable-libmp3lame --enable-libx264 --enable-libfaac --enable-libvpx --enable-zlib --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libxvid --enable-libfreetype --enable-x11grab --enable-nonfree --enable-gpl --enable-version3 --enable-version2
  libavutil    51. 17. 0 / 51. 17. 0
  libavcodec   53. 17. 0 / 53. 17. 0
  libavformat  53. 13. 0 / 53. 13. 0
  libavdevice  53.  4. 0 / 53.  4. 0
  libavfilter   2. 43. 3 /  2. 43. 3
  libswscale    2.  1. 0 /  2.  1. 0
  libpostproc  51.  2. 0 / 51.  2. 0

Seems stream 0 codec frame rate differs from container frame rate: 2997.00 (2997/1) -> 29.97 (2997/100)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'AppleProRes422.mov':
  Metadata:
    major_brand     : qt  
    minor_version   : 537199360
    compatible_brands: qt  
    creation_time   : 2011-03-30 16:15:56
  Duration: 00:01:14.27, start: -31.262930, bitrate: 10923 kb/s
    Stream #0:0(eng): Video: prores (apch / 0x68637061), yuv422p10le, 720x486, 61092 kb/s, 29.97 fps, 29.97 tbr, 2997 tbn, 2997 tbc
    Metadata:
      creation_time   : 2011-03-30 16:15:56
    Stream #0:1(eng): Subtitle: none (c608 / 0x38303663)
    Metadata:
      creation_time   : 2011-03-30 16:15:56
    Stream #0:2(eng): Audio: pcm_s24le (in24 / 0x34326E69), 48000 Hz, 1 channels, s32, 1152 kb/s
    Metadata:
      creation_time   : 2011-03-30 16:15:56
    Stream #0:3(eng): Audio: pcm_s24le (in24 / 0x34326E69), 48000 Hz, 1 channels, s32, 1152 kb/s
    Metadata:
      creation_time   : 2011-03-30 16:15:56
    Stream #0:4(eng): Audio: pcm_s24le (in24 / 0x34326E69), 48000 Hz, 1 channels, s32, 1152 kb/s
    Metadata:
      creation_time   : 2011-03-30 16:15:56
    Stream #0:5(eng): Audio: pcm_s24le (in24 / 0x34326E69), 48000 Hz, 1 channels, s32, 1152 kb/s
    Metadata:
      creation_time   : 2011-03-30 16:15:56
    Stream #0:6(eng): Audio: pcm_s24le (in24 / 0x34326E69), 48000 Hz, 1 channels, s32, 1152 kb/s
    Metadata:
      creation_time   : 2011-03-30 16:15:56
    Stream #0:7(eng): Audio: pcm_s24le (in24 / 0x34326E69), 48000 Hz, 1 channels, s32, 1152 kb/s
    Metadata:
      creation_time   : 2011-03-30 16:15:56
    Stream #0:8(eng): Audio: pcm_s24le (in24 / 0x34326E69), 48000 Hz, 1 channels, s32, 1152 kb/s
    Metadata:
      creation_time   : 2011-03-30 16:15:56
    Stream #0:9(eng): Audio: pcm_s24le (in24 / 0x34326E69), 48000 Hz, 1 channels, s32, 1152 kb/s
    Metadata:
      creation_time   : 2011-03-30 16:15:56
    Stream #0:10(eng): Data: none (tmcd / 0x64636D74)
    Metadata:
      creation_time   : 2011-03-30 16:15:56
Incompatible pixel format 'yuv422p10le' for codec 'libx264', auto-selecting format 'yuv420p'
[buffer @ 0x81f5660] w:720 h:486 pixfmt:yuv422p10le tb:1/1000000 sar:0/1 sws_param:
[buffersink @ 0x8099100] auto-inserting filter 'auto-inserted scale 0' between the filter 'src' and the filter 'out'
[scale @ 0x8099520] w:720 h:486 fmt:yuv422p10le -> w:720 h:486 fmt:yuv420p flags:0x4
[libx264 @ 0x81f5ee0] using cpu capabilities: MMX2 SSE2Fast SSSE3 Cache64
[libx264 @ 0x81f5ee0] profile High, level 3.1
[libx264 @ 0x81f5ee0] 264 - core 116 r2074 2641b9e - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - http://www.videolan.org/x264.html - options: cabac=1 ref=2 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=6 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=3 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=0 weightp=1 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=30 rc=crf mbtree=1 crf=22.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.40 aq=1:1.00
Output #0, mp4, to 'test.mp4':
  Metadata:
    major_brand     : qt  
    minor_version   : 537199360
    compatible_brands: qt  
    creation_time   : 2011-03-30 16:15:56
    encoder         : Lavf53.13.0
    Stream #0:0(eng): Video: h264 (![0][0][0] / 0x0021), yuv420p, 720x486, q=-1--1, 2997 tbn, 29.97 tbc
    Metadata:
      creation_time   : 2011-03-30 16:15:56
Stream mapping:
  **[COLOR="Red"]Stream #0.0 -> #0.0 (prores_gpl -> libx264)[/COLOR]**
Press [q] to stop, [?] for help
frame= 1283 fps= 52 q=-1.0 Lsize=     979kB time=00:00:42.74 bitrate= 187.5kbits/s dup=937 drop=0    
video:958kB audio:0kB global headers:0kB muxing overhead 2.171840%
frame I:6     Avg QP:18.66  size: 46746
[libx264 @ 0x81f5ee0] frame P:323   Avg QP:20.68  size:  1461
[libx264 @ 0x81f5ee0] frame B:954   Avg QP:29.45  size:   239
[libx264 @ 0x81f5ee0] consecutive B-frames:  0.9%  0.0%  0.0% 99.1%
[libx264 @ 0x81f5ee0] mb I  I16..4:  4.5% 64.7% 30.8%
[libx264 @ 0x81f5ee0] mb P  I16..4:  0.0%  0.0%  0.0%  P16..4: 13.1%  4.0%  2.7%  0.0%  0.0%    skip:80.1%
[libx264 @ 0x81f5ee0] mb B  I16..4:  0.2%  0.2%  0.0%  B16..8:  5.5%  0.6%  0.0%  direct: 1.2%  skip:92.3%  L0:49.2% L1:44.2% BI: 6.6%
[libx264 @ 0x81f5ee0] 8x8 transform intra:59.4% inter:67.1%
[libx264 @ 0x81f5ee0] coded y,uvDC,uvAC intra: 62.6% 75.4% 47.0% inter: 1.9% 3.3% 0.2%
[libx264 @ 0x81f5ee0] i16 v,h,dc,p: 32% 24% 36%  9%
[libx264 @ 0x81f5ee0] i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 19% 14% 37%  4%  4%  5%  3%  6%  6%
[libx264 @ 0x81f5ee0] i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 32% 27% 11%  4%  5%  6%  4%  5%  5%
[libx264 @ 0x81f5ee0] i8c dc,h,v,p: 44% 25% 28%  3%
[libx264 @ 0x81f5ee0] Weighted P-Frames: Y:2.2% UV:1.2%
[libx264 @ 0x81f5ee0] ref P L0: 65.7% 34.3%
[libx264 @ 0x81f5ee0] ref B L0: 66.6% 33.4%
[libx264 @ 0x81f5ee0] ref B L1: 84.8% 15.2%
[libx264 @ 0x81f5ee0] kb/s:183.13

```

Mind you the output video simply showed a single frame for the entire clip, I shall have to investigate a little further,,,,

---

