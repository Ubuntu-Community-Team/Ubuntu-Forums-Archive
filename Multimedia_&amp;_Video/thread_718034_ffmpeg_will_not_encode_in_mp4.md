---
title: "ffmpeg will not encode in mp4"
date: 2008-03-07
forum: Multimedia &amp; Video
---

### Post by underdog512 on 2008-03-07
I am trying to convert an avi to mp4 using ffmpeg.  I have been able to do this in the past, i guess when i was runing fiesty.  now I have ffmpeg installed under gutsy and I keep getting this 


Unsupported codec for output stream #0.1

any ideas as to whats going on?

---

### Post by philc on 2008-03-07
Please post the entire output from FFmpeg to help with resolution.

I'm going to guess and say that you don't have FFmpeg linked to some external libraries, like x264 and xVid.

---

### Post by underdog512 on 2008-03-07
ffmpeg -i /home/adam/Videos/final\ fantasy\ -\ the\ spirits\ within\ divx\ www\ uri\ -\ the\ spirits\ within.avi  -r 800 /home/adam/Videos/final\ fantasy\ -\ the\ spirits\ within\ divx\ www\ uri\ -\ the\ spirits\ within.mp4
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jun  3 2007 20:59:25, gcc: 4.1.3 20070528 (prerelease) (Ubuntu 4.1.2-9ubuntu2)
Input #0, avi, from '/home/adam/Videos/final fantasy - the spirits within divx www uri - the spirits within.avi':
  Duration: 01:41:32.3, start: 0.000000, bitrate: 963 kb/s
  Stream #0.0: Video: msmpeg4, yuv420p, 576x320, 23.98 fps(r)
  Stream #0.1: Audio: mp3, 44100 Hz, stereo, 128 kb/s
Output #0, mp4, to '/home/adam/Videos/final fantasy - the spirits within divx www uri - the spirits within.mp4':
  Stream #0.0: Video: mpeg4, yuv420p, 576x320, q=2-31, 200 kb/s, 800.00 fps(c)
  Stream #0.1: Audio: 0x0000, 44100 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.1

---

### Post by shirilover on 2008-03-07
Are you altering the audio codec in this conversion?
Mp4 containers will not normally accept mp3 audio.
You may need to re-encode the audio stream to AAC first.

---

### Post by philc on 2008-03-08
First, perhaps try altering your FFmpeg command to just copy the video and audio information:

```
ffmpeg -i input.avi -vcodec copy -acodec copy -f mp4 output.mp4
```

If that doesn't work try compiling FFmpeg with the libmp3lame library enabled. --enable-libmp3lame during ./configure

---

### Post by underdog512 on 2008-03-08
hmmm.......   I wonder why it wasn't this complex when I had it installed in fiesty.  it was a real simple command.  

Does anybody think there is a particular codec I am missing?

---

### Post by underdog512 on 2008-03-08
> **philc said:**
> First, perhaps try altering your FFmpeg command to just copy the video and audio information:

```
ffmpeg -i input.avi -vcodec copy -acodec copy -f mp4 output.mp4
```

If that doesn't work try compiling FFmpeg with the libmp3lame library enabled. --enable-libmp3lame during ./configure


here is the output from that command....


ffmpeg -i final_fantasy_the_spirits within.avi -vcodec copy -acodec copy -f mp4 final_fantasy_the_spirits withi.mp4
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jun  3 2007 20:59:25, gcc: 4.1.3 20070528 (prerelease) (Ubuntu 4.1.2-9ubuntu2)
final_fantasy_the_spirits: I/O error occured
Usually that means that input file is truncated and/or corrupted.

---

### Post by Steven_B on 2008-03-08
> Input #0, avi, from '/home/adam/Videos/final fantasy - the spirits within divx www uri - the spirits within.avi':
Duration: 01:41:32.3, start: 0.000000, bitrate: 963 kb/s
Stream #0.0: Video: msmpeg4, yuv420p, 576x320, 23.98 fps(r)
Stream #0.1: Audio: mp3, 44100 Hz, stereo, 128 kb/s
Output #0, mp4, to '/home/adam/Videos/final fantasy - the spirits within divx www uri - the spirits within.mp4':
Stream #0.0: Video: mpeg4, yuv420p, 576x320, q=2-31, 200 kb/s, 800.00 fps(c)
Stream #0.1: Audio: 0x0000, 44100 Hz, stereo, 64 kb/s
Stream mapping:
Stream #0.0 -> #0.0
Stream #0.1 -> #0.1
Unsupported codec for output stream #0.1
I'm pretty sure that the problem is that you need to specify the audio codec.  I have the same issue, and will post a solution if I find one.

**EDIT:** I think I figured it out.  The normal audio codec for .mp4 is AAC, but the ubuntu ffmpeg package doesn't have AAC encoding support due to license issues.  You could compile it yourself, or use [Medibuntu's]("https://help.ubuntu.com/community/Medibuntu") packages.

---

### Post by justsomedude on 2008-03-08
> fmpeg -i /home/adam/Videos/final\ fantasy\ -\ the\ spirits\ within\ divx\ www\ uri\ -\ the\ spirits\ within.avi -r 800 /home/adam/Videos/final\ fantasy\ -\ the\ spirits\ within\ divx\ www\ uri\ -\ the\ spirits\ within.mp4

May I ask what are you trying to do here?

You are forcing a frame rate of 800 fps??? :confused:

If you meant bitrate, you should use -b 800.

But even that would be total nonsense, your input video is 835 kbit/s.

There is no benefit for you at all, the resulting file would be not much smaller but have inferior quality.

If you just want to use an mp4 container, you can use MP4Box to transmux the file. MP4Box is included in gpac (available through Synaptic).

---

