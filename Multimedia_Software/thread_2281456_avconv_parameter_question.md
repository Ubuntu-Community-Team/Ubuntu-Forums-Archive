---
title: "avconv parameter question"
date: 2015-06-07
forum: Multimedia Software
---

### Post by dewdrop_world on 2015-06-07
I've used avconv many times to reduce video resolution, and until yesterday, it always worked very quickly. But yesterday, I was trying to do this to a video file from my phone and it did... weird stuff. I guess I'm missing a parameter, but I never needed any parameters beyond these before. I'm completely at a loss what's different about this input file.

```
$ avconv -ss 06.589 -i VIDEO0009.mp4 -vcodec libx264 -s 640x360 gz-rain-small.mp4

avconv version 0.8.17-4:0.8.17-0ubuntu0.12.04.1, Copyright (c) 2000-2014 the Libav developers
  built on Mar 16 2015 13:26:50 with gcc 4.6.3
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'VIDEO0009.mp4':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: isommp42
    creation_time   : 2015-06-06 09:00:54
  Duration: 00:00:18.04, start: 0.000000, bitrate: 12558 kb/s
    Stream #0.0(eng): Video: h264 (Baseline), yuv420p, 1280x720, 12009 kb/s, PAR 65536:65536 DAR 16:9, 30.04 fps, 90k tbr, 90k tbn, 180k tbc
    Metadata:
      creation_time   : 2015-06-06 09:00:54
    Stream #0.1(eng): Audio: aac, 48000 Hz, stereo, s16, 192 kb/s
    Metadata:
      creation_time   : 2015-06-06 09:00:54
[buffer @ 0x1574dc0] w:1280 h:720 pixfmt:yuv420p
[scale @ 0x156ede0] w:1280 h:720 fmt:yuv420p -> w:640 h:360 fmt:yuv420p flags:0x4
[libx264 @ 0x157a080] using SAR=1/1
[libx264 @ 0x157a080] MB rate (82800000) > level limit (983040)
[libx264 @ 0x157a080] using cpu capabilities: MMX2 SSE2Fast SSSE3 FastShuffle SSE4.2 AVX
[libx264 @ 0x157a080] profile Main, level 5.1
[libx264 @ 0x157a080] 264 - core 120 r2151 a3f4407 - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - http://www.videolan.org/x264.html - options: cabac=1 ref=3 deblock=1:0:0 analyse=0x1:0x111 me=hex subme=7 psy=1 psy_rd=1.00:0.00 mixed_ref=0 me_range=16 chroma_me=1 trellis=1 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=6 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=0 b_adapt=1 b_bias=0 direct=1 weightb=0 open_gop=1 weightp=2 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=crf mbtree=1 crf=23.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.25 aq=1:1.00
Output #0, mp4, to 'gz-rain-small.mp4':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: isommp42
    creation_time   : 2015-06-06 09:00:54
    encoder         : Lavf53.21.1
    Stream #0.0(eng): Video: libx264, yuv420p, 640x360 [PAR 1:1 DAR 16:9], q=-1--1, 180k tbn, 90k tbc
    Metadata:
      creation_time   : 2015-06-06 09:00:54
    Stream #0.1(eng): Audio: libvo_aacenc, 48000 Hz, stereo, s16, 200 kb/s
    Metadata:
      creation_time   : 2015-06-06 09:00:54
Stream mapping:
  Stream #0:0 -> #0:0 (h264 -> libx264)
  Stream #0:1 -> #0:1 (aac -> libvo_aacenc)
Press ctrl-c to stop encoding
frame=  764 fps=380 q=35.0 size=      68kB time=0.01 bitrate=55750.4kbits/s dup=
frame= 3767 fps=336 q=33.0 size=     427kB time=0.04 bitrate=84652.3kbits/s dup=
frame= 6770 fps=324 q=33.0 size=     772kB time=0.07 bitrate=84707.1kbits/s dup=
frame= 9757 fps=320 q=33.0 size=    1129kB time=0.11 bitrate=85740.3kbits/s dup=
frame=12744 fps=318 q=33.0 size=    1487kB time=0.14 bitrate=86348.0kbits/s dup=
frame=15748 fps=317 q=33.0 size=    1835kB time=0.17 bitrate=86201.4kbits/s dup=

```

When I ctrl-C'ed to kill it, it was taking roughly 6 seconds to encode 0.03-0.04 seconds of video. The result should be about 11 seconds, so I'd estimate over 30 minutes for the whole job. [1] states "avconv is a very fast video and audio converter," but almost 3 minutes to encode 1 second of video is somewhat less than "very fast."

I am puzzled by the fps=380, fps=336 statistics. The original video is 30.04 fps. ???

Do I need other commandline parameters? Which ones?

Thanks in advance,
James

---

### Post by SeijiSensei on 2015-06-07
> **dewdrop_world said:**
> I am puzzled by the fps=380, fps=336 statistics. The original video is 30.04 fps. ???

That's the speed of conversion.  Did you let it finish converting and play the result?  What does it look like?

30.04 is a bit weird. Usually a "30 fps" video actually has 29.97 frames per second.

---

### Post by dewdrop_world on 2015-06-07
> **SeijiSensei said:**
> That's the speed of conversion.  Did you let it finish converting and play the result?  What does it look like?

No, because 30 minutes to convert 11 seconds of video is ludicrous.

I'm still confused by the fps reading. If I open the original, unedited video from the phone using avidemux, it tells me the original has 541 frames. (541 / 30.04 = 18 sec -- I'm using avconv's -ss parameter to cut the first 6.5 sec, leaving ~11 sec to convert.) If it's converting over 300 frames per second, it should finish in less than two seconds. ???

hjh

---

### Post by mc4man on 2015-06-08
Don't use phones here nor avconv nor 12.04. What seems suspicious is - 
MB rate (82800000) > level limit (983040) & the various 1835kB time=0.17 bitrate=86201.4kbits/s dup=
Maybe this is your issue - [http://superuser.com/questions/602950/problems-with-frame-rate-on-video-conversion-using-ffmpeg-with-libx264](http://superuser.com/questions/602950/problems-with-frame-rate-on-video-conversion-using-ffmpeg-with-libx264)

---

### Post by FakeOutdoorsman on 2015-06-08
Can you provide the input file? If it's something you'd rather not share can you test a recent [static build of ffmpeg](http://johnvansickle.com/ffmpeg/)?
```

wget http://johnvansickle.com/ffmpeg/builds/ffmpeg-git-32bit-static.tar.xz
tar xf ffmpeg-git-32bit-static.tar.xz
cd ffmpeg-git-*
./ffmpeg -ss 06.589 -i ~/VIDEO0009.mp4 -vcodec libx264 -vf scale 640:-2 ~/gz-rain-small-ffmpeg.mp4
```

---

