---
title: "FFmpeg failing to transcode from MPEG2-PS to DV"
date: 2006-11-22
forum: Multimedia &amp; Video
---

### Post by Jonathan Métillon on 2006-11-22
Hi,

I try to transcode a MPEG2-PS file containing MPEG2 video and AC3
sound to a DV file with FFmpeg. I use this command:

```
ffmpeg -i MOV068.mpg -target dv -croptop 86 -cropbottom 86 MOV068.dv
```Which produces this result :

```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads
--enable-vorbis --enable-libogg --enable-a52 --enable-dts
--enable-libgsm --enable-dc1394 --disable-debug --enable-shared
--prefix=/usr
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Sep 20 2006 00:26:15, gcc: 4.1.2 20060906 (prerelease)
(Ubuntu 4.1.1-13ubuntu2)
Input #0, mpeg, from 'MOV068.mpg':
  Duration: 00:00:03.9, start: 0.258444, bitrate: 4167 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x576, 8400 kb/s,
25.00 fps(r)
  Stream #0.1[0x80]: Audio: ac3, 48000 Hz, stereo, 256 kb/s
Assuming PAL for target.
Output #0, dv, to 'MOV068.dv':
  Stream #0.0: Video: dvvideo, yuv420p, 720x404, q=2-31, 200 kb/s, 25.00 fps(c)
  Stream #0.1: Audio: pcm_s16le, 48000 Hz, stereo, 1536 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
No accelerated IMDCT transform found
[dv @ 0xb7f7fc30]Can't initialize DV format!
Make sure that you supply exactly two streams:
     video: 25fps or 29.97fps, audio: 2ch/48Khz/PCM
     (50Mbps allows an optional second audio stream)
Could not write header for output file #0 (incorrect codec parameters ?)
```I checked with ffmpeg -formats and it shows that the DV format is
avaiable. What's going on? How can I fix that?

The exact version I use is:

```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Sep 20 2006 00:26:15, gcc: 4.1.2 20060906 (prerelease) (Ubuntu 4.1.1-13ubuntu2)
ffmpeg      SVN-rUNKNOWN
libavutil   3211264
libavcodec  3345152
libavformat 3278080
```
Thank you for your time!

Jonathan

---

### Post by zoreslav on 2006-12-23
You should type it like that:
ffmpeg -i something.avi -target dv  ~/Desktop/new.dv
works fine for me in that order of parameters exactly,

---

### Post by Jonathan Métillon on 2006-12-23
Oh thank you zoreslav ;)

This is an old post, I already solved this and much more. You can see that here:

[http://ubuntuforums.org/showthread.php?t=231202#post1855229](http://ubuntuforums.org/showthread.php?t=231202#post1855229)

Thank you again. :-D

---

