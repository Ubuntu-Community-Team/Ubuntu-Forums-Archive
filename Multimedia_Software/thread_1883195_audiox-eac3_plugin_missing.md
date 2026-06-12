---
title: "audio/x-eac3 plugin missing"
date: 2011-11-18
forum: Multimedia Software
---

### Post by calande on 2011-11-18
Hello,

I'm trying to watch a HD video, and VLC reports that there's a plugin missing:

> No packages with the requested plugins found
The requested plugins are:
audio/x-eac3 decoder

I already have gstreamer-ffmpeg installed. Here's more info on the file:

> General
Unique ID                                : 87653121747361540041363701703468199902 (0x41F1608F791FA15440A5D86860F12FDE)
Complete name                            : /home/charles/diskstation/public/Videos/Twilight 1 - Fascination.mkv
Format                                   : Matroska
Format version                           : Version 2
File size                                : 5.51 GiB
Duration                                 : 1h 59mn
Overall bit rate                         : 6 590 Kbps
Writing application                      : Lavf52.64.2
Writing library                          : Lavf52.64.2

Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : High@L4.0
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 4 frames
Codec ID                                 : V_MPEG4/ISO/AVC
Duration                                 : 1h 59mn
Bit rate                                 : 6 203 Kbps
Width                                    : 1 920 pixels
Height                                   : 1 080 pixels
Display aspect ratio                     : 16:9
Frame rate                               : 25.000 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : MBAFF
Bits/(Pixel*Frame)                       : 0.120
Stream size                              : 5.18 GiB (94%)
Language                                 : English
Color primaries                          : BT.709-5, BT.1361, IEC 61966-2-4, SMPTE RP177
Transfer characteristics                 : BT.709-5, BT.1361
Matrix coefficients                      : BT.709-5, BT.1361, IEC 61966-2-4 709, SMPTE RP177

Audio
ID                                       : 2
Format                                   : E-AC-3
Format/Info                              : Audio Coding 3
Codec ID                                 : A_EAC3
Duration                                 : 1h 59mn
Bit rate mode                            : Constant
Bit rate                                 : 256 Kbps
Channel(s)                               : 6 channels
Channel positions                        : Front: L C R, Side: L R, LFE
Sampling rate                            : 48.0 KHz
Compression mode                         : Lossy
Stream size                              : 219 MiB (4%)
Language                                 : English

VLC on Win7 can read this file. What do you think I should install?
Thanks!

---

### Post by calande on 2011-11-19
What do you think?

---

### Post by BicyclerBoy on 2011-11-19
VLC does not use gstreamer plugins (afaik).

Your windows VLC is likely very up-to-date & your ubuntu version is older & does not have the recent ffmpeg HDA decoder support.

Find an up-to-date VLC ppa for your distro..

VLC requires lots of CPU unless you can use VAAPI..but your video h/w is never going to..

You can/could find PCI cards with nvidia 8400 (vdpau) but this could just be money wasted.
The GT430 PCI-express is the recommended minimum..

---

### Post by mc4man on 2011-11-19
What version of vlc are you using, no issue here when trying on some various eac3 sample files

Maybe go here & see if you can playback a couple, I tried 2, names shown in screens,1st seemed similar to yours, screens from vlc's tools > Codecs information  box while playing or in the case of 1st. one paused, sample is quite short

[http://samples.mplayerhq.hu/A-codecs/AC3/eac3/](http://samples.mplayerhq.hu/A-codecs/AC3/eac3/)

(note - vlc does not use any gstreamer plugin

Edit: vlc -vv shows audio decoding thru avcodec (libavcodecXX in a ubuntu repo vlc

> avcodec decoder debug: ffmpeg codec (A/52 B Audio (aka E-AC3)) started

---

### Post by calande on 2011-11-20
Thanks, it's working fine now :)

---

