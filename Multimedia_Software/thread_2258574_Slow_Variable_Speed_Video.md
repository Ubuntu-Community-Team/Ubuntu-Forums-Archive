---
title: "Slow Variable Speed Video"
date: 2014-12-28
forum: Multimedia Software
---

### Post by mcman56 on 2014-12-28
When playing a GoPro video (MP4), the video speed is not constant and sound works only for a few seconds when starting the video.  The video sort of lags and then maybe runs at actual speed for a few seconds before lagging again.  This happens in Videos and Openshot Video Editor when running directly from the camera or from the hard drive.  The camera recorded at its maximum resolution of 1080p.  I don't have problems running YouTube videos online.

The video works fine in Quicktime on a Vista PC with a 2.5GHz processor.  (6gb memory, 64 bit).  The specs for the Ubuntu machine show an AMD Dual Core Processor E1-1200 with a speed of 1.4 GHz.  Could this processor just be too slow or is there rsomethign else I could do to correct?

---

### Post by CantankRus on 2014-12-28
Try playing the video in VLC.
May need to install.

---

### Post by Rob Sayer on 2014-12-29
Need more info ... the bitrate from those HD cameras can be very high so the hardware may indeed be too slow.  But it's hard to say.

Install mediainfo-gui, open one of the problem files with it, post the result here using mediainfo text mode.  I suspect it's uncompressed h.264.  And a very large file for the length of the video.

---

### Post by mcman56 on 2014-12-29
VLC is much worse.  

I ran mediainfo-gui but don't understand how to do a text mode.  A screen print is attached.  I used a terminal version to get what is below.  The GoPro setup can be changed.  Would I have to decrease resolution much to make it work?  Or could the video be processed or converted to another format that would work?  (I really don't know how compression vs non compression affects playing.)  Or could this be a screen driver issue?

Thanks for looking at this. 

General
Complete name                            : file:///home/dan/Videos/G0030049.MP4
Format                                   : MPEG-4
Format profile                           : JVT
Codec ID                                 : avc1
File size                                : 942 MiB
Duration                                 : 8mn 42s
Overall bit rate                         : 15.1 Mbps
Encoded date                             : UTC 2014-12-18 15:40:07
Tagged date                              : UTC 2014-12-18 15:40:07
AMBA                                     : 

Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : Main@L4.2
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 1 frame
Format settings, GOP                     : M=1, N=8
Codec ID                                 : avc1
Codec ID/Info                            : Advanced Video Coding
Duration                                 : 8mn 42s
Bit rate mode                            : Constant
Bit rate                                 : 15.0 Mbps
Width                                    : 1 280 pixels
Height                                   : 960 pixels
Display aspect ratio                     : 4:3
Frame rate mode                          : Constant
Frame rate                               : 59.940 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.204
Stream size                              : 933 MiB (99%)
Title                                    : GoPro AVC
Language                                 : English
Encoded date                             : UTC 2014-12-18 15:40:07
Tagged date                              : UTC 2014-12-18 15:40:07
Color primaries                          : BT.709
Transfer characteristics                 : BT.709
Matrix coefficients                      : BT.709

Audio
ID                                       : 2
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : LC
Codec ID                                 : 40
Duration                                 : 8mn 42s
Bit rate mode                            : Constant
Bit rate                                 : 128 Kbps
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 48.0 KHz
Compression mode                         : Lossy
Stream size                              : 7.97 MiB (1%)
Title                                    : GoPro AAC
Language                                 : English
Encoded date                             : UTC 2014-12-18 15:40:07
Tagged date                              : UTC 2014-12-18 15:40:07

Other
ID                                       : 3
Type                                     : Time code
Format                                   : QuickTime TC
Duration                                 : 8mn 42s
Time code of first frame                 : 15:39:10:38
Time code settings                       : Striped
Language                                 : English
Encoded date                             : UTC 2014-12-18 15:40:07
Tagged date                              : UTC 2014-12-18 15:40:07

---

### Post by Rob Sayer on 2014-12-30
I don't see anything unusual about the format of the video.  But the video bitrate is 15.0 Mbps.  That's very high, and openshot is a large program.

What's the video card?  Need more specs.

---

### Post by mcman56 on 2014-12-30
The specs show AMD Radeon HD 7310.

"Videos" shows a slightly uneven speed also.  VLC was massively choppy/ blocky.  I tried different video drivers but don't see a difference.

---

