---
title: "avconv: Saving MP4 Process Hangs"
date: 2015-09-04
forum: Multimedia Software
---

### Post by christian.griffin on 2015-09-04
Posted this also on AskUbuntu and StackOverflow. No answers.

I'm setting up a website where users can upload videos and share them. I'm using avconv to reduce the video size and save it twice, once as an mp4 and again as a webm.

Uploading a .MOV from a phone, the video conversion is quick and manageable.

Uploading a .mp4 from a Samsung Galaxy S3, the video conversion to webm is also quick. But, the conversion to another mp4 takes FOREVER - literally hours. Why? Is anyone able to shed light on the problem?

My avconv output is below.


```
    avconv -i /path/video.mp4 -c:v libx264 -vf transpose=1,transpose=1,transpose=1 -s 640x480 /path/video-out.mp4
    avconv version 0.8.17-4:0.8.17-0ubuntu0.12.04.1, Copyright (c) 2000-2014 the Libav developers
    built on Mar 16 2015 13:26:50 with gcc 4.6.3
    Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/path/video.mp4':
      Metadata:
        major_brand     : isom
        minor_version   : 0
        compatible_brands: isom3gp4
        creation_time   : 2015-09-04 15:08:21
    Duration: 00:00:07.76, start: 0.000000, bitrate: 11756 kb/s
    Stream #0.0(eng): Video: h264 (Constrained Baseline), yuv420p, 1280x720, 11967 kb/s, 29.81 fps, 90k tbr, 90k tbn, 180k tbc
    Metadata:
      creation_time   : 2015-09-04 15:08:21
    Stream #0.1(eng): Audio: aac, 48000 Hz, stereo, s16, 119 kb/s
    Metadata:
      creation_time   : 2015-09-04 15:08:21
    File '/path/video-out.mp4' already exists. Overwrite ? [y/N] y
    [buffer @ 0xc3d580] w:1280 h:720 pixfmt:yuv420p
    [scale @ 0xc3dac0] w:1280 h:720 fmt:yuv420p -> w:640 h:480 fmt:yuv420p flags:0x4
    [transpose @ 0xc3e280] w:640 h:480 dir:1 -> w:480 h:640 rotation:clockwise vflip:0
    [transpose @ 0xc3e7c0] w:480 h:640 dir:1 -> w:640 h:480 rotation:clockwise vflip:0
    [transpose @ 0xc3ede0] w:640 h:480 dir:1 -> w:480 h:640 rotation:clockwise vflip:0
    [libx264 @ 0xc2b100] MB rate (108000000) > level limit (983040)
    [libx264 @ 0xc2b100] using cpu capabilities: MMX2 SSE2Fast SSSE3 FastShuffle SSE4.2 AVX
    [libx264 @ 0xc2b100] profile Main, level 5.1
    [libx264 @ 0xc2b100] 264 - core 120 r2151 a3f4407 - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - http://www.videolan.org/x264.html - options: cabac=1 ref=3 deblock=1:0:0 analyse=0x1:0x111 me=hex subme=7 psy=1 psy_rd=1.00:0.00 mixed_ref=0 me_range=16 chroma_me=1 trellis=1 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=3 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=0 b_adapt=1 b_bias=0 direct=1 weightb=0 open_gop=1 weightp=2 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=crf mbtree=1 crf=23.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.25 aq=1:1.00
    Output #0, mp4, to '/path/video-out.mp4':
      Metadata:
        major_brand     : isom
        minor_version   : 0
        compatible_brands: isom3gp4
        creation_time   : 2015-09-04 15:08:21
        encoder         : Lavf53.21.1
        Stream #0.0(eng): Video: libx264, yuv420p, 480x640, q=-1--1, 180k tbn, 90k tbc
        Metadata:
          creation_time   : 2015-09-04 15:08:21
        Stream #0.1(eng): Audio: libvo_aacenc, 48000 Hz, stereo, s16, 200 kb/s
        Metadata:
          creation_time   : 2015-09-04 15:08:21
    Stream mapping:
      Stream #0:0 -> #0:0 (h264 -> libx264)
      Stream #0:1 -> #0:1 (aac -> libvo_aacenc)
    Press ctrl-c to stop encoding
```

Here's an example frame output:

```
    frame=124398 fps=142 q=33.0 size=   16885kB time=1.38 bitrate=100110.2kbits/s dup=124356 drop=0
```

I've had the process running the whole time I've been writing this question, and so far it's done... 22 frames.

What could be the problem?

Since posting the question on AskUbuntu and StackOverflow, the process has just started hanging, and won't move past frame... 32 or so. Also hard rebooted the server in case the CPU was just getting overwhelmed with other processes. No dice, same problem.

It's worth noting that I'm more or less a novice at this. I could be totally misreading the output. I could be missing a very obvious solution. If so I apologize.

---

### Post by TheFu on 2015-09-04
I've been using ffmpeg from a daily binary PPA.

```
#!/bin/sh
SZ=720 
FF_OPTS="-vcodec libx264 -crf 19.5 -preset medium -strict experimental -filter:v scale=-1:$SZ -c:a aac "

for filename in "$@"; do

   IN="$filename"
   ROOT=`echo "$filename"| sed -e 's/.avi$//' `
   OUT="$ROOT-$SZ.mkv"

   nice ffmpeg -y -i "$IN" $FF_OPTS  "$OUT"
   sleep 10
done
```

I like to maintain constant quality - some real crap output will happen otherwise.  I also prefer mkv containers over mp4.  Use the preset options - fast, speedo-fast, ludacris-fast ... check the manpage for the exact presets. I don't remember what they really are. Basically the speed of the encoding determines the file size with this method.  Oh - and the input filename needs to be scrubbed to prevent spaces or other weird characters with this script.

There are better ways to get the "ROOT" name - I was just lazy.
The scaling maintains the aspect ratio and I only throw HiDef inputs.  If the original input was smaller, this would not be smart.

What's the deal with the 3 transpose?  [https://ffmpeg.org/ffmpeg-filters.html#transpose](https://ffmpeg.org/ffmpeg-filters.html#transpose) shows how to use that for ffmpeg.

Oh - the 10 sec sleep at the end lets the CPUs cool down - I had overheating issues.  If you want to have a first-in-first-out queue, check out taskspooler.

Sorry - that's all I know.

---

### Post by mc4man on 2015-09-04
> **christian.griffin said:**
> 

```
    frame=124398 fps=142 q=33.0 size=   16885kB time=1.38 bitrate=100110.2kbits/s dup=124356 drop=0
```

.
Your are duping an incredible number of frames & the reported  kbits/s is about 100 times higher than it should be based on your command. Seems a mess, try ffmpeg instead

---

### Post by FakeOutdoorsman on 2015-09-05
> **mc4man said:**
> Seems a mess, try ffmpeg instead

Unsurprisingly, [using ffmpeg was the solution](http://askubuntu.com/questions/670241/avconv-saving-mp4-process-hangs).

---

