---
title: "avconv speeds up video"
date: 2014-06-13
forum: Multimedia Software
---

### Post by palmerito0 on 2014-06-13
Hi, I'm trying to convert a .crf file from a security camera to a .mp4 MPEG-4 file. 

I tried ```
avconv -i XXXX.crf -c:v libx264 XXXXX.mp4
``` and the file was converted with no errors. When I checked the file size of the .mp4 file, it was 1/10 of the size of the .crf file. When I played this new .mp4 file, the video was going ~40x faster than the .crf file!

This is the mediainfo for the .crf:

```

General
ID                               : 1 (0x1)
Complete name                    : C:\Users\rcarreteroadmin\Desktop\232518.crf
Format                           : MPEG-TS
File size                        : 1.27 MiB
Duration                         : 42s 320ms
Overall bit rate                 : 251 Kbps


Video
ID                               : 256 (0x100)
Menu ID                          : 1 (0x1)
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : Baseline@L3.0
Format settings, CABAC           : No
Format settings, ReFrames        : 1 frame
Format settings, GOP             : M=1, N=16
Codec ID                         : 27
Duration                         : 42s 353ms
Bit rate                         : 239 Kbps
Width                            : 640 pixels
Height                           : 480 pixels
Display aspect ratio             : 4:3
Frame rate mode                  : Variable
Standard                         : Component
Color space                      : YUV
Chroma subsampling               : 4:2:0
Bit depth                        : 8 bits
Scan type                        : Progressive
Stream size                      : 1.20 MiB (95%)


Menu
ID                               : 4095 (0xFFF)
Menu ID                          : 1 (0x1)
Duration                         : 42s 320ms
List                             : 256 (0x100) (AVC) / 257 (0x101) ()
Service name                     : vservice3
Service provider                 : vmpeg4
Service type                     : digital television

```

And for the .mp4:

```

GeneralFormat                           : MPEG-4
Format profile                   : Base Media
Codec ID                         : isom
File size                        : 197 KiB
Duration                         : 766ms
Overall bit rate                 : 2 106 Kbps
Writing application              : Lavf53.21.1


Video
ID                               : 1
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : Main@L3.0
Format settings, CABAC           : Yes
Format settings, ReFrames        : 3 frames
Codec ID                         : avc1
Codec ID/Info                    : Advanced Video Coding
Duration                         : 766ms
Bit rate mode                    : Variable
Bit rate                         : 2 093 Kbps
Width                            : 640 pixels
Height                           : 480 pixels
Display aspect ratio             : 4:3
Frame rate mode                  : Variable
Frame rate                       : 31.332 fps
Minimum frame rate               : 30.000 fps
Maximum frame rate               : 60.000 fps
Color space                      : YUV
Chroma subsampling               : 4:2:0
Bit depth                        : 8 bits
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.217
Stream size                      : 196 KiB (99%)
Writing library                  : x264 core 123 r2189 35cf912
Encoding settings                : cabac=1 / ref=3 / deblock=1:0:0 / analyse=0x1:0x111 / me=hex / subme=7 / psy=1 / psy_rd=1.00:0.00 / mixed_ref=0 / me_range=16 / chroma_me=1 / trellis=1 / 8x8dct=0 / cqm=0 / deadzone=21,11 / fast_pskip=1 / chroma_qp_offset=-2 / threads=12 / sliced_threads=0 / nr=0 / decimate=1 / interlaced=0 / bluray_compat=0 / constrained_intra=0 / bframes=3 / b_pyramid=0 / b_adapt=1 / b_bias=0 / direct=1 / weightb=0 / open_gop=1 / weightp=2 / keyint=250 / keyint_min=25 / scenecut=40 / intra_refresh=0 / rc_lookahead=40 / rc=crf / mbtree=1 / crf=23.0 / qcomp=0.60 / qpmin=0 / qpmax=69 / qpstep=4 / ip_ratio=1.25 / aq=1:1.00

```

Thank You!

---

### Post by SeijiSensei on 2014-06-13
My guess is that the camera uses a low frame rate.  Try using the "-r" parameter to set an output frame rate.  Look in the camera's documentation to see what rate it uses, or just experiment with some low numbers.  I'd start with "-r 1" which shows one frame per second and go up from there as needed.
```
avconv -i XXXX.crf -c:v libx264 -r 1 XXXXX.mp4
```

---

### Post by FakeOutdoorsman on 2014-06-13
Can you provide the input file? Do you know the make and model of the camera?

---

### Post by palmerito0 on 2014-06-14
> **SeijiSensei said:**
> My guess is that the camera uses a low frame rate.  Try using the "-r" parameter to set an output frame rate.  Look in the camera's documentation to see what rate it uses, or just experiment with some low numbers.  I'd start with "-r 1" which shows one frame per second and go up from there as needed.
```
avconv -i XXXX.crf -c:v libx264 -r 1 XXXXX.mp4
```

I had already tried that, but I was trying at about 30 fps. This is probably my answer. Ill try it as soon as I can. :P

---

