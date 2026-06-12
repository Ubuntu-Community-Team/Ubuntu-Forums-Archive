---
title: "ffmpeg / avconv overlay + scale +audio + time"
date: 2013-09-11
forum: Multimedia Software
---

### Post by Valpskott on 2013-09-11
So, I record gaming videos and render them via scripts. Today I made a watermark of sorts to overlay over my videos.

I've been searchin high and low for 3 problems I'm having.
First of, the overlay is in 1920x1080.

This kinda works for me as long as the recorded video is in the same resolution as the watermark video (1920x1080):
> avconv -i PART01.mov -acodec copy -ar 44100 -vf "movie=watermark.mov [logo];[in][logo] overlay=0:0 [out]" -strict experimental output.mov

I can grab the resolution from PART01.mov via "res=$(avconv -i PART01.mov 2>&1 | grep -m 1 "Stream #0" | awk '{print $8}' | sed -e 's/x.*//g')".
But I can't figure out where to put "scale=1280:720" in the render-command.

The remaining two problems are:
1, include the audio from watermark.mov
2, insert watermark.mov at a specific time (not in the beginning of the episode, but rather 5 minuter in).

Any level of help with either of these problems would be much appreciated.

---

### Post by FakeOutdoorsman on 2013-09-12
> **Valpskott said:**
> 2, insert watermark.mov at a specific time (not in the beginning of the episode, but rather 5 minuter in).

You can do this with real ffmpeg from FFmpeg, but not avconv. You can [compile ffmpeg](http://trac.ffmpeg.org/wiki/CompilationGuide) or simply use a [Linux build of ffmpeg](http://ffmpeg.org/download.html#LinuxBuilds).

Please show the output of:
```
ffmpeg -i PART01.mov -i watermark.mov
```

---

### Post by Valpskott on 2013-09-13
This is the output when a recorded video (PART01.mov) is in 1280x720p.

> 
$ ffmpeg -i PART01.mov -i watermark.mov 
ffmpeg version 0.8.6-4:0.8.6-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Apr  2 2013 17:00:59 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'PART01.mov':
  Metadata:
    major_brand     : isom
    minor_version   : 512
    compatible_brands: isomiso2mp41
    encoder         : Lavf53.21.1
  Duration: 00:00:06.87, start: 0.000000, bitrate: 96208 kb/s
    Stream #0.0(und): Video: mpeg4 (Simple Profile), yuv420p, 1280x720 [PAR 1:1 DAR 16:9], 96541 kb/s, 30 fps, 30 tbr, 30 tbn, 30 tbc
    Stream #0.1(und): Audio: mp3, 44100 Hz, 2 channels, s16, 179 kb/s
Input #1, mov,mp4,m4a,3gp,3g2,mj2, from 'watermark.mov':
  Metadata:
    major_brand     : qt  
    minor_version   : 537199360
    compatible_brands: qt  
    creation_time   : 2013-09-11 14:47:57
  Duration: 00:00:08.19, start: 0.000000, bitrate: 37741 kb/s
    Stream #1.0(eng): Video: qtrle, bgra, 1920x1080, 36604 kb/s, PAR 1920:1920 DAR 16:9, 30 fps, 30 tbr, 30 tbn, 30 tbc
    Metadata:
      creation_time   : 2013-09-11 14:47:57
    Stream #1.1(eng): Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s
    Metadata:
      creation_time   : 2013-09-11 14:47:57
    Stream #1.2(eng): Data: tmcd / 0x64636D74, 0 kb/s
    Metadata:
      creation_time   : 2013-09-11 14:48:15
At least one output file must be specified


However, sometimes (depending on the game) the video will be in 1920x1080, but both the video and audio codecs should be the same as in the 1280x720 videos.

So to clarify. I need help with the syntax of "-vf" to scale down the 1920x1080 watermark to fit a 1280x720 video.
I'd also like if the audio from the watermark will merge with the audio of the video.
And finally, I want to set a time-code for when the watermark should appear in the video. I know I can do that by splitting the video and then joining them together again after the watermark has been added, but that would be a 3-4 step process. I'd rather do everything in one step.

---

### Post by FakeOutdoorsman on 2013-09-13
> **Valpskott said:**
> ```
ffmpeg version 0.8.6-4:0.8.6-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
```
This is the fake ffmpeg from a fork. It is buggy and not useful. You'll need to use the real ffmpeg. See the links I provided earlier in this thread for more info.

Example:
```
ffmpeg -i PART01.mov -i watermark.mov -filter_complex \
"[0:v]scale=1280:720[bg]; \
 [1:v]scale=1280:720[over]; \
 [bg][over]overlay,format=yuv420p[v]; \
 [0:a]aresample=44100,aformat=sample_fmts=s16:channel_layouts=stereo[a0]; \
 [1:a]aresample=44100,aformat=sample_fmts=s16:channel_layouts=stereo[a1]; \
 [a0][a1]amerge,pan=stereo:c0<c0+c2:c1<c1+c3[a]" \
-map "[v]" -map "[a]" -codec:v libx264 -crf 23 -preset medium -codec:a libfdk_aac -vbr 5 output.mov
```

You can enable timeline editing for the video overlay, but it will not automatically also offset the audio from watermark.mov:
```
 [bg][over]overlay=enable='gte(t,5*60)',format=yuv420p[v]; \
```

With amerge, if inputs do not have the same duration, the output will stop with the shortest. 

Also see:
[FFmpeg and x264 Encoding Guide](https://trac.ffmpeg.org/wiki/x264EncodingGuide)
[FFmpeg and AAC Encoding Guide](https://trac.ffmpeg.org/wiki/AACEncodingGuide)
[FFmpeg Filters Documentation](http://ffmpeg.org/ffmpeg-filters.html)
[Timeline editing with FFmpeg filters](http://ffmpeg.org/ffmpeg-filters.html#Timeline-editing)

---

### Post by Valpskott on 2013-09-19
Sorry for late reply and thank you for your reply.

I've updated ffmpeg via a precompiled repo.
> ffmpeg version 0.10.8-7:0.10.8-1~precise1 Copyright (c) 2000-2013 the FFmpeg developers
  built on Sep  5 2013 14:09:48 with gcc 4.6.3
But I get this error.
> Unrecognized option 'filter_complex'

---

