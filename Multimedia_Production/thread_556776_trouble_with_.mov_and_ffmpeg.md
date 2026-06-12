---
title: "trouble with .mov and ffmpeg"
date: 2007-09-21
forum: Multimedia Production
---

### Post by dbbolton on 2007-09-21
i'm trying to convert a mov file to an mpg. here what i tried, and the output:

```
ffmpeg -i '/home/daniel/Desktop/P1011401.MOV' out.mpg

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Jan 28 2007 22:48:38, gcc: 4.1.2 20070106 (prerelease) (Ubuntu 4.1.1-21ubuntu7)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/daniel/Desktop/P1011401.MOV':
  Duration: 00:05:57.5, start: 0.000000, bitrate: 2579 kb/s
  Stream #0.0(eng): Video: mjpeg, yuvj422p, 320x240, 15.00 fps(r)
  Stream #0.1(eng): Audio: pcm_u8, 7875 Hz, mono, 63 kb/s
Output #0, mpeg, to 'out.mpg':
  Stream #0.0: Video: mpeg1video, yuv420p, 320x240, q=2-31, 200 kb/s, 15.00 fps(c)
  Stream #0.1: Audio: mp2, 7875 Hz, mono, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mpeg1video @ 0xb7dea508]MPEG1/2 does not support 15/1 fps
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

```

any suggestions?

---

### Post by dbbolton on 2007-09-21
i guess it was the output as mpg that was causing the problem. i tried outputting to flv and it worked, but there is no sound. anyone know why?

---

### Post by lhtown on 2007-09-25
Try playing it with VLC player. If that doesn't work, get the lastest version of ffmpeg and the associated files from getdeb.net. It works for me.

---

### Post by dbbolton on 2007-09-25
well, i needed to compress the file size.

---

### Post by lhtown on 2007-09-25
Were you able to hear the sound when you tried it in VLC player?

---

### Post by dbbolton on 2007-09-25
> **lhtown said:**
> Were you able to hear the sound when you tried it in VLC player?
i caved and had my friend do it on his mac. thanks though :D

---

### Post by lhtown on 2007-10-05
I just wanted to follow up on this. I just upgraded to Gutsy beta and ffmpeg quit working. (when I convert from a .MOV file to .FLV, there is no sound.) It might work to install the version from getdeb, but it seems to be older than the version of ffmpeg that I have.

Basically, the problem seems to be that Ubuntu compiles ffmpeg without support for some codecs for legal reasons. However, if it is legal where you live, you can compile it with the codecs and support that you need.

For outdated directions, go to this page:
[https://wiki.ubuntu.com/ffmpeg](https://wiki.ubuntu.com/ffmpeg)

I followed the directions there, but I ran into a few problems. The main one was that the config options that are provided don't work properly with Gutsy.

```
./configure --enable-gpl --enable-pp --enable-zlib --enable-vorbis \ 
        --enable-libogg --enable-theora --enable-a52 --enable-dts \
        --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame \
        --enable-faad --enable-faac --enable-xvid
```

In the section you see above, you will have to prefix some of the options with "lib".  If you try running it, it will throw an error and for all of the ones that it throws an error, just back up and add "lib" before the command changing --enable-theora to --enable-libtheora and so forth.

There was also a dependency I had to install at one point, but I don't recall what it was. There were a couple of other hitches also, but basically, you get the idea.

It installed ffmpeg in /usr/local/bin/ instead of /usr/bin, so I just put a sim link to it for convenience so I don't have to type the entire path into the terminal every time.

---

### Post by Creative2 on 2007-10-06
i suggest to use mencoder.... (installed by medibuntu repo)

this can be a commandline to converter mov to mpeg or mpg =)

see the last post there

---

### Post by Creative2 on 2007-10-17
mm sorry mistake the right command line for mpeg is this =( so sorry for mistake 

mencoder -oac mp3lame  -lameopts abr:br=128 -srate 48000 -ovc lavc -lavcopts vcodec=mpeg1video:vbitrate=500 -vf scale=320:240 -ofps 25 -of mpeg -o OUTPUT.mpg INPUT

you can choose mpeg2video too like video codec

---

### Post by tminuszero on 2007-11-16
Thanks Creative2 - I forgot that my upgrade to gutsy had commented out the medibuntu source. Once I commented that and updated my system everything worked great in ffmpeg!

---

