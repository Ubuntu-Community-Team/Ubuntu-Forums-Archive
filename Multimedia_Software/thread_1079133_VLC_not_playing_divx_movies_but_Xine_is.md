---
title: "VLC not playing divx movies but Xine is"
date: 2009-02-24
forum: Multimedia Software
---

### Post by vishnu on 2009-02-24
I have VLC 0.9.4 installed.  I can play AVI files perfectly well in Xin and movie player but VLC doesn't play them.  No error message.  Simply flashes the name very quickly in the info bar at the bottom of the player then does nothing as if no file is loaded.  Below is the info of an example video I've tried.
Both Movie Player and Xine have no problem with these files.

General

Format                           : AVI

Format/Info                      : Audio Video Interleave

File size                        : 698 MiB

Duration                         : 1h 28mn

Overall bit rate                 : 1 098 Kbps

Writing application              : VirtualDubMod 1.5.10.2 (build 2540/release)

Writing library                  : VirtualDubMod build 2540/release



Video

Format                           : MPEG-4 Visual

Format profile                   : Streaming Video@L1

Format settings, BVOP            : Yes

Format settings, QPel            : No

Format settings, GMC             : No warppoints

Format settings, Matrix          : Default

Muxing mode                      : Packed bitstream

Codec ID                         : XVID

Codec ID/Hint                    : XviD

Duration                         : 1h 28mn

Bit rate                         : 961 Kbps

Width                            : 640 pixels

Height                           : 352 pixels

Display aspect ratio             : 16/9

Frame rate                       : 25.000 fps

Resolution                       : 24 bits

Colorimetry                      : 4:2:0

Scan type                        : Progressive

Bits/(Pixel*Frame)               : 0.171

Stream size                      : 610 MiB (87%)

Writing library                  : XviD 1.1.2 (UTC 2006-11-01)



Audio

Format                           : MPEG Audio

Format version                   : Version 1

Format profile                   : Layer 3

Codec ID                         : 55

Codec ID/Hint                    : MP3

Duration                         : 1h 28mn

Bit rate mode                    : Constant

Bit rate                         : 128 Kbps

Channel(s)                       : 2 channels

Sampling rate                    : 48.0 KHz

Resolution                       : 16 bits

Stream size                      : 81.3 MiB (12%)

Alignment                        : Aligned on interleaves

Interleave, duration             : 40 ms (1.00 video frame)

Interleave, preload duration     : 504 ms

---

### Post by x33a on 2009-02-25
did you try some different video output module?

go to tools -> preferences -> video -> output modules.

---

### Post by vishnu on 2009-02-25
yeah.  it's set to default.  i tried x11 but no go.

---

