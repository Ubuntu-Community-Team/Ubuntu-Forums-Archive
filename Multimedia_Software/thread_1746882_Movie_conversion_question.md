---
title: "Movie conversion question"
date: 2011-05-02
forum: Multimedia Software
---

### Post by gofurygo on 2011-05-02
Hello

Im not sure if this is the appropriate category for this question but I'm sure someone out there knows how to fix this "issue".

Recently I bought a new mobile and I'm having a hard time converting videos for it. Appearantly it supports 3gp and mp4 movies. I downloaded a webvideo for testing and it plays fine. So I "duplicated" the web videos settings to convert a movie...but it still wont work on the mobile.

I looked into both files with MediaInfo... here is the output:

File that works fine:
```
General
Complete name                    : G:\Videos\www.rofl.to.mp4
Format                           : MPEG-4
Format profile                   : Base Media
Codec ID                         : isom
File size                        : 4.34 MiB
Duration                         : 3mn 0s
Overall bit rate                 : 202 Kbps
Writing application              : Lavf52.31.0

Video
ID                               : 1
Format                           : MPEG-4 Visual
Format profile                   : Simple@L1
Format settings, BVOP            : No
Format settings, QPel            : No
Format settings, GMC             : No warppoints
Format settings, Matrix          : Default (H.263)
Codec ID                         : 20
Duration                         : 3mn 0s
Bit rate mode                    : Variable
Bit rate                         : 158 Kbps
Width                            : 320 pixels
Height                           : 240 pixels
Display aspect ratio             : 4:3
Frame rate mode                  : Constant
Frame rate                       : 14.985 fps
Color space                      : YUV
Chroma subsampling               : 4:2:0
Bit depth                        : 8 bits
Scan type                        : Progressive
Compression mode                 : Lossy
Bits/(Pixel*Frame)               : 0.137
Stream size                      : 3.40 MiB (78%)
Writing library                  : Lavc52.20.0

Audio
ID                               : 2
Format                           : AAC
Format/Info                      : Advanced Audio Codec
Format profile                   : LC
Codec ID                         : 40
Duration                         : 2mn 59s
Bit rate mode                    : Variable
Bit rate                         : 41.4 Kbps
Channel(s)                       : 1 channel
Channel positions                : Front: C
Sampling rate                    : 24.0 KHz
Compression mode                 : Lossy
Stream size                      : 908 KiB (20%)
```The file that doesnt work is this one:
```
General
Complete name                    : G:\Videos\Balls.of.Fury.2007.mp4
Format                           : MPEG-4
Format profile                   : QuickTime
Codec ID                         : qt  
File size                        : 227 MiB
Duration                         : 1h 30mn
Overall bit rate                 : 351 Kbps
Encoded date                     : UTC 2011-04-28 11:58:48
Tagged date                      : UTC 2011-04-28 11:58:48

Video
ID                               : 2
Format                           : MPEG-4 Visual
Format profile                   : Simple@L3
Format settings, BVOP            : No
Format settings, QPel            : No
Format settings, GMC             : No warppoints
Format settings, Matrix          : Default (H.263)
Codec ID                         : 20
Duration                         : 1h 30mn
Bit rate mode                    : Variable
Bit rate                         : 217 Kbps
Nominal bit rate                 : 567 Kbps
Maximum bit rate                 : 3 785 Kbps
Width                            : 320 pixels
Height                           : 240 pixels
Display aspect ratio             : 4:3
Frame rate mode                  : Constant
Frame rate                       : 15.000 fps
Color space                      : YUV
Chroma subsampling               : 4:2:0
Bit depth                        : 8 bits
Scan type                        : Progressive
Compression mode                 : Lossy
Bits/(Pixel*Frame)               : 0.188
Stream size                      : 140 MiB (62%)
Writing library                  : XviD 1.2.1 (UTC 2008-12-04)
Language                         : English
Encoded date                     : UTC 2011-04-28 11:58:48
Tagged date                      : UTC 2011-04-28 11:58:48

Audio
ID                               : 1
Format                           : AAC
Format/Info                      : Advanced Audio Codec
Format profile                   : LC
Codec ID                         : 40
Duration                         : 1h 30mn
Bit rate mode                    : Variable
Bit rate                         : 132.3 Kbps
Nominal bit rate                 : 48.0 Kbps
Maximum bit rate                 : 55.3 Kbps
Channel(s)                       : 2 channels
Channel positions                : Front: L R
Sampling rate                    : 44.1 KHz
Compression mode                 : Lossy
Stream size                      : 84.6 MiB (37%)
Language                         : English
Encoded date                     : UTC 2011-04-28 11:58:48
Tagged date                      : UTC 2011-04-28 11:58:48
```The only significant difference I can see is, that the order of video/audio stream is reversed... 

Does anybody have an idea what I am doing wrong?

Thanks in advance ;-)

---

### Post by gofurygo on 2011-05-03
Bump...

Any "expert" around here regarding file conversion...? I should mention, the file that is not working was converted with Arista... I made a profile by myself to do it...but :(

Thanks ;-)

---

