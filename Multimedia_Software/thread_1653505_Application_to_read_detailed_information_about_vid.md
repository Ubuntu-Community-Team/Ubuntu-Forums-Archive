---
title: "Application to read detailed information about video files"
date: 2010-12-27
forum: Multimedia Software
---

### Post by e24ohm on 2010-12-27
Is there a utility that can be used to view file information about a video file? Example: if the file was encoded with ffmpeg, and if it is H.264. In addition, what type of encoder was used for audio?

Thanks.

---

### Post by FakeOutdoorsman on 2010-12-27
You can use FFmpeg to investigate the contents of a file. Example:
```
$ ffmpeg -i IronMan.mkv
[...]
Input #0, matroska,webm, from 'IronMan.mkv':
  Duration: 00:01:48.50, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: h264, yuv420p, 1280x720, PAR 115:87 DAR 1840:783, 23.98 fps, 24 tbr, 1k tbn, 47.95 tbc
    Stream #0.1: Audio: aac, 48000 Hz, stereo, s16

```
FFmpeg shows that the input file contains H.264 video and AAC audio in a MKV container among some other details. If the video was encoded with x264 you can use *strings* to find out what encoding settings were used:
```
$ strings IronMan.mkv | grep x264
x264 - core 65 r999+1 eb3ef1b - H.264/MPEG-4 AVC codec - Copyleft 2003-2008 - http://www.videolan.org/x264.html - options: cabac=1 ref=4 deblock=1:-2:-2 analyse=0x3:0x113 me=tesa subme=9 psy_rd=1.0:0.0 mixed_ref=1 me_range=32 chroma_me=1 trellis=0 8x8dct=1 cqm=0 deadzone=6,6 chroma_qp_offset=-2 threads=3 nr=0 decimate=1 mbaff=0 bframes=3 b_pyramid=1 b_adapt=2 b_bias=0 direct=3 wpredb=1 keyint=250 keyint_min=25 scenecut=40(pre) rc=2pass bitrate=4000 ratetol=1.0 qcomp=0.60 qpmin=10 qpmax=51 qpstep=4 cplxblur=20.0 qblur=0.5 ip_ratio=1.40 pb_ratio=1.30 aq=1:1.00
```
[mediainfo](http://mediainfo.sourceforge.net/en/Download) is another useful tool:
```
$ mediainfo IronMan.mkv 
General
Unique ID                        : 192593309687601836363669245965641314523 (0x90E41F49EA2D7231824DC5CD1FB5F0DB)
Complete name                    : IronMan.mkv
Format                           : Matroska
File size                        : 53.6 MiB
Duration                         : 1mn 48s
Overall bit rate                 : 4 141 Kbps
Encoded date                     : UTC 2008-10-22 06:43:30
Writing application              : mkvmerge v2.2.0 ('Turn It On Again') built on Mar  4 2008 12:58:26
Writing library                  : libebml v0.7.7 + libmatroska v0.8.1

Video
ID                               : 1
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : High@L4.0
Format settings, CABAC           : Yes
Format settings, ReFrames        : 4 frames
Codec ID                         : V_MPEG4/ISO/AVC
Duration                         : 1mn 48s
Nominal bit rate                 : 4 000 Kbps
Width                            : 1 280 pixels
Height                           : 720 pixels
Display aspect ratio             : 2.35:1
Original display aspect ratio    : 16:9
Frame rate                       : 23.976 fps
Color space                      : YUV
Chroma subsampling               : 4:2:0
Bit depth                        : 8 bits
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.181
Writing library                  : x264 core 65 r999+1 eb3ef1b
Encoding settings                : cabac=1 / ref=4 / deblock=1:-2:-2 / analyse=0x3:0x113 / me=tesa / subme=9 / psy_rd=1.0:0.0 / mixed_ref=1 / me_range=32 / chroma_me=1 / trellis=0 / 8x8dct=1 / cqm=0 / deadzone=6,6 / chroma_qp_offset=-2 / threads=3 / nr=0 / decimate=1 / mbaff=0 / bframes=3 / b_pyramid=1 / b_adapt=2 / b_bias=0 / direct=3 / wpredb=1 / keyint=250 / keyint_min=25 / scenecut=40(pre) / rc=2pass / bitrate=4000 / ratetol=1.0 / qcomp=0.60 / qpmin=10 / qpmax=51 / qpstep=4 / cplxblur=20.0 / qblur=0.5 / ip_ratio=1.40 / pb_ratio=1.30 / aq=1:1.00

Audio
ID                               : 2
Format                           : AAC
Format/Info                      : Advanced Audio Codec
Format profile                   : LC
Codec ID                         : A_AAC
Duration                         : 1mn 48s
Channel(s)                       : 2 channels
Channel positions                : Front: L R
Sampling rate                    : 48.0 KHz
Compression mode                 : Lossy
```

---

### Post by e24ohm on 2010-12-27
Mate - thanks so much. This output is what I was looking for.

I have been trying to get videos onto my Sansa Fuze; however, they will not play. There is a canned video on my player so I want to see if I can reproduce the file with the right encoders.

On another note, there is a software encoder tool with the CD for the device; however, my CD will only work in Windows, and I do not have a copy of Windows...

this is going to work great...thanks mate...cheers!!!

---

