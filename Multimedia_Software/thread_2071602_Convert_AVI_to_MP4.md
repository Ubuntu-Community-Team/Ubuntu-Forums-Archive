---
title: "Convert AVI to MP4"
date: 2012-10-15
forum: Multimedia Software
---

### Post by alfirdaous on 2012-10-15
Hi everybody

While converting a video from AVI to MP4, I loose the video quality, BUT if I trim video part (ads part) with an MP4 output, I got a good video quality with more than double video size (169MB becomes 484MB), commands used are:

Remove 5 seconds od ads:
```

sudo ffmpeg -ss 00:00:05 -i input.avi -strict experimental output.mp4

```

Original size is: 169MB, and output size is: 484MB

Convert from AVI to MP4:
```

sudo ffmpeg -i input.avi -strict experimental -acodec aac -ab 128 -vcodec mpeg4 output.mp4

```

Output size is 40MB, less size and less quality.

Here are the input file mediainfo

```

General
Complete name                    : INPUT1.avi
Format                           : AVI
Format/Info                      : Audio Video Interleave
File size                        : 169 MiB
Duration                         : 26mn 19s
Overall bit rate                 : 896 Kbps
Writing application              : VirtualDubMod 1.5.10.3 Fr | www.virtualdub-fr.org ||  (build 2550/release)
Writing library                  : VirtualDubMod build 2550/release

Video
ID                               : 0
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : High@L1.3
Format settings, CABAC           : Yes
Format settings, ReFrames        : 3 frames
Codec ID                         : H264
Duration                         : 26mn 19s
Bit rate                         : 759 Kbps
Width                            : 352 pixels
Height                           : 288 pixels
Display aspect ratio             : 1.222
Frame rate                       : 25.000 fps
Original frame rate              : 50.000 fps
Resolution                       : 8 bits
Colorimetry                      : 4:2:0
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.299
Stream size                      : 143 MiB (85%)
Writing library                  : x264 core 115 r1955bm 06f5fa5
Encoding settings                : cabac=1 / ref=3 / deblock=1:0:0 / analyse=0x3:0x113 / me=hex / subme=7 / psy=1 / psy_rd=1.00:0.00 / mixed_ref=1 / me_range=16 / chroma_me=1 / trellis=1 / 8x8dct=1 / cqm=0 / deadzone=21,11 / fast_pskip=1 / chroma_qp_offset=-2 / threads=2 / sliced_threads=1 / slices=2 / nr=0 / decimate=1 / interlaced=0 / bluray_compat=0 / constrained_intra=0 / bframes=0 / weightp=2 / keyint=250 / keyint_min=25 / scenecut=40 / intra_refresh=0 / rc=crf / mbtree=0 / crf=20.0 / qcomp=0.60 / qpmin=0 / qpmax=69 / qpstep=4 / ip_ratio=1.40 / aq=1:1.00

Audio
ID                               : 1
Format                           : MPEG Audio
Format version                   : Version 1
Format profile                   : Layer 3
Format_Settings_Mode             : Joint stereo
Format_Settings_ModeExtension    : MS Stereo
Codec ID                         : 55
Codec ID/Hint                    : MP3
Duration                         : 26mn 19s
Bit rate mode                    : Constant
Bit rate                         : 128 Kbps
Channel(s)                       : 2 channels
Sampling rate                    : 48.0 KHz
Stream size                      : 24.1 MiB (14%)
Alignment                        : Split accross interleaves
Interleave, duration             : 40 ms (1.00 video frame)
Interleave, preload duration     : 500 ms

```

My aim, is to convert from AVI to MP4, more less the same file size, and same video quality

Thanks in advance

---

### Post by evilsoup on 2012-10-16
Since that AVI file has h.264 video, you can straight-up copy the video stream into an MP4.

```
ffmpeg -i input.avi -vcodec copy -acodec copy output.mp4
```This won't work for all files, but in this case you're lucky, since both the video and audio streams are compatible with MP4. This will be completely lossless.

Also, there's no reason to use sudo, and in fact you should avoid using sudo unless it's absolutely necessary.

---

### Post by alfirdaous on 2012-10-16
thx evilsoup, it works, I tried 3 things on the same:

* Copy from AVI to MP4 => it works
* Remove 3 sec ads => it works
* Write on the video => DOES NOT work

```

ffmpeg -ss 00:00:03 -i INPUT.avi -strict experimental -vf "drawtext=fontfile='/usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold.ttf':text='www.site.com':x=20:y=30:fontsize=15:fontcolor=white" -vcodec copy -acodec copy final_video.mp4

```

---

### Post by FakeOutdoorsman on 2012-10-16
Most video filters, including *drawtext*, require you to re-encode, so filters and "copy" are mutually exclusive. What you need to do is choose the highest *-crf* value that still gives you an acceptable quality. See the CRF section of the [FFmpeg and x264 Encoding Guide](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide).

---

### Post by alfirdaous on 2012-10-17
Thx [FakeOutdoorsman]("http://ubuntuforums.org/member.php?u=162846"), well, I did the drawtext with other filters, but drawtext DOES NOT work, I'll check the link

---

### Post by FakeOutdoorsman on 2012-10-17
> **alfirdaous said:**
> I did the drawtext with other filters, but drawtext DOES NOT work

What do you mean? Please be more descriptive when something does not work as expected and include all necessary steps so someone can easily duplicate the issue.

---

### Post by alfirdaous on 2012-10-17
well, when I combine these three steps at one:

> 
* Copy from AVI to MP4 => it works
* Remove 3 sec ads => it works
* Write on the video => DOES NOT work


the 1st two does work, BUT the drawtext DOES NOT:

```

ffmpeg -ss 00:00:03 -i INPUT.avi -strict experimental -vf "drawtext=fontfile='/usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold.ttf':text='www.site.com':x=20:y=30:fontsize=15:fontcolor=white" -vcodec copy -acodec copy final_video.mp4

```

---

### Post by FakeOutdoorsman on 2012-10-17
As I already mentioned you can not use "drawtext" with "-vcodec copy". In your case drawtext is being ignored. If you want to use drawtext, or any other video filter, then you will have to re-encode instead of simply copying the video stream. Maybe it will be easiest for you if I supply an example:

```
ffmpeg -i INPUT.avi -ss 00:00:03 -vf "drawtext=fontfile='/usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold.ttf':text='www.site.com':x=20:y=30:fontsize=15:fontcolor=white" -vcodec libx264 -preset medium -crf 24 -acodec copy final_video.mp4
```

Adjust the *-crf* and *-preset* options to fit your needs as described in the CRF section of the [FFmpeg and x264 Encoding Guide](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide).

---

### Post by evilsoup on 2012-10-17
Man, after ages of struggling to get to grips with ffmpeg's various poorly-documented options, using a scattering of (often misleading) guides across the internet... that page clarifies a bunch of stuff really well.

Thanks for the link, FakeOutdoorsman.

---

### Post by sidzen on 2012-10-17
Double thanx 4 the link, FakeOutdoorsman!

sidzen
(a once real outdoorsman now just a geek)

---

### Post by alfirdaous on 2012-10-17
Well, I went on a wrong way, looking at the word 'copy, I thought this is a 'copy' operation and there is another word for re-encoding, hence, the other presets are re-encoding.

Thx [FakeOutdoorsman]("http://ubuntuforums.org/member.php?u=162846"), I'll read the doc, still some doubt about preset, pass, maxrate,...

I''ll try the command :)

---

### Post by FakeOutdoorsman on 2012-10-18
Note that the encoding guide is designed for ffmpeg from FFmpeg, not avconv/"fake ffmpeg" from libav which is what Ubuntu now uses; meaning I have no idea if it works with avconv since I do not use it.

---

### Post by alfirdaous on 2012-10-20
> **FakeOutdoorsman said:**
> Note that the encoding guide is designed for ffmpeg from FFmpeg, not avconv/"fake ffmpeg" from libav which is what Ubuntu now uses; meaning I have no idea if it works with avconv since I do not use it.

I think Ubuntu will change the library from FFMPEG to AVCONV, If I am not mistaken, they use the same commands

---

### Post by FakeOutdoorsman on 2012-10-20
I assume libav will not change the names of the libraries (libavcodec, libavformat, etc). You must be referring to the cli tools. They have already changed the names of those upstream. I'm unsure how Ubuntu plans on dealing with this. For 18 months they have continued to use a "transitional ffmpeg" package which is quite confusing and misleading for most users. My guess is that this will continue indefinitely.

---

### Post by alfirdaous on 2012-10-20
Thx [FakeOutdoorsman]("http://ubuntuforums.org/member.php?u=162846"), we will wait then

I guess that re-encoding DOES NOT lose quality, isn't?

---

### Post by FakeOutdoorsman on 2012-10-20
You will lose quality if you re-encode, but not if you copy the stream. Exceptions can include using a lossless encoder (but loss can still occur depending on the situation), and there is "perceptively lossless" where enough bits were used by the encoder that you can't tell a difference between source and output (but it technically isn't lossless).

---

### Post by Merrattic on 2012-10-20
^^^

Spooky !=D>  ;)

---

### Post by alfirdaous on 2012-10-21
Thx everybody

---

