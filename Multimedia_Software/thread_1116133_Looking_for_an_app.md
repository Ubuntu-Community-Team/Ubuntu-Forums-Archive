---
title: "Looking for an app"
date: 2009-04-04
forum: Multimedia Software
---

### Post by dtommy79 on 2009-04-04
Hi,

I'm looking for a programme that can tell a movie's audio-video information.

Thanks

---

### Post by xc3RnbFO8P on 2009-04-04
Avidemux does it: Open movie> File> Properties

---

### Post by dtommy79 on 2009-04-04
Thank you

---

### Post by oldos2er on 2009-04-04
Vlc

---

### Post by FakeOutdoorsman on 2009-04-04
FFmpeg:
```
$ ffmpeg -i glockenspiel.avi 
Input #0, avi, from 'glockenspiel.avi':
  Duration: 00:00:35.66, start: 0.000000, bitrate: 30314 kb/s
    Stream #0.0: Video: dvvideo, yuv411p, 720x480, 29.97 tbr, 29.97 tbn, 29.97 tbc
    Stream #0.1: Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s
```
[mediainfo](http://mediainfo.sourceforge.net/):
```
$ mediainfo ungulate.avi 
General
Complete name                    : ungulate.avi
Format                           : AVI
Format/Info                      : Audio Video Interleave
File size                        : 129 MiB
Duration                         : 35s 669ms
Overall bit rate                 : 30.3 Mbps

Video
Format                           : Digital Video
Codec ID                         : dvsd
Codec ID/Hint                    : Sony
Duration                         : 35s 669ms
Bit rate                         : 28.8 Mbps
Width                            : 720 pixels
Height                           : 480 pixels
Display aspect ratio             : 4/3
Frame rate mode                  : Constant
Frame rate                       : 29.970 fps
Standard                         : NTSC
Resolution                       : 24 bits
Colorimetry                      : 4:1:1
Scan type                        : Interlaced
Bits/(Pixel*Frame)               : 2.778
Stream size                      : 122 MiB (95%)

Audio
Format                           : PCM
Format settings, Endianness      : Little
Format settings, Sign            : Unsigned
Codec ID                         : 1
Codec ID/Hint                    : Microsoft
Duration                         : 35s 669ms
Bit rate mode                    : Constant
Bit rate                         : 1 536 Kbps
Channel(s)                       : 2 channels
Sampling rate                    : 48.0 KHz
Resolution                       : 16 bits
Stream size                      : 6.53 MiB (5%)
Interleave, duration             : 939 ms (28.13 video frames)
Interleave, preload duration     : 967 ms

```

---

