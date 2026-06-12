---
title: "Audacity won't open .mp4 files"
date: 2017-02-22
forum: Multimedia Software
---

### Post by geomcd1949 on 2017-02-22
I used to be able to drag an .mp4 file or an .mkv file or a .webm file into Audacity and it would open the audio of the file. Now it doesn't do that anymore (V 2.1.3). It ells me it's an AAC file, and that it can't open it. I've used the Edit > Preferences > Libraries to Locate the ffmpeg library, but that doesn't help. Any suggestions? Thanks.

---

### Post by ajgreeny on 2017-02-22
Perhaps you are missing the needed aac decoder packages.

---

### Post by #&amp;thj^% on 2017-02-22
No problems here with any of the above formats.
1st question is always obvious to an Older user...and just checking politely here in this case...do you have the necessary codec's installed?
IE: ffmpeg and the plugins.
In a terminal do:
```
mediainfo  /path/to/your/file.mp4
```
You may need to install mediainfo for this.
```
sudo apt install mediainfo
```

and copy/paste the complete output into your next post within [ code]...[ /code] tags.

Just an example of my current playing Audio from a .mp4
```
Scooby Doo.mp4' 
General
Complete name                            : /media/me/My Book/Storage/1.Videos/2.Oldies/Scooby Doo.mp4
Format                                   : MPEG-4
Format profile                           : Base Media / Version 2
Codec ID                                 : mp42 (mp42/isom/avc1)
File size                                : 700 MiB
Duration                                 : 1h 26mn
Overall bit rate mode                    : Variable
Overall bit rate                         : 1 130 Kbps
Encoded date                             : UTC 2011-09-08 02:36:09
Tagged date                              : UTC 2011-09-08 03:25:52
Writing application                      : HandBrake 0.9.4 2009112300

Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : Main@L3
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 2 frames
Codec ID                                 : avc1
Codec ID/Info                            : Advanced Video Coding
Duration                                 : 1h 26mn
Bit rate                                 : 965 Kbps
Width                                    : 720 pixels
Height                                   : 400 pixels
Display aspect ratio                     : 16:9
Frame rate mode                          : Variable
Frame rate                               : 23.976 fps
Minimum frame rate                       : 13.320 fps
Maximum frame rate                       : 200.893 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.140
Stream size                              : 597 MiB (85%)
Writing library                          : x264 core 79
Encoding settings                        : cabac=1 / ref=2 / deblock=1:0:0 / analyse=0x1:0x111 / me=hex / subme=6 / psy=1 / psy_rd=1.0:0.0 / mixed_ref=0 / me_range=16 / chroma_me=1 / trellis=0 / 8x8dct=0 / cqm=0 / deadzone=21,11 / chroma_qp_offset=-2 / threads=3 / nr=0 / decimate=1 / mbaff=0 / constrained_intra=0 / bframes=2 / b_pyramid=0 / b_adapt=1 / b_bias=0 / direct=1 / wpredb=0 / wpredp=2 / keyint=240 / keyint_min=24 / scenecut=40 / rc_lookahead=40 / rc=2pass / mbtree=1 / bitrate=965 / ratetol=1.0 / qcomp=0.60 / qpmin=10 / qpmax=51 / qpstep=4 / cplxblur=20.0 / qblur=0.5 / ip_ratio=1.40 / aq=1:1.00
Encoded date                             : UTC 2011-09-08 02:36:09
Tagged date                              : UTC 2011-09-08 03:25:52
Color range                              : Limited
Color primaries                          : BT.601 NTSC
Transfer characteristics                 : BT.709
Matrix coefficients                      : BT.601
Menus                                    : 3

Audio
ID                                       : 2
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : LC
Codec ID                                 : 40
Duration                                 : 1h 26mn
Bit rate mode                            : Variable
Bit rate                                 : 160 Kbps
Maximum bit rate                         : 206 Kbps
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 48.0 KHz
Frame rate                               : 46.875 fps (1024 spf)
Compression mode                         : Lossy
Stream size                              : 98.9 MiB (14%)
Title                                    : Stereo
Language                                 : English
Encoded date                             : UTC 2011-09-08 02:36:09
Tagged date                              : UTC 2011-09-08 03:25:52

Menu
ID                                       : 3
Codec ID                                 : text
Duration                                 : 1h 26mn
Encoded date                             : UTC 2011-09-08 02:36:09
Tagged date                              : UTC 2011-09-08 03:25:52
Menu For                                 : 1
00:00:00.000                             : Chapter 1
00:07:36.572                             : Chapter 2
00:14:55.895                             : Chapter 3
00:24:39.311                             : Chapter 4
00:31:29.387                             : Chapter 5
00:37:25.576                             : Chapter 6
00:45:33.397                             : Chapter 7
00:52:42.247                             : Chapter 8
00:58:32.096                             : Chapter 9
01:04:17.825                             : Chapter 10
01:10:54.672                             : Chapter 11
01:15:15.649                             : Chapter 12
01:19:11.718                             : Chapter 13
Bit rate mode                            : VBR


```
Ninja'ed by ajgreeny:)

---

### Post by Yellow Pasque on 2017-02-24
Check ffmpeg (or avconv for older Ubuntu versons): 
```
ffmpeg -codecs | grep -i aac
```

---

