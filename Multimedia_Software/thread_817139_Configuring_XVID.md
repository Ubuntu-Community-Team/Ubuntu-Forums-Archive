---
title: "Configuring XVID"
date: 2008-06-03
forum: Multimedia Software
---

### Post by maltman on 2008-06-03
Currently I'm just using xvid4conf to configure my xvid settings. However, the Windows version of the xvid configuration appears to have additional settings that I can't seem to find.
For example, if you look here, [http://ryan.com.br/virtualdub_en.htm#xvid]("http://ryan.com.br/virtualdub_en.htm#xvid") there's a "Profile @ Level" setting that I can't find in Linux.

Specifically what I'm looking to do is set the Profile to L5.1 and to disable Packet Bitstream.
Any suggestions?

---

### Post by maltman on 2008-06-03
Just as an example, here's the mediainfo results of one of my movies with an audio sync issue.

```
General
Complete name                    : Gross_Anatomy-001.avi
Format                           : AVI
Format/Info                      : Audio Video Interleave
File size                        : 1.73 GiB
Duration                         : 1h 46mn
Overal bit rate                  : 2318 Kbps
Writing application              : transcode-1.0.2

Video
Format                           : MPEG-4 Visual
Format profile                   : Streaming Video@L1
Format settings, BVOP            : Yes
Format settings, QPel            : No
Format settings, GMC             : No warpoints
Format settings, Matrix          : Default
Muxing mode                      : Packet Bitstream
Codec ID                         : XVID
Codec ID/Hint                    : XviD
Duration                         : 1h 46mn
Bit rate                         : 2117 Kbps
Width                            : 720 pixels
Height                           : 400 pixels
Display aspect ratio             : 16/9
Frame rate                       : 23.976 fps
Resolution                       : 8 bits
Colorimetry                      : 4:2:0
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.307
Stream size                      : 1.58 GiB
Writing library                  : XviD 1.1.2 (UTC 2006-11-01)

Audio
Format                           : AC-3
Format/Info                      : Audio Coding 3
Format profile                   : Dolby Digital
Codec ID                         : 2000
Duration                         : 1h 46mn
Bit rate mode                    : Constant
Bit rate                         : 192 Kbps
Channel(s)                       : 2 channels
Channel positions                : L R
Sampling rate                    : 48.0 KHz
Resolution                       : 16 bits
Stream size                      : 147 MiB
```

And I was told the following two lines from above are an issue:
Format profile                   : Streaming Video@L1
Muxing mode                      : Packet Bitstream

but I can't find where to change them at...

---

