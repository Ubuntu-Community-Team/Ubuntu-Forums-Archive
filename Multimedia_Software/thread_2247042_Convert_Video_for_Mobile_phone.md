---
title: "Convert Video for Mobile phone"
date: 2014-10-05
forum: Multimedia Software
---

### Post by linuxyogi on 2014-10-05
Hi,

My phone is an entry level [touch screen phone]("http://www.gsmarena.com/nokia_asha_501-5445.php"). Its video playback capability is quite limited.

I have downloaded this video from the web and my phone can play this video just fine.

So I am looking for a way to batch convert some videos with these particular settings.

I tried avidemux but problem is when I select the video codec as MPEG-4 AVC then 

go to *Configure *I can't find a way to change the bitrate.

If I get a command which works I will simply back it up to cloud so as long as 

this phone lasts this problem won't arise again.

This is the sample video

```
$ mediainfo viideo.mp4 
General
Complete name                            : viideo.mp4
Format                                   : MPEG-4
Format profile                           : Base Media
Codec ID                                 : isom
File size                                : 27.9 MiB
Duration                                 : 6mn 38s
Overall bit rate mode                    : Variable
Overall bit rate                         : 587 Kbps
Writing application                      : Lavf53.5.0

Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : Baseline@L3.1
Format settings, CABAC                   : No
Format settings, ReFrames                : 2 frames
Codec ID                                 : avc1
Codec ID/Info                            : Advanced Video Coding
Duration                                 : 6mn 38s
Bit rate                                 : 512 Kbps
Width                                    : 320 pixels
Height                                   : 240 pixels
Display aspect ratio                     : 4:3
Frame rate mode                          : Constant
Frame rate                               : 25.000 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.267
Stream size                              : 24.3 MiB (87%)
Writing library                          : x264 core 125
Encoding settings                        : cabac=0 / ref=2 / deblock=1:0:0 / analyse=0x1:0x111 / me=hex / subme=6 / psy=1 / psy_rd=1.00:0.00 / mixed_ref=0 / me_range=16 / chroma_me=1 / trellis=0 / 8x8dct=0 / cqm=0 / deadzone=21,11 / fast_pskip=1 / chroma_qp_offset=-2 / threads=1 / lookahead_threads=1 / sliced_threads=0 / nr=0 / decimate=1 / interlaced=0 / bluray_compat=0 / constrained_intra=0 / bframes=0 / weightp=0 / keyint=250 / keyint_min=25 / scenecut=40 / intra_refresh=0 / rc_lookahead=40 / rc=2pass / mbtree=1 / bitrate=512 / ratetol=1.0 / qcomp=0.50 / qpmin=10 / qpmax=51 / qpstep=4 / cplxblur=20.0 / qblur=0.5 / ip_ratio=1.41 / aq=1:1.00
Language                                 : English
Tagged date                              : UTC 2014-09-24 03:30:54

Audio
ID                                       : 2
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : LC
Codec ID                                 : 40
Duration                                 : 6mn 38s
Bit rate mode                            : Variable
Bit rate                                 : 141 Mbps
Nominal bit rate                         : 38.3 Kbps
Maximum bit rate                         : 56.0 Kbps
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 44.1 KHz
Compression mode                         : Lossy
Stream size                              : 6.52 GiB
Language                                 : English
Tagged date                              : UTC 2014-09-24 03:30:54

Other #1
ID                                       : 65536
Type                                     : Hint
Format                                   : RTP
Codec ID                                 : rtp 
Duration                                 : 6mn 38s
Encoded date                             : UTC 2014-09-24 03:30:54
Tagged date                              : UTC 2014-09-24 03:30:54

Other #2
ID                                       : 65537
Type                                     : Hint
Format                                   : RTP
Codec ID                                 : rtp 
Duration                                 : 6mn 37s
Encoded date                             : UTC 2014-09-24 03:30:54
Tagged date                              : UTC 2014-09-24 03:30:54
Bit rate mode                            : VBR


```

---

### Post by David D. on 2014-10-05
I use Transmageddon Video Transcoder to convert video files.  It converts to a number of formats, including the MP4 that you want.  This program is available in Ubuntu Software Center.

---

### Post by linuxyogi on 2014-10-05
> **David D. said:**
> I use Transmageddon Video Transcoder to convert video files.  It converts to a number of formats, including the MP4 that you want.  This program is available in Ubuntu Software Center.

Before selecting each preset I Google about the specs of that model to get an idea about the 

resolution of the output. Leaving the Motorola preset all of the ones that I have tried exceeds 

my phone's screen resolution but still when I play the videos on my phone I see a lot of noise.

mediainfo prints the resolution is low. I wonder why they did that. My source videos are all 720p. 

I have tried these presents

[ATTACH=CONFIG]256956[/ATTACH]

Result of N900

```
$ mediainfo N900.mp4 
General
Complete name                            : N900.mp4
Format                                   : MPEG-4
Format profile                           : Base Media / Version 2
Codec ID                                 : mp42
File size                                : 75.0 MiB
Duration                                 : 5mn 8s
Overall bit rate mode                    : Variable
Overall bit rate                         : 2 036 Kbps
Encoded date                             : UTC 2014-10-05 15:41:00
Tagged date                              : UTC 2014-10-05 15:41:00
Writing application                      : x264
gsst                                     : 0
gstd                                     : 309056
gssd                                     : BADC234E5HH1406150300061270
gshh                                     : r18---sn-cvh7zn7r.googlevideo.com

Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : Baseline@L2.1
Format settings, CABAC                   : No
Format settings, ReFrames                : 3 frames
Codec ID                                 : avc1
Codec ID/Info                            : Advanced Video Coding
Duration                                 : 5mn 8s
Bit rate                                 : 1 904 Kbps
Nominal bit rate                         : 2 048 Kbps
Maximum bit rate                         : 5 638 Kbps
[B][COLOR=#ff0000]Width                                    : 176 pixels
Height                                   : 144 pixels[/COLOR][/B]
Display aspect ratio                     : 16:9
Frame rate mode                          : Constant
Frame rate                               : 25.000 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 3.005
Stream size                              : 70.1 MiB (93%)
Writing library                          : x264 core 142 r2431 a5831aa
Encoding settings                        : cabac=0 / ref=3 / deblock=1:0:0 / analyse=0x1:0x111 / me=hex / subme=7 / psy=1 / psy_rd=1.00:0.00 / mixed_ref=1 / me_range=16 / chroma_me=1 / trellis=1 / 8x8dct=0 / cqm=0 / deadzone=21,11 / fast_pskip=1 / chroma_qp_offset=-2 / threads=3 / lookahead_threads=1 / sliced_threads=0 / nr=0 / decimate=1 / interlaced=0 / bluray_compat=0 / constrained_intra=0 / bframes=0 / weightp=0 / keyint=250 / keyint_min=25 / scenecut=40 / intra_refresh=0 / rc_lookahead=40 / rc=cbr / mbtree=1 / bitrate=2048 / ratetol=1.0 / qcomp=0.60 / qpmin=0 / qpmax=69 / qpstep=4 / vbv_maxrate=2048 / vbv_bufsize=1228 / nal_hrd=none / filler=0 / ip_ratio=1.40 / aq=1:1.00
Language                                 : English
Encoded date                             : UTC 2014-10-05 15:41:00
Tagged date                              : UTC 2014-10-05 15:41:00

Audio
ID                                       : 2
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : LC
Codec ID                                 : 40
Duration                                 : 5mn 8s
Bit rate mode                            : Variable
Bit rate                                 : 128 Kbps
Maximum bit rate                         : 246 Kbps
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 48.0 KHz
Compression mode                         : Lossy
Stream size                              : 4.71 MiB (6%)
Language                                 : English
Encoded date                             : UTC 2014-10-05 15:41:00
Tagged date                              : UTC 2014-10-05 15:41:00


```

---

### Post by linuxyogi on 2014-10-06
Encoded a file with handbrake and it worked.

```
$ mediainfo handbrake.mp4 
General
Complete name                            : handbrake.mp4
Format                                   : MPEG-4
Format profile                           : Base Media / Version 2
Codec ID                                 : mp42
File size                                : 23.2 MiB
Duration                                 : 5mn 1s
Overall bit rate mode                    : Variable
Overall bit rate                         : 646 Kbps
Movie name                               : [Hon3y] Ek Villain---Galliyan
Encoded date                             : UTC 2014-10-06 09:27:03
Tagged date                              : UTC 2014-10-06 09:30:34
Writing application                      : HandBrake rev5474 2014072799

Video
ID                                       : 1
Format                                   : MPEG-4 Visual
Format profile                           : Simple@L1
Format settings, BVOP                    : No
Format settings, QPel                    : No
Format settings, GMC                     : No warppoints
Format settings, Matrix                  : Default (H.263)
Codec ID                                 : 20
Duration                                 : 5mn 1s
Source duration                          : 5mn 1s
Bit rate mode                            : Variable
Bit rate                                 : 518 Kbps
Maximum bit rate                         : 2 519 Kbps
Width                                    : 564 pixels
Height                                   : 240 pixels
Display aspect ratio                     : 2.35:1
Frame rate mode                          : Constant
Frame rate                               : 25.000 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Compression mode                         : Lossy
Bits/(Pixel*Frame)                       : 0.153
Stream size                              : 18.6 MiB (80%)
Source stream size                       : 18.6 MiB (80%)
Writing library                          : Lavc54.35.0
Encoded date                             : UTC 2014-10-06 09:27:03
Tagged date                              : UTC 2014-10-06 09:30:34
Color primaries                          : BT.709
Transfer characteristics                 : BT.709
Matrix coefficients                      : BT.709

Audio
ID                                       : 2
Format                                   : MPEG Audio
Format version                           : Version 1
Format profile                           : Layer 3
Codec ID                                 : 69
Duration                                 : 5mn 1s
Source duration                          : 5mn 1s
Bit rate mode                            : Variable
Bit rate                                 : 125 Kbps
Maximum bit rate                         : 153 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 48.0 KHz
Compression mode                         : Lossy
Stream size                              : 4.50 MiB (19%)
Source stream size                       : 4.50 MiB (19%)
Language                                 : Hindi
Encoded date                             : UTC 2014-10-06 09:27:03
Tagged date                              : UTC 2014-10-06 09:30:34


```

---

