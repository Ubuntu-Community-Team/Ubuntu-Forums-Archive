---
title: "Cinelerra Read/Write Error?"
date: 2008-04-01
forum: Multimedia &amp; Video
---

### Post by dbsoundman on 2008-04-01
I have just started using Cinelerra, and I'm trying to render a video I made. I found some instructions [here]("http://crazedmuleproductions.blogspot.com/2007/06/beginners-guide-to-exporting-video-from.html#dvd"), and I followed them, but I can't get the video to render. I started Cinelerra in a terminal to get the errors, and this is what I got for output. As you can see, I tried twice, and the second time I removed the -hq command to see if that was the problem:

```

Render::run 1
Render::run 2
Render::run 3
Render::run 4
Render::run 5
Render::run 6
Render::run 7
Render::run 8
Render::run 8.1
Render::run 8.2
Render::run 8.3
Render::run 9
Render::run 10
trying popen( ffmpeg -f yuv4mpegpipe -i - -y -target dvd -ilme -ildct -hq -f mpeg2video /home/dan/Video/jaroslav video cinelerra.m2v)
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Jan 28 2007 22:48:38, gcc: 4.1.2 20070106 (prerelease) (Ubuntu 4.1.1-21ubuntu7)
Input #0, yuv4mpegpipe, from 'pipe:':
  Duration: N/A, bitrate: N/A
  Stream #0.0: Video: rawvideo, yuv420p, 720x480, 29.97 fps(r)
Assuming NTSC for target.
ffmpeg: unrecognized option '-hq'
Received sigpipe
Render::run: Session finished.
Render::render 90
Render::run 11
Render::run 12
Render::run 100
Render::run 1
Render::run 2
Render::run 3
Render::run 4
Render::run 5
Render::run 6
Render::run 7
Render::run 8
Render::run 8.1
Render::run 8.2
Render::run 8.3
Render::run 9
Render::run 10
trying popen( ffmpeg -f yuv4mpegpipe -i - -y -target dvd -ilme -ildct -f mpeg2video /home/dan/Video/jaroslav video cinelerra.m2v)
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Jan 28 2007 22:48:38, gcc: 4.1.2 20070106 (prerelease) (Ubuntu 4.1.1-21ubuntu7)
Input #0, yuv4mpegpipe, from 'pipe:':
  Duration: N/A, bitrate: N/A
  Stream #0.0: Video: rawvideo, yuv420p, 720x480, 29.97 fps(r)
Assuming NTSC for target.
Unable for find a suitable output format for 'video'
Received sigpipe
Render::run: Session finished.

```

The error Cinelerra tells me is something about a read/write error. I had no problems exporting the audio, only the video. Any ideas of what is wrong?

Thanks,
Dan

---

### Post by dbsoundman on 2008-04-01
One other note: I disabled the "use pipe" command, and it is working now. I will find out later what happens when I use ffmpeg to mux the files, but I would still like to know what is wrong with the pipe.

-Dan

---

