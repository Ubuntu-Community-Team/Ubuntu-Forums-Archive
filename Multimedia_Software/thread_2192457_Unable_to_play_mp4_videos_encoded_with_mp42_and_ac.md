---
title: "Unable to play mp4 videos encoded with mp42 and acv1 codecs"
date: 2013-12-07
forum: Multimedia Software
---

### Post by MikeB23930 on 2013-12-07
Until recently I had no problem playing mp4's.  In the past few days I have run into several that play for a short time, become jerky, start breaking up and finally die.  What little I've been able to find out indicates that this problem may be related to a quicktime codec.  I've installed every codec and plugin I could find in the 13.10 repositories all to no avail. Any help would be greatly appreciated.

EDIT:  After doing a bit more comparison of problem files it appears that the common thread is the video codec avc1,  How do I get a codec to decode mp4's coded with the avc1 codec?

Here is the result of running mediainfo against a typical problem file:

--------------------------------------------------------------------------------------------------------------------------------------
General
Complete name                            : Video.mp4
Format                                        : MPEG-4
Format profile                              : Base Media / Version 2
Codec ID                                     : mp42
File size                                      : 521 MiB
Duration                                     : 24mn 12s
Overall bit rate                            : 3 008 Kbps
Encoded date                               : UTC 2012-02-17 17:44:34
Tagged date                                : UTC 2012-02-17 17:46:53

Video
ID                                            : 2
Format                                     : AVC
Format/Info                               : Advanced Video Codec
Format profile                            : Main@L4.0
Format settings, CABAC                : No
Format settings, ReFrames            : 2 frames
Codec ID                                   : avc1
Codec ID/Info                            : Advanced Video Coding
Duration                                   : 24mn 12s
Bit rate                                    : 2 895 Kbps
Width                                      : 1 888 pixels
Original width                           : 1 920 pixels
Height                                     : 1 062 pixels
Original height                          : 1 080 pixels
Display aspect ratio                   : 16:9
Frame rate mode                      : Constant
Frame rate                               : 23.976 fps
Color space                              : YUV
Chroma subsampling                  : 4:2:0
Bit depth                                  : 8 bits
Scan type                                 : Progressive
Bits/(Pixel*Frame)                     : 0.060
Stream size                              : 501 MiB (96%)
Language                                 : English
Encoded date                            : UTC 2012-02-17 17:44:33
Tagged date                              : UTC 2012-02-17 17:46:53
Color primaries                         : BT.709
Transfer characteristics               : BT.709
Matrix coefficients                      : BT.709

Audio
ID                                            : 1
Format                                     : AAC
Format/Info                               : Advanced Audio Codec
Format profile                            : LC
Codec ID                                   : 40
Duration                                    : 24mn 12s
Source duration                          : 24mn 12s
Bit rate mode                             : Constant
Bit rate                                     : 108 Kbps
Nominal bit rate                         : 128 Kbps
Channel count                            : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 44.1 KHz
Compression mode                     : Lossy
Delay relative to video                : 42ms
Stream size                               : 18.6 MiB (4%)
Source stream size                     : 18.6 MiB (4%)
Language                                  : English
Encoded date                             : UTC 2012-02-17 17:42:55
Tagged date                               : UTC 2012-02-17 17:46:53

--------------------------------------------------------------------------------------------------------------------------------------

Thanks,

Mike

---

