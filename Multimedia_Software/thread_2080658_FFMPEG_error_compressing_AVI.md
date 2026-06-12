---
title: "FFMPEG error compressing AVI"
date: 2012-11-04
forum: Multimedia Software
---

### Post by dgharmon on 2012-11-04
Any suggestions would be greatly appreciated ...
-------

$ffmpeg -i input.avi -vcodec msmpeg4v2 output.avi
-------

Input #0, avi, from 'input.avi':

  Metadata:
    creation_time   : 2012-11-01 15:55:43
    encoder         : CanonMVI06

  Duration: 00:00:16.79, start: 0.000000, bitrate: 15625 kb/s

    Stream #0.0: Video: mjpeg, yuvj422p, 640x480, 30 tbr, 30 tbn, 30 tbc
    Stream #0.1: Audio: pcm_s16le, 44100 Hz, 1 channels, s16, 705 kb/s

Incompatible pixel format 'yuvj422p' for codec 'msmpeg4v2', auto-selecting format 'yuv420p'

[buffer @ 0x24e2b80] w:640 h:480 pixfmt:yuvj422p

[avsink @ 0x24f1200] auto-inserting filter 'auto-inserted scaler 0' between the filter 'src' and the filter 'out'
[scale @ 0x24ec940] w:640 h:480 fmt:yuvj422p -> w:640 h:480 fmt:yuv420p flags:0x4

Incompatible sample format 's16' for codec 'ac3', auto-selecting format 'flt'

[ac3 @ 0x24f0d60] channel_layout not specified
[ac3 @ 0x24f0d60] No channel layout specified. The encoder will guess the layout, but it might be incorrect.
[ac3 @ 0x24f0d60] invalid bit rate

Output #0, avi, to 'output.avi':
    Stream #0.0: Video: msmpeg4v2, yuv420p, 640x480, q=2-31, 200 kb/s, 90k tbn, 30 tbc
    Stream #0.1: Audio: ac3, 44100 Hz, mono, flt, 200 kb/s

Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1

Error while opening encoder for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height

---

### Post by FakeOutdoorsman on 2012-11-05
Please show the complete console output. You left out some stuff. Also place it in the [noparse][code][/noparse] tag for readability.

---

### Post by dgharmon on 2012-11-05
> **FakeOutdoorsman said:**
> Please show the complete console output. You left out some stuff. Also place it in the [noparse][code][/noparse] tag for readability.

This works .. infile.avi = 17M, outfile.mp4 = 1.7M .. resolution looks good ...


$ffmpeg -i infile.avi -strict experimental -vcodec libx264 -acodec aac -ar 48000 -ac 2 -y outfile.mp4

---

