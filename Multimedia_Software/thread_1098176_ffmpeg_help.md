---
title: "ffmpeg help"
date: 2009-03-16
forum: Multimedia Software
---

### Post by cdmike2k8 on 2009-03-16
I am running a server, and I want to use it to convert videos.  I installed ffmpeg and mencoder, although I believe I still need all the encoders/codecs.  I am getting the error: : Unknown encoder 'mpeg2video' How would I go about getting them?  It is ubuntu 8.10 server, by the way.

---

### Post by inobe on 2009-03-16
i made a howto, you can change the outputs and unputs or tweak anything to work the way you want it to.

[http://ubuntuforums.org/showthread.php?t=1092106](http://ubuntuforums.org/showthread.php?t=1092106)

or you can scroll down and check out the links we posted....


you still need to install the list of stuff for things to work as they should.

handbrake is also an option with the list of stuff i mentioned.

actuall just forget handbrake considering you have no GUI

edit: skip the nautilus stuff too !

---

### Post by cdmike2k8 on 2009-03-16
Thanks, that seemed to get it going.  I was not able to install ubuntu-restricted-extras as it wants to install a gui.  With the listed packages in the guide, would I be able to do a .mkv?

---

### Post by inobe on 2009-03-16
yes' i never tried output' input went well...


leave out the restricted stuff if its working .

edit: keep this for reference [http://www.ffmpeg.org/documentation.html](http://www.ffmpeg.org/documentation.html)

the docs will explain some things' especially matroska

---

### Post by inobe on 2009-03-16
output for mkv works.........

edit: the complete video doesn't have audio, i will need to try some things to find out why.


for reference i will paste the results

```
desktop:~/Videos$ ffmpeg -i beyonce.mpeg -vcodec libx264 -s 480x320 -r 24  -b 100k -acodec libfaac -ac 2 -ar 32000 -ab 128k -qscale 1 beyonces.mkv
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Input #0, mpeg, from 'beyonce.mpeg':
  Duration: 00:03:23.6, start: 0.236800, bitrate: 1947 kb/s
    Stream #0.0[0x1e0]: Video: mpeg1video, yuv420p, 352x240 [PAR 200:219 DAR 880:657], 104857 kb/s, 29.97 tb(r)
    Stream #0.1[0x1c0]: Audio: mp2, 44100 Hz, stereo, 224 kb/s
Output #0, matroska, to 'beyonces.mkv':
    Stream #0.0: Video: libx264, yuv420p, 480x320 [PAR 217:243 DAR 217:162], q=2-31, 100 kb/s, 24.00 tb(c)
    Stream #0.1: Audio: libfaac, 32000 Hz, stereo, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[libx264 @ 0xb7e1f2f0]using SAR=217/243
[libx264 @ 0xb7e1f2f0]using cpu capabilities: MMX MMXEXT SSE SSE2 SSE3 Cache64 
[matroska @ 0xb7fa3388]No AAC extradata, unable to determine samplerate.
Press [q] to stop encoding
frame= 4889 fps= 25 q=-7672591.2 Lsize=   16932kB time=203.6 bitrate= 681.4kbits/s    
video:14118kB audio:2729kB global headers:0kB muxing overhead 0.506419%
[libx264 @ 0xb7e1f2f0]slice I:408   Avg QP:27.83  size:  6043
[libx264 @ 0xb7e1f2f0]slice P:4481  Avg QP:29.77  size:  2672
[libx264 @ 0xb7e1f2f0]mb I  I16..4: 50.2%  0.0% 49.8%
[libx264 @ 0xb7e1f2f0]mb P  I16..4: 14.3%  0.0%  0.0%  P16..4: 38.1%  0.0%  0.0%  0.0%  0.0%    skip:47.6%
[libx264 @ 0xb7e1f2f0]final ratefactor: -27.71
[libx264 @ 0xb7e1f2f0]SSIM Mean Y:0.9656078
[libx264 @ 0xb7e1f2f0]kb/s:567.1

```

---

### Post by FakeOutdoorsman on 2009-03-16
> **cdmike2k8 said:**
> I am running a server, and I want to use it to convert videos.  I installed ffmpeg and mencoder, although I believe I still need all the encoders/codecs.  I am getting the error: : Unknown encoder 'mpeg2video' How would I go about getting them?  It is ubuntu 8.10 server, by the way.
If you're going to do some serious encoding, especially H.264, then I recommend compiling FFmpeg since the revision from the repository is quite dated:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by inobe on 2009-03-16
being the ffmpeg newbie' i also appreciate the valuable information.

thank you FakeOutdoorsman :)

---

### Post by FakeOutdoorsman on 2009-03-17
> **inobe said:**
> being the ffmpeg newbie' i also appreciate the valuable information.

thank you FakeOutdoorsman :)
For a self-proclaimed FFmpeg newbie you are giving good suggestions.  I'm still learning too.

---

