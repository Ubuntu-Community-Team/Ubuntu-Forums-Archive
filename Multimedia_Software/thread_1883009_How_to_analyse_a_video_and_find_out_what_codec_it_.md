---
title: "How to analyse a video and find out what codec it uses and other info"
date: 2011-11-18
forum: Multimedia Software
---

### Post by CrimpJiggler on 2011-11-18
In Ubuntu how can I find out what codecs (as in how the video and audio streams are encoded) a video contains? There must be some kinda simple program that will tell you everything about a video file such as how the video stream is encoded, how the audio stream is encoded, if it contains subtitles or not etc. Avidemux is a brilliant video editing program that I use to convert video files but as far as I know it doesn't give you info on video files.

---

### Post by MoreOrLess on 2011-11-18
```
apt-get install mediainfo
```EDIT: (or mediainfo-gui)

---

### Post by andrew.46 on 2011-11-18
Mediainfo is great, specifically for matroska containers there is always mkvinfo:

```

andrew@skamandros~/html/andrews-corner/tmp$ **[COLOR="Red"]mkvinfo matrix_sparring_h10.mkv [/COLOR]**
+ EBML head
|+ EBML version: 1
|+ EBML read version: 1
|+ EBML maximum ID length: 4
|+ EBML maximum size length: 8
|+ Doc type: matroska
|+ Doc type version: 2
|+ Doc type read version: 2
+ Segment, size 24838212
|+ Seek head (subentries will be skipped)
|+ EbmlVoid (size: 4029)
|+ Segment information
| + Timecode scale: 1000000
| + Muxing application: libebml v1.2.2 + libmatroska v1.3.0
| + Writing application: mkvmerge v5.0.1 ('Es ist Sommer') built on Oct 10 2011 19:36:05
| + Duration: 262.385s (00:04:22.385)
| + Date: Sat Nov  5 20:57:30 2011 UTC
| + Title: Matrix sparring scene
| + Segment UID: 0x0b 0x28 0x1d 0x00 0x51 0x67 0xf7 0xa3 0xf5 0xdf 0x8b 0x84 0xe3 0x1d 0x83 0x4b
|+ Segment tracks
| + A track
|  + Track number: 1
|  + Track UID: 3869488441
|  + Track type: video
|  + Lacing flag: 0
|  + MinCache: 1
|  + Codec ID: V_MPEG4/ISO/AVC
|  + CodecPrivate, length 48 (h.264 profile: High 10 @L3.2)
|  + Default duration: 40.000ms (25.000 fps for a video track)
|  + Name: Encoded with x264 High 10 Profile (Hi10P)
|  + Video track
|   + Pixel width: 720
|   + Pixel height: 416
|   + Display width: 1024
|   + Display height: 416
|  + Content encodings
|   + Content encoding
|    + Content compression
|     + Algorithm: 3 (header removal)
|     + Settings: length 1, data:  0x00
| + A track
|  + Track number: 2
|  + Track UID: 2920820996
|  + Track type: audio
|  + Codec ID: A_AAC
|  + CodecPrivate, length 5
|  + Default duration: 23.220ms (43.066 fps for a video track)
|  + Name: Encoded with neroAacEnc 1.5.4.0
|  + Audio track
|   + Sampling frequency: 44100
|   + Channels: 2
|+ EbmlVoid (size: 1110)
|+ Chapters
| + EditionEntry
|  + EditionFlagHidden: 0
|  + EditionFlagDefault: 0
|  + EditionUID: 2885960509
|  + ChapterAtom
|   + ChapterUID: 3740677497
|   + ChapterTimeStart: 00:00:00.059000000
|   + ChapterFlagHidden: 0
|   + ChapterFlagEnabled: 1
|   + ChapterDisplay
|    + ChapterString: 00:00:00.059
|    + ChapterLanguage: eng
|+ EbmlVoid (size: 101)
|+ Cluster
andrew@skamandros~/html/andrews-corner/tmp$ 

```

and also ffprobe:

```

andrew@skamandros~/html/andrews-corner/tmp$**[COLOR="Red"] ffprobe matrix_sparring_h10.mkv [/COLOR]**
ffprobe version N-34914-g7056f13, Copyright (c) 2007-2011 the FFmpeg developers
  built on Nov 17 2011 09:44:22 with gcc 4.5.3
  configuration: --prefix=/usr --mandir=/usr/man --enable-postproc --enable-avfilter --enable-pthreads --enable-shared --disable-static --disable-ffserver --disable-avconv --enable-libvorbis --enable-libmp3lame --enable-libx264 --enable-libfaac --enable-libvpx --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libvo-aacenc --enable-libvo-amrwbenc --enable-libspeex --enable-zlib --enable-libxvid --enable-libfreetype --enable-x11grab --enable-nonfree --enable-gpl --enable-version3
  libavutil    51. 25. 0 / 51. 25. 0
  libavcodec   53. 34. 0 / 53. 34. 0
  libavformat  53. 20. 0 / 53. 20. 0
  libavdevice  53.  4. 0 / 53.  4. 0
  libavfilter   2. 48. 1 /  2. 48. 1
  libswscale    2.  1. 0 /  2.  1. 0
  libpostproc  51.  2. 0 / 51.  2. 0
Input #0, matroska,webm, from 'matrix_sparring_h10.mkv':
  Metadata:
    title           : Matrix sparring scene
  Duration: 00:04:22.38, start: 0.000000, bitrate: 757 kb/s
    Chapter #0.0: start 0.059000, end 262.385000
    Metadata:
      title           : 00:00:00.059
    Stream #0:0(eng): Video: h264 (High 10), yuv420p10le, 720x416 [SAR 64:45 DAR 32:13], 25 fps, 25 tbr, 1k tbn, 50 tbc (default)
    Metadata:
      title           : Encoded with x264 High 10 Profile (Hi10P)
    Stream #0:1(eng): Audio: aac, 44100 Hz, stereo, s16 (default)
    Metadata:
      title           : Encoded with neroAacEnc 1.5.4.0

andrew@skamandros~/html/andrews-corner/tmp$ 

```

but perhaps mediainfo is the most general purpose:

```

andrew@skamandros~/html/andrews-corner/tmp$ **[COLOR="Red"]mediainfo matrix_sparring_h10.mkv [/COLOR]**
General
Unique ID                                : 14829788043047948209532235037227713355 (0xB281D005167F7A3F5DF8B84E31D834B)
Complete name                            : matrix_sparring_h10.mkv
Format                                   : Matroska
Format version                           : Version 2
File size                                : 23.7 MiB
Duration                                 : 4mn 22s
Overall bit rate                         : 757 Kbps
Movie name                               : Matrix sparring scene
Encoded date                             : UTC 2011-11-05 20:57:30
Writing application                      : mkvmerge v5.0.1 ('Es ist Sommer') built on Oct 10 2011 19:36:05
Writing library                          : libebml v1.2.2 + libmatroska v1.3.0

Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : High 10@L3.2
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 16 frames
Muxing mode                              : Header stripping
Codec ID                                 : V_MPEG4/ISO/AVC
Duration                                 : 4mn 22s
Width                                    : 720 pixels
Height                                   : 416 pixels
Display aspect ratio                     : 2.462
Frame rate mode                          : Variable
Frame rate                               : 25.000 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 10 bits
Scan type                                : Progressive
Title                                    : Encoded with x264 High 10 Profile (Hi10P)
Writing library                          : x264 core 119 r2106 07efeb4
Encoding settings                        : cabac=1 / ref=16 / deblock=1:-1:-1 / analyse=0x3:0x133 / me=umh / subme=10 / psy=1 / psy_rd=1.00:0.15 / mixed_ref=1 / me_range=24 / chroma_me=1 / trellis=2 / 8x8dct=1 / cqm=0 / deadzone=21,11 / fast_pskip=1 / chroma_qp_offset=-3 / threads=3 / sliced_threads=0 / nr=0 / decimate=1 / interlaced=0 / bluray_compat=0 / constrained_intra=0 / bframes=8 / b_pyramid=2 / b_adapt=2 / b_bias=0 / direct=3 / weightb=1 / open_gop=0 / weightp=2 / keyint=250 / keyint_min=25 / scenecut=40 / intra_refresh=0 / rc_lookahead=60 / rc=crf / mbtree=1 / crf=24.0 / qcomp=0.60 / qpmin=0 / qpmax=81 / qpstep=4 / ip_ratio=1.40 / aq=1:1.00
Language                                 : English

Audio
ID                                       : 2
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : LC
Codec ID                                 : A_AAC
Duration                                 : 4mn 22s
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 44.1 KHz
Compression mode                         : Lossy
Title                                    : Encoded with neroAacEnc 1.5.4.0
Language                                 : English

Menu
00:00:00.059                             : en:00:00:00.059


andrew@skamandros~/html/andrews-corner/tmp$ 

```

---

