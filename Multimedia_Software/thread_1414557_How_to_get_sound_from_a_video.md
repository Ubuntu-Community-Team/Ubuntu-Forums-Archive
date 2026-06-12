---
title: "How to get sound from a video"
date: 2010-02-23
forum: Multimedia Software
---

### Post by Weepleman on 2010-02-23
Hi, when I download a video, and want to get the sound from it, I have to convert the .flv to a .m4v in handbrake, and then save the audio from that in avidemux.  Is there any way to speed this up, because handbrake is very slow, and you can't do this in batch for either one, thank you. :)

---

### Post by Jose Catre-Vandis on 2010-02-23
Try

```
ffmpeg -i <input> -vn <output>
```

more detailed:

```
ffmpeg -i input.flv -vn -acodec libmp3lame -ac 2 -ab 128k output.mp3
```

the -vn options tells ffmpeg "no video"

---

### Post by Weepleman on 2010-02-23
I got this 
```
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.92 (359/12)
Input #0, flv, from 'YouTube_-_Black_Hole_Disco_Karaoke_(low_resolution).flv':
  Duration: 00:01:54.34, start: 0.000000, bitrate: 216 kb/s
    Stream #0.0: Video: flv, yuv420p, 146x112, 208 kb/s, 29.92 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, stereo, s16, 8 kb/s
Output #0, mp3, to 'Black-Hole-Disco.mp3':
    Stream #0.0: Audio: 0x0000, 22050 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Unsupported codec for output stream #0.0

```
and a mp3 file of 0 bytes, and the other option said unknown encoder libmp3lame, and then I tried to apt-get the library, and it could not find package.

---

### Post by mc4man on 2010-02-23
Just use ffmpeg to copy the audio, in this case mp3

So.. (replace blue
```
ffmpeg -i [COLOR="Blue"]/path/to/filename[/COLOR] -vn -acodec copy [COLOR="Blue"]output_name[/COLOR].mp3
```

Ex. of your flv from youtube
> 
doug@doug-desktop:~$ ffmpeg -i /tmp/FlashAi3sit -vn -acodec copy bh.mp3
FFmpeg version SVN-r22013, Copyright (c) 2000-2010 the FFmpeg developers
  built on Feb 23 2010 21:12:18 with gcc 4.4.1
  configuration: --extra-cflags='-Wall -g ' --enable-gpl --enable-version3 --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab --disable-vdpau --enable-postproc --enable-libopenjpeg --enable-libvorbis --enable-pthreads --enable-libspeex
  libavutil     50. 9. 0 / 50. 9. 0
  libavcodec    52.55. 0 / 52.55. 0
  libavformat   52.54. 0 / 52.54. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0.10. 0 /  0.10. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[flv @ 0xa21f3a0]Estimating duration from bitrate, this may be inaccurate

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.92 (359/12)
Input #0, flv, from '/tmp/FlashAi3sit':
  Metadata:
    duration        : 114
    starttime       : 0
    totalduration   : 114
    width           : 146
    height          : 112
    videodatarate   : 204
    audiodatarate   : 47
    totaldatarate   : 259
    framerate       : 30
    bytelength      : 3705542
    canseekontime   : true
    sourcedata      : B4A7D0083MM
    purl            : 
    pmsg            : 
  Duration: 00:01:54.34, start: 0.000000, bitrate: 216 kb/s
    Stream #0.0: Video: flv, yuv420p, 146x112, 208 kb/s, 29.92 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, 2 channels, s16, 8 kb/s
Output #0, mp3, to 'bh.mp3':
  Metadata:
    TSSE            : Lavf52.54.0
    Stream #0.0: Audio: libmp3lame, 22050 Hz, 2 channels, 8 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Press [q] to stop encoding
size=     652kB time=114.39 bitrate=  46.7kbits/s    
video:0kB audio:652kB global headers:0kB muxing overhead 0.004942%


---

### Post by Weepleman on 2010-02-24
That made a mp3 that was the right size and length, but it was all repeating and stuff, like it would play a few words, and then play it again.  It sounded like people singing in a round.
--------------------------------------------------------------------------------------------------------------------------------------
Sorry, that was just a problem with movie player.  It works fine in VLC.  Thank you very much for your help!

---

