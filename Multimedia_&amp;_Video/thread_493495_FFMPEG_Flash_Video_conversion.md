---
title: "FFMPEG Flash Video conversion"
date: 2007-07-05
forum: Multimedia &amp; Video
---

### Post by sbennettgso on 2007-07-05
I've got a working Gallery2 installation and I'm trying to get videos stored on my server such that they will stream.  I ran across using FFMPEG as a transcoder to accomplish this, but the audio doesn't seem to come through on the transcoded file.  Here's output from one attempt at this:

```
scott@scott-laptop:~/Desktop$ ffmpeg -i 100_2771.MOV movie.flv
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Jan 28 2007 22:48:38, gcc: 4.1.2 20070106 (prerelease) (Ubuntu 4.1.1-21ubuntu7)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '100_2771.MOV':
  Duration: 00:00:49.9, start: 0.000000, bitrate: 2429 kb/s
  Stream #0.0(eng): Video: mjpeg, yuvj420p, 320x240, 20.00 fps(r)
  Stream #0.1(eng): Audio: pcm_s8, 11025 Hz, mono, 88 kb/s
Output #0, flv, to 'movie.flv':
  Stream #0.0: Video: flv, yuv420p, 320x240, q=2-31, 200 kb/s, 20.00 fps(c)
Stream mapping:
  Stream #0.0 -> #0.0
[flv @ 0xb7ec8508]removing common factors from framerate
Press [q] to stop encoding
frame=  999 q=14.1 Lsize=    1411kB time=50.0 bitrate= 231.4kbits/s    
video:1395kB audio:0kB global headers:0kB muxing overhead 1.130339%

```

I can see that the audio stream was not mapped to the output file.  Am I missing a configure option in FFMPEG?

Thanks,
Scott

---

