---
title: "Converting h264 to xbox-ready format"
date: 2009-04-05
forum: Multimedia Software
---

### Post by Visti on 2009-04-05
Anyway. I'm in a small pickle here - I have a bunch of videos that I can't play on my xbox (located on a USB harddrive). They play fine on my computer, so it's the codec that's wacky. I run a quick check in my trusty VLC and this is the information I get:

Stream 1 : Video
Codec: h264
Framerate: 24.7
Resolution:  768x432

Stream 2: Audio
Codec: mpga
Channels: 2
Bitrate: 135 kb/s

So yeah, it's basically a h264 video file, I haven't encountered them much, so I don't know a lot about it and, for once, I didn't encode the file myself. Now, I do a little google search and it seems ffmpeg should be able to decode it, so first I do a 'ffmpeg -formats' and sure enough, h264 and a few other h* are in there. Additionally, I also find a command posted on a forum, which should convert h264 files into files playable on the xbox. I then turned it into this script:

for vid in *.avi; do ffmpeg -y -i "$vid" -vcodec h264 -b 1000000 -acodec aac -ar 48000 -ab 160 -f mov "${vid%%avi}"mov; done;

This is the output I get:

```
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:48:10, gcc: 4.3.2
Input #0, avi, from '3x01 - Shadowman 9 (InThe Cradle of Destiny).avi':
  Duration: 00:23:39.3, start: 0.000000, bitrate: 1151 kb/s
    Stream #0.0: Video: h264, yuv420p, 768x432 [PAR 81:256 DAR 9:16], 23.98 tb(r)
    Stream #0.1: Audio: mp3, 44100 Hz, stereo, 32 kb/s
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
Unknown encoder 'h264'

```

And now I'm just confused. Is there an easier way to go about this, keeping in mind that I do have an entire folder of it and it would be neat to just point a script at it and have it work for a while.

---

