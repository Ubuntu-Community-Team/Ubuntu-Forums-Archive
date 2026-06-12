---
title: "how to rotate an MP4 video"
date: 2013-10-06
forum: Multimedia Software
---

### Post by ZICODIAN on 2013-10-06
Hi *

I would like to rotate a video that was shot in a vertical orientation. The resulting video should rotate the video, but not crop the original. The quality should be as close to the original as possible and the process should not take an unreasonable amount of time to complete. I would appreciate any suggestions. I am new to codecs etc. and I have tried three approaches so far:

- Openshot

OpenShot has an easy to use way to rotate videos, however, it crops the top and bottom of the video, so it is not useful to me for the current task.

- FFmpeg

I am awaiting the results of the following command:

```
ffmpeg -i video_1.mp4 -vf "transpose=1" video_2.mp4
```

The processing for this command is taking far too long for my purposes (it's been over an hour processing a 25 second video).

- MEncoder

I have not yet had success with MEncoder. I ran the following command:

```
mencoder -ovc lavc -vf rotate=2 -oac pcm video_1.mp4 -o video_2.mp4
```

This produced the following output:


```
MEncoder svn r34540 (Ubuntu), built with gcc-4.7 (C) 2000-2012 MPlayer Team


WARNING: OUTPUT FILE FORMAT IS _AVI_. See -of help.
success: format: 0  data: 0x0 - 0x804276
libavformat version 53.21.1 (external)
Mismatching header version 53.19.0
libavformat file format detected.
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (aac), -aid 0, -alang eng
VIDEO:  [H264]  640x480  24bpp  90000.000 fps  2566.0 kbps (313.2 kbyte/s)
[V] filefmt:44  fourcc:0x34363248  size:640x480  fps:90000.000  ftime:=0.0000
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
libavcodec version 53.35.0 (external)
Mismatching header version 53.32.2
AUDIO: 48000 Hz, 2 ch, s16le, 124.6 kbit/8.11% (ratio: 15569->192000)
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [rotate=2]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
Unsupported PixelFormat 61
Unsupported PixelFormat 53
Unsupported PixelFormat 81
Movie-Aspect is undefined - no prescaling applied.
videocodec: libavcodec (480x640 fourcc=34504d46 [FMP4])
[mpeg4 @ 0x7febd0094320]timebase 1/90000 not supported by MPEG 4 standard, the maximum admitted value for the timebase denominator is 65535
Could not open codec.
FATAL: Cannot initialize video driver.


Exiting...
```

I am unsure how to proceed. I would appreciate assistance. Thank you.

---

### Post by FakeOutdoorsman on 2013-10-06
> **ZICODIAN said:**
> 
I am awaiting the results of the following command:

```
ffmpeg -i video_1.mp4 -vf "transpose=1" video_2.mp4
```

The processing for this command is taking far too long for my purposes (it's been over an hour processing a 25 second video).

Using video filters requires encoding, so the defaults may not be what you want if you do no declare any options.

Without the ffmpeg console output I can not tell if, by default, your build is using the encoder "mpeg4" or "libx264" (this one is faster). If you are using libx264, then use a faster preset. Add "-preset veryfast" as an output option (anywhere after the "-i"). Additionally, instead of re-encoding any existing audio you can [stream copy](http://ffmpeg.org/ffmpeg.html#Stream-copy) it with "-codec:a copy" as an output option.

Always include the console output when asking ffmpeg usage questions.

Also see:
[list]
[*][FFmpeg and x264 Encoding Guide](https://trac.ffmpeg.org/wiki/x264EncodingGuide)
[*][How to flip a video 180° (vertical/upside down) with FFmpeg?](http://superuser.com/a/578329/110524)
[/list]

---

