---
title: "Is there a way to convert swf to video fairly easily?"
date: 2009-04-17
forum: Multimedia Software
---

### Post by kliljedahl on 2009-04-17
I have some older videos I would like to upload to You Tube, but they are no longer recognized if they are in swf format. All help is greatly appreciated in advance.

---

### Post by andrew.46 on 2009-04-18
Hi kliljedahl,

I will admit to not knowing much about the swf format but I spent a bit of time in the samples section of the MPlayer website and after a bit of a shock at the USA.swf files (don't ask!) I downloaded this one:

```
$ wget http://samples.mplayerhq.hu/SWF/zeldaADPCM2bit.swf
```

This is a pretty low-quality file but converts easily with FFmpeg, just ignore the encoding settings which I have just used for example:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]ffmpeg -i zeldaADPCM2bit.swf -acodec libmp3lame -ab 64k -vcodec mpeg4 -sameq test.mp4[/COLOR]**
FFmpeg version SVN-r18507, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --prefix=/usr --mandir=/usr/man --disable-debug 
--enable-shared --disable-static --enable-postproc --enable-avfilter 
--enable-pthreads --enable-libtheora --enable-libvorbis --enable-x11grab 
--enable-libmp3lame --enable-libx264 --enable-libschroedinger 
--enable-libfaac --enable-libfaad --enable-libamr-wb --enable-libamr-nb 
--enable-libgsm --enable-libspeex --enable-zlib --enable-nonfree --enable-gpl
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.25. 0 / 52.25. 0
  libavformat   52.32. 0 / 52.32. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    0. 5. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 14 2009 21:33:36, gcc: 4.2.4
Input #0, swf, from 'zeldaADPCM2bit.swf':
  Duration: N/A, start: 0.000000, bitrate: N/A
[B][COLOR="Red"]    Stream #0.0: Audio: adpcm_swf, 22050 Hz, mono, s16
    Stream #0.1: Video: flv, yuv420p, 160x120, 12 tbr, 12 tbn, 12 tbc[/COLOR][/B]
[mpeg4 @ 0x8071e50]removing common factors from framerate
Output #0, mp4, to 'test.mp4':
[B][COLOR="Red"]    Stream #0.0: Video: mpeg4, yuv420p, 160x120, q=2-31, 200 kb/s, 12 tbn, 12 tbc
    Stream #0.1: Audio: libmp3lame, 22050 Hz, mono, s16, 64 kb/s[/COLOR][/B]
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
Press [q] to stop encoding
frame=  358 fps=227 q=0.0 Lsize=    2306kB time=29.83 bitrate= 633.2kbits/s    
video:2060kB audio:233kB global headers:0kB muxing overhead 0.567316%

```

Looks easy enough in this example but I suspect all shockwave files are not created equal :-). If you are interested in following the FFmpeg path there are 2 guides well worth looking at:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

And BTW don't use my settings for youtube, that was just a quick demo :-).

All the best,

Andrew

---

### Post by ubuntu-freak on 2009-04-18
See if the multimedia howto in my sig helps.

---

