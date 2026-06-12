---
title: "Remove video bottom part: black screen"
date: 2016-01-10
forum: Multimedia Software
---

### Post by alfirdaous on 2016-01-10
Hello everyone,

I cropped a video bottom (50 pixels), using ffmpeg command line, the output is black screen, the sound is clear and good:

```
   ffmpeg -i Original.mp4 -t 00:00:29 -vf crop=iw:ih-50:0:0 Done.mp4
```

  ffmpeg version:

  ```
ffmpeg version 0.8.17-4:0.8.17-0ubuntu0.12.04.1, Copyright (c) 2000-2014 the Libav developers
  built on Mar 16 2015 13:26:50 with gcc 4.6.3
```

  video information:

  ```
mediainfo '--Inform=Video;%Width%x%Height%' Original.mp4
634x360
```

  Thanks in advance

---

### Post by mc4man on 2016-01-11
In 12.04 either use avconv or better yet try a static *real* ffmpeg build, it should be ok in 12.04 (never tried, never will
[http://johnvansickle.com/ffmpeg/](http://johnvansickle.com/ffmpeg/)

What's called ffmpeg in 12.04 is some old bastardization by the libav folks

---

### Post by alfirdaous on 2016-01-12
I used avconv, I've got the same result:

mediainfo for original file:

```

General
Complete name                            : Original.mp4
Format                                   : MPEG-4
Format profile                           : Base Media / Version 2
Codec ID                                 : mp42
File size                                : 15.3 MiB
Duration                                 : 5mn 35s
Overall bit rate mode                    : Variable
Overall bit rate                         : 383 Kbps
Encoded date                             : UTC 2015-07-24 08:01:26
Tagged date                              : UTC 2015-07-24 08:01:26
gsst                                     : 0
gstd                                     : 335945
gssd                                     : B0AFCF32B
gshh                                     : r9---sn-25g7sne7.googlevideo.com

Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : Baseline@L3.0
Format settings, CABAC                   : No
Format settings, ReFrames                : 1 frame
Format settings, GOP                     : M=1, N=60
Codec ID                                 : avc1
Codec ID/Info                            : Advanced Video Coding
Duration                                 : 5mn 35s
Bit rate                                 : 285 Kbps
Maximum bit rate                         : 569 Kbps
Width                                    : 634 pixels
Height                                   : 360 pixels
Display aspect ratio                     : 16:9
Frame rate mode                          : Constant
Frame rate                               : 29.970 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.042
Stream size                              : 11.4 MiB (74%)
Tagged date                              : UTC 2015-07-24 08:01:28

Audio
ID                                       : 2
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : LC
Codec ID                                 : 40
Duration                                 : 5mn 35s
Bit rate mode                            : Variable
Bit rate                                 : 96.0 Kbps
Maximum bit rate                         : 102 Kbps
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 44.1 KHz
Compression mode                         : Lossy
Stream size                              : 3.84 MiB (25%)
Title                                    : IsoMedia File Produced by Google, 5-11-2011
Encoded date                             : UTC 2015-07-24 08:01:27
Tagged date                              : UTC 2015-07-24 08:01:28

```


mediainfo for cropped file:

```

General
Complete name                            : Done.mp4
Format                                   : MPEG-4
Format profile                           : Base Media
Codec ID                                 : isom
File size                                : 645 KiB
Duration                                 : 9s 10ms
Overall bit rate mode                    : Variable
Overall bit rate                         : 587 Kbps
Encoded date                             : UTC 2015-07-24 08:01:26
Tagged date                              : UTC 2015-07-24 08:01:26
Writing application                      : Lavf53.21.1

Video
ID                                       : 1
Format                                   : MPEG-4 Visual
Format profile                           : Simple@L1
Format settings, BVOP                    : No
Format settings, QPel                    : No
Format settings, GMC                     : No warppoints
Format settings, Matrix                  : Default (H.263)
Codec ID                                 : 20
Duration                                 : 9s 9ms
Bit rate                                 : 381 Kbps
Width                                    : 634 pixels
Height                                   : 310 pixels
Display aspect ratio                     : 2.045
Frame rate mode                          : Constant
Frame rate                               : 29.970 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Compression mode                         : Lossy
Bits/(Pixel*Frame)                       : 0.065
Stream size                              : 419 KiB (65%)
Writing library                          : Lavc53.35.0
Encoded date                             : UTC 2015-07-24 08:01:26
Tagged date                              : UTC 2015-07-24 08:01:26

Audio
ID                                       : 2
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : LC
Codec ID                                 : 40
Duration                                 : 9s 10ms
Bit rate mode                            : Variable
Bit rate                                 : 200 Kbps
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 44.1 KHz
Compression mode                         : Lossy
Stream size                              : 220 KiB (34%)
Encoded date                             : UTC 2015-07-24 08:01:26
Tagged date                              : UTC 2015-07-24 08:01:26

```

---

### Post by mc4man on 2016-01-12
Try the static ffmpeg, 4 years is old even for the likes of libav

---

### Post by alfirdaous on 2016-01-12
> **mc4man said:**
> Try the static ffmpeg, 4 years is old even for the likes of libav

I tried, the same result, I will change the video, may be it is coming from the video source

---

### Post by FakeOutdoorsman on 2016-01-12
Please show your command and the complete console output. What player are you trying?

---

### Post by alfirdaous on 2016-01-12
Here you go:

```

ffmpeg -i Original/Original.mp4 -t 00:00:29 -vf crop=iw:ih-50:0:0 Done/Done.mp4

ffmpeg version 0.8.17-4:0.8.17-0ubuntu0.12.04.1, Copyright (c) 2000-2014 the Libav developers
  built on Mar 16 2015 13:26:50 with gcc 4.6.3
The ffmpeg program is only provided for script compatibility and will be removed
in a future release. It has been deprecated in the Libav project to allow for
incompatible command line syntax improvements in its replacement called avconv
(see Changelog for details). Please use avconv instead.
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Original/Original.mp4':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: isommp42
    creation_time   : 2015-07-24 08:01:26
  Duration: 00:05:35.87, start: 0.000000, bitrate: 383 kb/s
    Stream #0.0(und): Video: h264 (Constrained Baseline), yuv420p, 634x360 [PAR 1:1 DAR 317:180], 284 kb/s, 29.97 fps, 29.97 tbr, 30k tbn, 59.94 tbc
    Stream #0.1(und): Audio: aac, 44100 Hz, stereo, s16, 96 kb/s
    Metadata:
      creation_time   : 2015-07-24 08:01:27
[buffer @ 0x639d80] w:634 h:360 pixfmt:yuv420p
[crop @ 0x6482e0] w:634 h:360 -> w:634 h:310
Output #0, mp4, to 'Done/Done.mp4':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: isommp42
    creation_time   : 2015-07-24 08:01:26
    encoder         : Lavf53.21.1
    Stream #0.0(und): Video: mpeg4, yuv420p, 634x310 [PAR 1:1 DAR 317:155], q=2-31, 200 kb/s, 30k tbn, 29.97 tbc
    Stream #0.1(und): Audio: libvo_aacenc, 44100 Hz, stereo, s16, 200 kb/s
    Metadata:
      creation_time   : 2015-07-24 08:01:27
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press ctrl-c to stop encoding
frame=  870 fps= 92 q=19.3 Lsize=    1679kB time=29.00 bitrate= 474.2kbits/s
video:953kB audio:708kB global headers:0kB muxing overhead 1.086535%

```

I am trying to play it on the web, on MAC as well using iTunes and QuickTimes Player

---

### Post by FakeOutdoorsman on 2016-01-13
That's the old, dead, broken, buggy counterfeit "ffmpeg" from the fork named Libav that mc4man mentioned. Download ffmpeg from the link from post #2.

You have several options to execute it (note the **./**):
```
cd to/directory/containing_it
./ffmpeg -i ...
```

or

```
/full/path/to/ffmpeg -i ...
```

or
```

mkdir ~/bin
mv ffmpeg ~/bin
hash -r
. ~/.profile
```

This 3rd option lets you just run "ffmpeg" no matter what directory you're in. Alternatively, instead of running "hash -r && . ~/.profile" you can simply log out then log in. You'll only need to do that once.

---

### Post by Rob Sayer on 2016-01-14
If you want to learn CLI tools that's fine, but have you tried doing this in avidemux or Openshot?  Avidemux (at least from the repos, which is the one I use) isn't the best at h.264/mpeg4 AVC support.  For that something like Openshot would be better.  But for mpeg-4 visual it's fine.  And both are reasonably easy to use.

I'm also curious whether all you wanted to do was crop the video or convert the format as well.  The input is mpeg-4 AVC and the output is mpeg-4 Visual.  That's a quite old format and not very powerful.  Xvid would be better, especially because bmore devices support it.  But if all you wanted to do is crop I don't see much need for a different format output.

---

