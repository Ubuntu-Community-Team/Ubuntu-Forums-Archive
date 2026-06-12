---
title: "glc-play | ffmpeg encoding = 0 seconds video?"
date: 2011-10-15
forum: Multimedia Software
---

### Post by Homo Luminus on 2011-10-15
Hello.

I've been trying to record some ingame footage of a game I'm working on. Since it uses OpenGL, I'm using glc-capture to capture the screen. The capturing goes well, I can play back the stream using glc-play. However, when trying to encode the stream into mp4 format, this happens:

```

codemonkey$ glc-play rwi_0_25.linux-29991-0.glc -o - -y 1 | ffmpeg -i - -sameq -y video.mp4
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Sep 16 2011 17:04:18, gcc: 4.4.3
Input #0, yuv4mpegpipe, from 'pipe:':
  Duration: N/A, bitrate: N/A
    Stream #0.0: Video: rawvideo, yuv420p, 640x480, 30 tbr, 30 tbn, 30 tbc
Output #0, mp4, to 'video.mp4':
    Stream #0.0: Video: mpeg4, yuv420p, 640x480, q=2-31, 200 kb/s, 90k tbn, 30 tbc
Stream mapping:
  Stream #0.0 -> #0.0
frame=   11 fps=  0 q=0.0 Lsize=       6kB time=0.37 bitrate= 126.1kbits/s    
video:5kB audio:0kB global headers:0kB muxing overhead 17.221095%

```

It looks like a nice ffmpeg output with no problems. But when I play back the video.mp4 in VLC, it doesn't show anything at all. It seems to be an mp4 file of 0 seconds length. VLC gives no error messages either, just plays it, but there's nothing in there... Any thoughts?

I'm running 10.04 by the way.

---

### Post by FakeOutdoorsman on 2011-10-15
The 0.5 release of FFmpeg is quite old. The official FFmpeg response would be to use the latest available source code. See:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

However, just for testing purposes you can skip most of that guide and just do:
```
sudo apt-get update
sudo apt-get install build-essential libsdl1.2-dev yasm
cd
wget "http://git.videolan.org/?p=ffmpeg.git;a=snapshot;h=HEAD;sf=tgz" -O ffmpeg-HEAD-$(date +%Y%m%d%H%M%S).tar.gz
tar xzvf ffmpeg-HEAD*
cd ffmpeg-HEAD*
./configure --disable-doc
make
```
Now try this command:
```
glc-play rwi_0_25.linux-29991-0.glc -o - -y 1 | ./ffmpeg -i - -qscale 3 -y video.mp4
```
Then play the output with ffplay:
```
./ffplay video.mp4
```
Then play it with whatever other players you were using to rule out that it's a playback issue.

If everything works then there must be a fixed bug or addition to FFmpeg that deals with your issue. If it does not work then we can (probably) rule out your ancient version being at fault.

You can then follow the guide to get a more functional FFmpeg integrated into the package management system.

---

