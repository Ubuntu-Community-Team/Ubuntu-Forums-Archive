---
title: "Colors &quot;shifted&quot; during mp4 playback"
date: 2013-01-20
forum: Mythbuntu
---

### Post by DouweD on 2013-01-20
Hey people,

I was wondering if anybody is familiar with the following situation:

When I want to play an mp4 file, its seems as if the RGB colors are shifted with respect to each other.  I have an other file which is mkv and it plays perfectly. I am using Mythtv 0.26 with the internal player and standard playback settings. 

I have been searching the internet for a solution and found references to a hue problem. Tried to adapt this but made no difference. 

Any help is appreciated, thanks!

EDIT: I found this one reference to the same problem in chromium: [http://code.google.com/p/chromium/issues/detail?id=96907](http://code.google.com/p/chromium/issues/detail?id=96907) no solution though...

---

### Post by nickrout on 2013-01-21
please post the full output of mediainfo for this file.

---

### Post by DouweD on 2013-01-21
Thanks! Here is the requested info (only left the name of the file out):

General
Complete name                     : #####
Format                                   : MPEG-4
Format profile                           : Base Media
Codec ID                                 : isom
File size                                : 152 MiB
Duration                                 : 21mn 18s
Overall bit rate mode                    : Variable
Overall bit rate                         : 995 Kbps
Encoded date                             : UTC 2012-12-13 18:38:51
Tagged date                              : UTC 2012-12-13 18:38:51

Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : High@L3.1
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 5 frames
Codec ID                                 : avc1
Codec ID/Info                            : Advanced Video Coding
Duration                                 : 21mn 18s
Bit rate                                 : 886 Kbps
Maximum bit rate                         : 8 572 Kbps
Width                                    : 720 pixels
Height                                   : 404 pixels
Display aspect ratio                     : 16:9
Frame rate mode                          : Constant
Frame rate                               : 23.976 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.127
Stream size                              : 135 MiB (89%)
Writing library                          : x264 core 129 r2230 1cffe9f
Encoding settings                        : cabac=1 / ref=5 / deblock=1:1:1 / analyse=0x3:0x133 / me=umh / subme=9 / psy=1 / psy_rd=1.00:0.00 / mixed_ref=1 / me_range=16 / chroma_me=1 / trellis=2 / 8x8dct=1 / cqm=0 / deadzone=21,11 / fast_pskip=1 / chroma_qp_offset=-2 / threads=18 / lookahead_threads=3 / sliced_threads=0 / nr=0 / decimate=1 / interlaced=0 / bluray_compat=0 / constrained_intra=0 / bframes=3 / b_pyramid=2 / b_adapt=2 / b_bias=0 / direct=3 / weightb=1 / open_gop=0 / weightp=2 / keyint=250 / keyint_min=23 / scenecut=40 / intra_refresh=0 / rc_lookahead=60 / rc=crf / mbtree=1 / crf=20.0 / qcomp=0.60 / qpmin=0 / qpmax=69 / qpstep=4 / ip_ratio=1.40 / aq=1:1.00
Encoded date                             : UTC 2012-12-13 17:01:17
Tagged date                              : UTC 2012-12-13 18:38:51
Matrix coefficients                      : BT.709

Audio
ID                                       : 2
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : LC
Codec ID                                 : 40
Duration                                 : 21mn 18s
Bit rate mode                            : Variable
Bit rate                                 : 105 Kbps
Maximum bit rate                         : 143 Kbps
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 48.0 KHz
Compression mode                         : Lossy
Delay relative to video                  : 83ms
Stream size                              : 16.0 MiB (11%)
Encoded date                             : UTC 2012-12-13 18:38:51
Tagged date                              : UTC 2012-12-13 18:38:51

---

### Post by DouweD on 2013-01-24
Im sorry for replying to my own message, but does anybody have an idea on what may be causing this strange problem?

EDIT: It turned out to be a driver problem... thanks for the help anyway!

---

