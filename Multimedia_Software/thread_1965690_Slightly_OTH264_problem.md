---
title: "Slightly OT:H264 problem"
date: 2012-04-26
forum: Multimedia Software
---

### Post by Jethro_uk on 2012-04-26
I have an MKV file, which purports to contain an H264 encoded video. When I try to play it on my network media player (a Cyclone) only audio plays - I get a blank screen.

Trying to open it in AVIDEMUX, I just get a green screen.

However, it plays fine in VLC.

Clearly there's a subtle problems somewhere. Can anyone suggest a tool to fix it ?

---

### Post by BicyclerBoy on 2012-04-26
Install/run in terminal:
mediainfo yourfile.mkv
ffmpeg -i yourfile.mkv

post the results..

VLC almost always works..

---

### Post by Jethro_uk on 2012-04-26
Thanks ... I see a warning from ffmpeg, is this the cause ?

```
General
Unique ID                                : 234328076679398328961673617426248625966 (0xB049F22B02158C87AF670F5E2F73EF2E)
Complete name                            : my.mkv
Format                                   : Matroska
Format version                           : Version 2
File size                                : 849 MiB
Duration                                 : 44mn 54s
Overall bit rate                         : 2 644 Kbps
Encoded date                             : UTC 2012-04-17 22:16:47
Writing application                      : mkvmerge v5.2.1 ('A Far Off Place') built on Jan  2 2012 23:21:10
Writing library                          : libebml v1.2.3 + libmatroska v1.3.0

Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : High@L4.1
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 5 frames
Muxing mode                              : Header stripping
Codec ID                                 : V_MPEG4/ISO/AVC
Duration                                 : 44mn 54s
Bit rate                                 : 2 208 Kbps
Width                                    : 1 280 pixels
Height                                   : 720 pixels
Display aspect ratio                     : 16:9
Frame rate                               : 25.000 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.096
Stream size                              : 709 MiB (83%)
Writing library                          : x264 core 122 r2184 5c85e0a
Encoding settings                        : cabac=1 / ref=5 / deblock=1:0:0 / analyse=0x3:0x113 / me=umh / subme=8 / psy=1 / psy_rd=1.00:0.00 / mixed_ref=1 / me_range=16 / chroma_me=1 / trellis=1 / 8x8dct=1 / cqm=0 / deadzone=21,11 / fast_pskip=1 / chroma_qp_offset=-2 / threads=12 / sliced_threads=0 / nr=0 / decimate=1 / interlaced=0 / bluray_compat=0 / constrained_intra=0 / bframes=3 / b_pyramid=2 / b_adapt=2 / b_bias=0 / direct=3 / weightb=1 / open_gop=0 / weightp=2 / keyint=250 / keyint_min=25 / scenecut=40 / intra_refresh=0 / rc_lookahead=50 / rc=crf / mbtree=1 / crf=21.0 / qcomp=0.60 / qpmin=0 / qpmax=69 / qpstep=4 / ip_ratio=1.40 / aq=1:1.00

Audio
ID                                       : 2
Format                                   : AC-3
Format/Info                              : Audio Coding 3
Format profile                           : Dolby Digital
Mode extension                           : CM (complete main)
Muxing mode                              : Header stripping
Codec ID                                 : A_AC3
Duration                                 : 44mn 54s
Bit rate mode                            : Constant
Bit rate                                 : 384 Kbps
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 48.0 KHz
Bit depth                                : 16 bits
Compression mode                         : Lossy
Delay relative to video                  : 96ms
Stream size                              : 123 MiB (15%)
Language                                 : English


```


```
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1.3, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1.3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Dec 21 2011 18:37:21, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 50.00 (50/1) -> 25.00 (25/1)
Input #0, matroska, from 'my.mkv':
  Duration: 00:44:54.46, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: h264, yuv420p, 1280x720, PAR 1:1 DAR 16:9, 25 tbr, 1k tbn, 50 tbc
    Stream #0.1(eng): Audio: ac3, 48000 Hz, stereo, s16

```

---

### Post by SeijiSensei on 2012-04-26
> **Jethro_uk said:**
> I have an MKV file, which purports to contain an H264 encoded video. When I try to play it on my network media player (a Cyclone) only audio plays - I get a blank screen.

Looking at [this Cyclone]("http://www.maplin.co.uk/500gb-cyclone-media-player-227469"), I don't see any support for Matroska (MKV) only "DAT VOB MPEG1/2/4 AVI (Divx,xvid)". It also doesn't support SSA or A*S subtitle formats, either. Many commercial players don't support Matroska or SSA because these formats aren't endorsed by entities like Microsoft or Sony.  I admit to being puzzled about how it can play the audio if it doesn't support Matroska.  If you're using a different device, look at the specifications on the file formats that it supports.

To play a Matroska file on this device, you'd need to [re-encode the file with XviD]("http://en.gentoo-wiki.com/wiki/Mencoder#XviD") and store it in the AVI container.

---

### Post by Jethro_uk on 2012-04-26
> **SeijiSensei said:**
> Looking at [this Cyclone]("http://www.maplin.co.uk/500gb-cyclone-media-player-227469"), I don't see any support for Matroska (MKV) only "DAT VOB MPEG1/2/4 AVI (Divx,xvid)". It also doesn't support SSA or A*S subtitle formats, either. Many commercial players don't support Matroska or SSA because these formats aren't endorsed by entities like Microsoft or Sony.  I admit to being puzzled about how it can play the audio if it doesn't support Matroska.  If you're using a different device, look at the specifications on the file formats that it supports.

To play a Matroska file on this device, you'd need to [re-encode the file with XviD]("http://en.gentoo-wiki.com/wiki/Mencoder#XviD") and store it in the AVI container.

Sorry, it's the Cyclone media adapter V2 [http://www.ebuyer.com/product/188647]("http://www.ebuyer.com/product/188647")- and it certainly does play MKV files.

---

### Post by SeijiSensei on 2012-04-26
Another possibility is that the device doesn't like the "high" H.264 [profile]("http://en.wikipedia.org/wiki/H.264/MPEG-4_AVC#Profiles").  From the output you posted above I see

> Format profile    : High@L4.1

That's the only item in the listing that seems even vaguely dicey.  I downloaded the user's manual for the device and don't see any information on what profiles it supports.  You might try a firmware upgrade.

Find a file that plays in the device and follow the same steps as you did above to see what profile that encoding uses.

---

### Post by Jethro_uk on 2012-04-26
> **SeijiSensei said:**
> Another possibility is that the device doesn't like the "high" H.264 [profile]("http://en.wikipedia.org/wiki/H.264/MPEG-4_AVC#Profiles").  From the output you posted above I see



That's the only item in the listing that seems even vaguely dicey.  I downloaded the user's manual for the device and don't see any information on what profiles it supports.  You might try a firmware upgrade.

Find a file that plays in the device and follow the same steps as you did above to see what profile that encoding uses.

Thanks for that. Unfortunately, here's the output from a file which does play:

```
General
Unique ID                                : 197917137995844481641366161338445122350 (0x94E5744A35E0BF15A43BB7104C84CB2E)
Complete name                            : my.mkv
Format                                   : Matroska
Format version                           : Version 2
File size                                : 985 MiB
Duration                                 : 42mn 28s
Overall bit rate                         : 3 241 Kbps
Encoded date                             : UTC 2012-04-25 20:04:53
Writing application                      : mkvmerge v3.1.0 ('Happy up here') built on Jan 19 2010 12:09:24
Writing library                          : libebml v0.7.9 + libmatroska v0.8.1

Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : High@L4.1
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 8 frames
Codec ID                                 : V_MPEG4/ISO/AVC
Duration                                 : 42mn 28s
Bit rate                                 : 2 793 Kbps
Width                                    : 1 280 pixels
Height                                   : 720 pixels
Display aspect ratio                     : 16:9
Frame rate                               : 23.976 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.126
Stream size                              : 848 MiB (86%)
Writing library                          : x264 core 122 r2184 5c85e0a
Encoding settings                        : cabac=1 / ref=8 / deblock=1:-2:-2 / analyse=0x3:0x113 / me=umh / subme=9 / psy=1 / psy_rd=1.00:0.00 / mixed_ref=1 / me_range=24 / chroma_me=1 / trellis=1 / 8x8dct=1 / cqm=0 / deadzone=21,11 / fast_pskip=0 / chroma_qp_offset=-2 / threads=12 / sliced_threads=0 / nr=0 / decimate=1 / interlaced=0 / bluray_compat=0 / constrained_intra=0 / bframes=5 / b_pyramid=2 / b_adapt=1 / b_bias=0 / direct=1 / weightb=1 / open_gop=0 / weightp=2 / keyint=250 / keyint_min=23 / scenecut=40 / intra_refresh=0 / rc_lookahead=40 / rc=crf / mbtree=1 / crf=18.0 / qcomp=0.60 / qpmin=0 / qpmax=69 / qpstep=4 / ip_ratio=1.40 / aq=1:1.00
Language                                 : English

Audio
ID                                       : 2
Format                                   : AC-3
Format/Info                              : Audio Coding 3
Mode extension                           : CM (complete main)
Codec ID                                 : A_AC3
Duration                                 : 42mn 28s
Bit rate mode                            : Constant
Bit rate                                 : 384 Kbps
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 48.0 KHz
Bit depth                                : 16 bits
Compression mode                         : Lossy
Stream size                              : 117 MiB (12%)
```

as far as I can see the profile is the same ...

I have already upgraded the firmware (to one for a Mivx player) and this player has played everything I have thrown at it, except this file. Clearly *something* is awry, as Avidemux doesn't like it either.

All these video formats do my head in.

---

### Post by BicyclerBoy on 2012-04-26
The first (problem) file has stripped headers...(header removal compression), this is normal from mkvtoolnix v4.1, but has caused problems for toy-boxes.
It was also written by a later version of libmatroska..

Install mkvtoolnix packages (mkvmerge-gui) & use this to load/remux this file into a new .mkv container & set the compression to none.

[http://www.mediasmartserver.net/2010/08/09/mkv-mania-header-compression-and-the-side-effects/](http://www.mediasmartserver.net/2010/08/09/mkv-mania-header-compression-and-the-side-effects/)

---

### Post by Jethro_uk on 2012-04-28
> **BicyclerBoy said:**
> The first (problem) file has stripped headers...(header removal compression), this is normal from mkvtoolnix v4.1, but has caused problems for toy-boxes.
It was also written by a later version of libmatroska..

Install mkvtoolnix packages (mkvmerge-gui) & use this to load/remux this file into a new .mkv container & set the compression to none.

[http://www.mediasmartserver.net/2010/08/09/mkv-mania-header-compression-and-the-side-effects/](http://www.mediasmartserver.net/2010/08/09/mkv-mania-header-compression-and-the-side-effects/)

Perfect !!!!!! I have to add the mkvmerge repository to my Synaptic, as 10.04 seems locked to v3.0.0, but  once upgraded, I loaded my file in, set the "Extra Options ... Compression" to none, and wrote out the remuxed file, and it played perfectly.

I imagine, if I really could be bothered, there's a script I could write which would run mediainfo into grep, look for compressed header, and remux the file automatically if needed ....

Many thanks

---

### Post by BicyclerBoy on 2012-04-28
It is possble to build the latest mkvtoolnix for lucid using bunkus's website & sourgeforge for libmatroska etc . I could not find a ppa..

The biggest hurdle is the mkvtoolnix toolchain requirement. This was much more difficult that building the application..

H264 profiles
High@L4.1 would mean bitrate was >=30Mbps, clearly this is not the case.

---

