---
title: "stream to Icecast2"
date: 2010-11-28
forum: Multimedia Software
---

### Post by rocker2344 on 2010-11-28
I have tried Webcamstudio and theour. none work for me. 
but theour got me close, i grabed the command and started to go through it
what i have so far
```
padsp ffmpeg -f video4linux2 -i /dev/video0 -f oss -i /dev/dsp -ac 1 - | ffmpeg2theora -H 22050 -a 0 -v 2 -x 320 -y 240 -F 15 -K 60 -c 1  -o /dev/stdout - | tee /home/rocker2344/test | oggfwd -p -d "" -g "" -n "" -u "" 192.168.1.129 8000 hackme /video.ogg 
```
and this is my output
```
FFmpeg version 0.6-4:0.6-2ubuntu6, Copyright (c) 2000-2010 the FFmpeg developers
  built on Oct  5 2010 22:36:53 with gcc 4.4.5
  configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
oggfwd: Connected to server
[video4linux2 @ 0x138f420]Estimating duration from bitrate, this may be inaccurate
Input #0, video4linux2, from '/dev/video0':
  Duration: N/A, start: 69972.599766, bitrate: -2147483 kb/s
    Stream #0.0: Video: rawvideo, yuyv422, 640x480, -2147483 kb/s, 1000k tbr, 1000k tbn, 1000k tbc
[oss @ 0x1390cd0]Estimating duration from bitrate, this may be inaccurate
Input #1, oss, from '/dev/dsp':
  Duration: N/A, start: 1290974198.835231, bitrate: N/A
    Stream #1.0: Audio: pcm_s16le, 44100 Hz, 1 channels, s16, 705 kb/s
Unable to find a suitable output format for 'pipe:'
ioctl(VIDIOC_QBUF)

File `pipe:' does not exist or has an unknown data format.
oggfwd: Quitting ...
oggfwd: Total bytes read: 0
```

What am i missing?

---

### Post by roelforg on 2011-12-28
In my efforts i found the solution:
the first ffmpeg should be like this:
```

ffmpeg -f alsa -i pulse test.mp3

```
to output the input on your input to the file test.mp3.
Press CTRL-C to end.

---

