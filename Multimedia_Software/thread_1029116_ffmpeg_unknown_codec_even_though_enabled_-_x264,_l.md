---
title: "ffmpeg unknown codec even though enabled - x264, libfaac"
date: 2009-01-03
forum: Multimedia Software
---

### Post by steve457 on 2009-01-03
I am having the hardest time trying to figure out why ffmpeg is unable to find the x264 and faac codec on my system.  The ffmpeg version I have installed is from the Mediabuntu repository, so it appears that these codecs should be enabled.

> 
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Input #0, avi, from 'MVI_1808.AVI':
  Duration: 00:00:45.1, start: 0.000000, bitrate: 15616 kb/s
  Stream #0.0: Video: mjpeg, yuvj422p, 640x480, 30.00 fps(r)
  Stream #0.1: Audio: pcm_s16le, 44100 Hz, mono, 705 kb/s
Unknown codec 'libx264'


I also checked the Synaptic package manager and found that libfaac0, libx264, x264, faac are all indicated as being installed.  What else am I missing here?  I am completely stumped at this point.

---

### Post by andrew.46 on 2009-01-03
Hi Steve,

Naming conventions change a little with ffmpeg. Try the following:

```
$ ffmpeg -formats | grep 264
```

Probably your x264 / h.264 encoder has a different name, perhaps 'h264' although I don't run your version so I cannot tell for sure.

  Andrew

---

### Post by dannyboy79 on 2010-06-15
bump, anyone having this problem? I am trying to run this command
```
cat capture008.dv | ffmpeg -f dv -i pipe: -acodec aac -vcodec h264 -s 720x480 -aspect 4:3 capture008.mp4

```
and I get this in return:
Unknown encoder 'h264'
cat: write error: Broken pipe
I found the pipe command with ffmpeg online and I am not sure how to use it despite me copying and pasting it. can someone help me? i am trying to be able to capture raw dv using dazzle hollywood dv bridge from my xbox360, then edit it with kino and export the edited dv file, then convert it using ffmpeg cause i don't like the mp4 best quality that kino exports, it's junk.

---

