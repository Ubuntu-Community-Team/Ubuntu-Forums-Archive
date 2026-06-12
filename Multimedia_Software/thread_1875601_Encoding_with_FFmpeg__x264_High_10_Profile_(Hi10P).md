---
title: "Encoding with FFmpeg / x264: High 10 Profile (Hi10P)"
date: 2011-11-05
forum: Multimedia Software
---

### Post by andrew.46 on 2011-11-05
University vacation is upon me so I have been investigating using FFmpeg to encode using High 10 Profile (Hi10P) which I believe is pretty big in the anime world but has not spread much further. I am interested to hear if anybody has been using it or if there can be any suggestions made of the technique I have used?

First step was to recompile x264 with the *--bit-depth=10* option, perhaps easiest Ubuntu method is follow [FakeOutdoorsman's great guide]("http://ubuntuforums.org/showthread.php?t=786095") and simply add this option in to the ./configure string given for x264. Next pull out my favourite scene from the Matrix:

```

tccat -i /dev/dvd -T 1,15,1 > fight.vob

```

and then pull out the audio and convert to aac:

```

ffmpeg -i fight.vob -ac 2 -ar 44100 -vn -f wav - | \
          neroAacEnc -ignorelength -q 0.65 -if - -of audio.mp4

```

The video processing is the one I am not so sure about, so I would welcome suggestions here:

```

ffmpeg -i fight.vob -an \
       -vcodec libx264 -preset veryslow -tune film -profile high10 \
       -crf 24 -vf crop=720:416:0:80 \
       video.mp4

```

The cropping is simply to take out the black bars from top and bottom. Note the slightly higher than usual crf value which I believe is recommended for h10 encoding. I then mux with mkvmerge:

```

mkvmerge --title "Matrix sparring scene" -o matrix_sparring_h10.mkv \
         --track-name 1:"Encoded with x264 High 10 Profile (Hi10P)" \
         --language 1:eng --default-track 1:yes video.mp4 \
         --track-name 1:"Encoded with neroAacEnc 1.5.4.0" \
         --language 1:eng --default-track 1:yes audio.mp4

```
The final result is here:

```

wget http://www.andrews-corner.org/tmp/matrix_sparring_h10.mkv

```

I would value any comments on the technique I have used and the quality of the output clip, plus any comments on the so-called 'high 10' profile in x264. Mediainfo shows the following on this output file:

```

andrew@skamandros~/media/matrix$ mediainfo matrix_sparring_h10.mkv 
General
Unique ID                                : 14829788043047948209532235037227713355 (0xB281D005167F7A3F5DF8B84E31D834B)
Complete name                            : matrix_sparring_h10.mkv
Format                                   : Matroska
Format version                           : Version 2
File size                                : 23.7 MiB
Duration                                 : 4mn 22s
Overall bit rate                         : 757 Kbps
Movie name                               : Matrix sparring scene
Encoded date                             : UTC 2011-11-05 20:57:30
Writing application                      : mkvmerge v5.0.1 ('Es ist Sommer') built on Oct 10 2011 19:36:05
Writing library                          : libebml v1.2.2 + libmatroska v1.3.0

Video
ID                                       : 1
[B][COLOR="Red"]Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : High 10@L3.2[/COLOR][/B]
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 16 frames
Muxing mode                              : Header stripping
Codec ID                                 : V_MPEG4/ISO/AVC
Duration                                 : 4mn 22s
Width                                    : 720 pixels
Height                                   : 416 pixels
Display aspect ratio                     : 2.462
Frame rate mode                          : Variable
Frame rate                               : 25.000 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 10 bits
Scan type                                : Progressive
Title                                    : Encoded with x264 High 10 Profile (Hi10P)
Writing library                          : x264 core 119 r2106 07efeb4
Encoding settings                        : cabac=1 / ref=16 / deblock=1:-1:-1 / analyse=0x3:0x133 / me=umh / subme=10 / psy=1 / psy_rd=1.00:0.15 / mixed_ref=1 / me_range=24 / chroma_me=1 / trellis=2 / 8x8dct=1 / cqm=0 / deadzone=21,11 / fast_pskip=1 / chroma_qp_offset=-3 / threads=3 / sliced_threads=0 / nr=0 / decimate=1 / interlaced=0 / bluray_compat=0 / constrained_intra=0 / bframes=8 / b_pyramid=2 / b_adapt=2 / b_bias=0 / direct=3 / weightb=1 / open_gop=0 / weightp=2 / keyint=250 / keyint_min=25 / scenecut=40 / intra_refresh=0 / rc_lookahead=60 / rc=crf / mbtree=1 / crf=24.0 / qcomp=0.60 / qpmin=0 / qpmax=81 / qpstep=4 / ip_ratio=1.40 / aq=1:1.00
Language                                 : English

Audio
ID                                       : 2
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : LC
Codec ID                                 : A_AAC
Duration                                 : 4mn 22s
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 44.1 KHz
Compression mode                         : Lossy
Title                                    : Encoded with neroAacEnc 1.5.4.0
Language                                 : English

Menu
00:00:00.059                             : en:00:00:00.059

```

---

### Post by kd7lxl on 2012-02-27
> **andrew.46 said:**
> First step was to recompile x264 with the *--bit-depth=10* option, perhaps easiest Ubuntu method is follow [FakeOutdoorsman's great guide]("http://ubuntuforums.org/showthread.php?t=786095") and simply add this option in to the ./configure string given for x264.
> ```

ffmpeg -i fight.vob -an \
       -vcodec libx264 -preset veryslow -tune film -profile high10 \
       -crf 24 -vf crop=720:416:0:80 \
       video.mp4
```Does compiling this way replace an existing 8-bit-depth libx264, or do they coexist? I see you are instructing ffmpeg to use Hi10P. I would like 8-bit-depth and 10-bit-depth installations of libx264 to coexist, so I can choose which bit-depth to use at runtime. It's not clear if this is possible with your installation.

---

### Post by andrew.46 on 2012-02-28
I believe that with x264 it is a case of using one or the other, but I am ready to be corrected.... I will investigate a little further.

---

### Post by kd7lxl on 2012-02-28
Hmm, that's what I was afraid of. Maybe I can hint which version of the library I want to use with LD_LIBRARY_PATH.

Did you have to recompile ffmpeg after you rebuilt libx264? I'm still thinking there's got to be a way to juggle two versions of libx264 and choose one at runtime.

---

### Post by andrew.46 on 2012-02-28
I certainly recompiled FFmpeg.

---

