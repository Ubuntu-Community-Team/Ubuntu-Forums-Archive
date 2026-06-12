---
title: "ffmpeg and how to convert video to Nokias 5800 phone format"
date: 2011-07-31
forum: Multimedia Software
---

### Post by cpcpcp on 2011-07-31
[SIZE=2][COLOR=DarkGreen]Has anyone figured out the command line option in ffmpeg to do this and will they please tell me as I am finding it all very frustrating.

I am told I need the output file to comply with this[/COLOR][/SIZE]
Video Resolution: 480*320
Video Bitrate: 768 kbps
Audio Bitrate: 128 kbps
Video Format: MPEG-4 (be sure not to use H264, as it’s not supported in the current firmware)
Audio Format: MP3
Audio Channels: 2 Channels 

[SIZE=2][COLOR=DarkGreen]Alternatively it the phone will reportedly support
[/COLOR][/SIZE][SIZE=2][COLOR=DarkGreen]3GPP formats (H.263)
Flash Video
H.264/AVC
MPEG-4
RealVideo 7,8,9/10
WMV 9[/COLOR][/SIZE]


[SIZE=2][COLOR=DarkGreen]the starting file is Arthur.mkv
and this is just one of my many attempts that does not work![/COLOR][/SIZE]
ffmpeg -i /home/cjp/Desktop/Arthur.mkv -r 15 -b 200kbit/s -s 176x144 -vcodec h263 -ar 8000 -ab 10.2k go.3gp

```
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1.1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar 31 2011 18:53:20, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (48000/1001) -> 23.98 (24000/1001)
Input #0, matroska, from '/home/cjp/Desktop/Arthur.mkv':
  Duration: 01:49:59.72, start: 0.000000, bitrate: N/A
    Stream #0.0(eng): Video: h264, yuv420p, 1280x720, PAR 1:1 DAR 16:9, 23.98 tbr, 1k tbn, 47.95 tbc
    Stream #0.1: Audio: aac, 24000 Hz, stereo, s16
    Stream #0.2: Subtitle: 0x0000
Output #0, 3gp, to 'go2.3gp':
    Stream #0.0(eng): Video: h263, yuv420p, 176x144 [PAR 16:11 DAR 16:9], q=2-31, 200 kb/s, 90k tbn, 15 tbc
    Stream #0.1: Audio: libopencore_amrnb, 8000 Hz, stereo, s16, 10 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[libopencore_amrnb @ 0x876baf0]Only mono supported
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height

```[SIZE=2][COLOR=DarkGreen]ffmeg is very clever but it has me beat
[/COLOR][/SIZE]
Chris

---

### Post by FakeOutdoorsman on 2011-08-01
> **cpcpcp said:**
> ```
[libopencore_amrnb @ 0x876baf0]Only mono supported
```

You almost got it. You need mono audio (-ac 1):
```
ffmpeg -i /home/cjp/Desktop/Arthur.mkv -r 15 -b 200kbit/s -s 176x144 -vcodec h263 -ar 8000 -ab 10.2k go.3gp
```

---

### Post by cpcpcp on 2011-08-01
> **FakeOutdoorsman said:**
> You almost got it. You need mono audio (-ac 1):
```
ffmpeg -i /home/cjp/Desktop/Arthur.mkv -r 15 -b 200kbit/s -s 176x144 -vcodec h263 -ar 8000 -ab 10.2k go.3gp
```

[SIZE=2][COLOR=DarkGreen]So close huh?

But at the moment, as you know, I have no ffmpeg at present to try again.

I did post the question on getting the latest version of ffmpeg where you asked and all it pulled up was a comment from Ron999[/COLOR][/SIZE] that 
"You're in the wrong place pal.
Put some effort into your original thread and you might get a response".

[SIZE=2][COLOR=DarkGreen]and he referred me back here which was kind of amusing.[/COLOR][/SIZE]

---

### Post by FakeOutdoorsman on 2011-08-01
My example should work with the repo FFmpeg.

---

