---
title: "ffmpeg problem: mkv to 3gp conversion"
date: 2009-07-22
forum: Multimedia Software
---

### Post by abhigyan91 on 2009-07-22
hey all, i was trying to convert a mkv video file to 3gp for my cell phone using:

```

ffmpeg -r 24 -i '/home/abhigyan/Desktop/source/Nickelback - If Today Was Your Last Day.mkv' -f 3gp -r 24 -vcodec h263 -acodec libmp3lame -s qcif out.3gp



```

and it gave me the following output.. i have tried tweeking with the bitrate and fps etc but still same prob.. plz help!!

> 
abhigyan@abhigyan-laptop:~$ ffmpeg -r 24 -i '/home/abhigyan/Desktop/source/Nickelback - If Today Was Your Last Day.mkv' -f 3gp -r 24 -vcodec h263 -acodec libmp3lame -s qcif out.3gp
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:48:10, gcc: 4.3.2
[matroska @ 0xb7fff4c8]Ignoring seekhead entry for ID=0x1549a966
[matroska @ 0xb7fff4c8]Ignoring seekhead entry for ID=0x1654ae6b
[matroska @ 0xb7fff4c8]Ignoring seekhead entry for ID=0x114d9b74
[matroska @ 0xb7fff4c8]Unknown entry 0x73a4 in info header
[matroska @ 0xb7fff4c8]Unknown track header entry 0x55aa - ignoring
[matroska @ 0xb7fff4c8]Unknown track header entry 0x23314f - ignoring
[matroska @ 0xb7fff4c8]Unknown track header entry 0x55ee - ignoring
[matroska @ 0xb7fff4c8]Unknown track header entry 0xaa - ignoring
[matroska @ 0xb7fff4c8]Unknown track header entry 0x55aa - ignoring
[matroska @ 0xb7fff4c8]Unknown track header entry 0x23314f - ignoring
[matroska @ 0xb7fff4c8]Unknown track header entry 0x55ee - ignoring
[matroska @ 0xb7fff4c8]Unknown track header entry 0xaa - ignoring
Input #0, matroska, from '/home/abhigyan/Desktop/source/Nickelback - If Today Was Your Last Day.mkv':
  Duration: 00:04:08.6, start: 0.000000, bitrate: N/A
    Stream #0.0(eng): Video: h264, yuv420p, 544x336 [PAR 142:125 DAR 4828:2625], 23.98 tb(r)
    Stream #0.1: Audio: mp3, 44100 Hz, stereo
File 'out.3gp' already exists. Overwrite ? [y/N] y
Output #0, 3gp, to 'out.3gp':
    Stream #0.0(eng): Video: h263, yuv420p, 176x144 [PAR 155:103 DAR 1705:927], q=2-31, 200 kb/s, 24.00 tb(c)
    Stream #0.1: Audio: libmp3lame, 44100 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[B][3gp @ 0xb7fff4c8]track 1: could not find tag for codec
Could not write header for output file #0 (incorrect codec parameters ?)[/B]


plz tell me what the bold text means..thx in adv

---

### Post by FakeOutdoorsman on 2009-07-22
> **abhigyan91 said:**
> plz tell me what the bold text means..thx in adv

This FFmpeg error could fail more gracefully and be more useful to regular users.  MP3 is not a valid audio format for 3GP.  Try AAC or AMR.  Check out the [Comparison of container formats](http://en.wikipedia.org/wiki/Comparison_of_container_formats) for more info on what 3GP can handle.  Untested example:

```
ffmpeg -i input -vcodec h263 -acodec libfaac -s qcif out.3gp
```

---

### Post by abhigyan91 on 2009-07-23
ok it worked when i used libfaac but the vidoe stream is too slow compared to the audio stream... this particular input file is 24fps(i checked using nautilus).. but when i do it with a vid of 25fps(the default fps for ffmpeg), it converts normally. Is there any way to specify fps for the input file because i  think the problem is ffmpeg can;t recogize the input fps.

I tried putting -r 24 in fornt of -i filename as you can see above but it still does not give proper results:(

---

