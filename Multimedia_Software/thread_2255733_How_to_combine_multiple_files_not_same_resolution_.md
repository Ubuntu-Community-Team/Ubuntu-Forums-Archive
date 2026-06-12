---
title: "How to combine multiple files not same resolution with mencoder"
date: 2014-12-07
forum: Multimedia Software
---

### Post by lext01 on 2014-12-07
Is there any way to combine multiple files into one with mencoder when some don't have the same resolution?

When trying command:

```

mencoder -forceidx -ovc x264 -oac pcm -o out.avi in1.flv in2.flv

```

I get error:

> 
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: {scale}
Movie-Aspect is 1.69:1 - prescaling to correct movie aspect.

New video file has different resolution or colorspace than the previous one.
FATAL: Cannot initialize video driver.

Exiting...



Using the same command as above with other video files, I get the following error.

> 
Pos:5401.8s 144435f (99%) 263.07fps Trem:   0min 1190mb  A-V:0.001 {431:1411}}
success: format: 0  data: 0x0 - 0x14845d5
libavformat file format detected.
{lavf} stream 0: video (h264), -vid 0
VIDEO:  {H264}  610x360  24bpp  25.000 fps  328.0 kbps (40.0 kbyte/s)
{V} filefmt:44  fourcc:0x34363248  size:610x360  fps:25.000  ftime:=0.0400
Opening video filter: {expand osd=1}
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
=====================================================
Opening video decoder: {ffmpeg} FFmpeg's libavcodec codec family
Selected video codec: {ffh264} vfm: ffmpeg (FFmpeg H.264)
=====================================================

Cannot mix video-only files with audio and video files. Try -nosound.

Exiting...


The first error was with all .flv files.  For the first error, I tried changing -vf and -format, but it seems those don't work.  

The file I was trying to create when the last error happened got to 99% and right before it was about to finish it came up with that error.  The last error was with some .flv files, and one .mp4 file. ALL FILES HAD SOUND!

Any ideas how to fix these problems?

Thanks

---

### Post by TheFu on 2014-12-07
**Any** way?   While not ideal, you can transcode each file to an identical format (same settings, resolution, codec, audio, container) then merge the 2 resulting files ... I'd recommend going to mpeg2 if there is any issue whatsoever.  Using an mpeg3 preset would make sense.  ffmpeg/avconv has presets - don't know about mencoder, sorry.  Whatever the common format is, best to choose the lower resolution and lesser audio as the common values for merging.

When you are done, you can put the mpeg2 files into an mp4 container, or transcode to xvid or h.264, as you like.  .avi, .mp4, .mkv are all just containers. Each can hold many different sorts of audio or video.

---

