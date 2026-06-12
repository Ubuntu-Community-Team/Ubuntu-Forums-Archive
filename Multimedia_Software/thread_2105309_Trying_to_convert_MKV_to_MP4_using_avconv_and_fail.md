---
title: "Trying to convert MKV to MP4 using avconv and failing"
date: 2013-01-15
forum: Multimedia Software
---

### Post by fatgeek on 2013-01-15
Hello,

I am trying to convert an MKV file to MP4 to play on my PS3. I am not trying to reencode anything, just remux into a different container. I am using:

```
avconv -i file.mkv -c copy file.mp4
```

When I run it it fails with the following error:

```

Stream mapping:
  Stream #0:0 -> #0:0 (copy)
  Stream #0:1 -> #0:1 (copy)
Press ctrl-c to stop encoding
[mp4 @ 0x8ed2c00] pts < dts in stream 0
av_interleaved_write_frame(): Invalid argument

```

Any idea what I'm doing wrong?

mediainfo output follows:
```
Unique ID                                : 215387143595240598917624007979072309217 (0xA20A0E111CB60CD4A34D926DF49147E1)
Complete name                            : file.mkv
Format                                   : Matroska
Format version                           : Version 2
File size                                : 1.37 GiB
Duration                                 : 43mn 21s
Overall bit rate                         : 4 513 Kbps
Encoded date                             : UTC 2013-01-14 18:57:07
Writing application                      : mkvmerge v5.8.0 ('No Sleep / Pillow') built on Sep  2 2012 15:37:04
Writing library                          : libebml v1.2.3 + libmatroska v1.3.0

Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : High@L3.1
Format settings, CABAC                   : No
Format settings, ReFrames                : 2 frames
Codec ID                                 : V_MPEG4/ISO/AVC
Duration                                 : 43mn 21s
Bit rate                                 : 4 039 Kbps
Width                                    : 1 280 pixels
Height                                   : 720 pixels
Display aspect ratio                     : 16:9
Frame rate                               : 23.976 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.183
Stream size                              : 1.22 GiB (90%)
Title                                    : file
Language                                 : English
Default                                  : Yes
Forced                                   : No
Color primaries                          : BT.709-5, BT.1361, IEC 61966-2-4, SMPTE RP177
Transfer characteristics                 : BT.709-5, BT.1361
Matrix coefficients                      : BT.709-5, BT.1361, IEC 61966-2-4 709, SMPTE RP177

Audio
ID                                       : 2
Format                                   : AC-3
Format/Info                              : Audio Coding 3
Mode extension                           : CM (complete main)
Codec ID                                 : A_AC3
Duration                                 : 43mn 21s
Bit rate mode                            : Constant
Bit rate                                 : 384 Kbps
Channel(s)                               : 6 channels
Channel positions                        : Front: L C R, Side: L R, LFE
Sampling rate                            : 48.0 KHz
Bit depth                                : 16 bits
Compression mode                         : Lossy
Stream size                              : 119 MiB (9%)
Title                                    : Dolby Digital 5.1 @ 384 kbps
Language                                 : English
Default                                  : Yes
Forced                                   : No


```

---

### Post by fatgeek on 2013-01-17
After much trial and error I got it working using:

```
avconv -i file.mkv -c:v copy -c:a copy file.mp4
```

---

### Post by raja.genupula on 2013-01-17
Thats really good news brother , Now please mark your thread as solved from thread tools.

Thank you.

---

