---
title: "ffmpeg .flv conversion"
date: 2009-03-19
forum: Multimedia Software
---

### Post by superposition on 2009-03-19
I am trying to convert some .flv to another format preferable mpeg4 however I have not been able to make it work I have ran ffmpeg - formats and flv is listed here is how I tried 
> 
fermeon@positron:~/Downloads$ ffmpeg -i video.flv video.mp4
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:48:10, gcc: 4.3.2
video.flv: Unknown format

what is wrong?
Is there a better way?
Thanks in advance for any help.

---

### Post by andrew.46 on 2009-03-19
Hi,

Can you post the *full *results of the following:

```
ffmpeg -i video.flv
```

This should give a few more details about the file itself.

All the best,

Andrew

---

### Post by superposition on 2009-03-21
Full Results are as follows
> 
fermeon@positron:~/Downloads$ ffmpeg -i video.flv
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:48:10, gcc: 4.3.2
video.flv: Unknown format
fermeon@positron:~/Downloads$ 


---

### Post by andrew.46 on 2009-03-21
Hi,

Seems a bit odd, especially if flv is listed in your -formats list. If nobody else has an idea can you post this file somewhere? BTW is your copy of FFmpeg a straight repository version or have you rebuilt it?

Andrew

---

### Post by mc4man on 2009-03-22
you could ck. with mediainfo and see what it says.

[http://www.getdeb.net/search.php?keywords=mediainfo](http://www.getdeb.net/search.php?keywords=mediainfo)

If so dl, install the 3 packages from right to left

---

### Post by FakeOutdoorsman on 2009-03-22
> **superposition said:**
> I am trying to convert some .flv to another format preferable mpeg4 however I have not been able to make it work I have ran ffmpeg
Is video.flv corrupt?  Are you able to view or play the video?  Where and how did you acquire this file?  I'm guessing that video.flv is corrupt because FFmpeg should be able to deal with this with no issues.

---

### Post by superposition on 2009-03-23
Ah yes, corruption was the culprit here. Can't believe I didn't think of that:(. Thanks for everyones help

---

### Post by Dr.Dixie on 2009-03-24
I basically want to do the same thing, but I don't know how to make ffmpeg output, and, considering the monsterlist of commands it has, I figured I'd try looking here and (hopefully) save myself some time.
Basically what I want to do is to know how to convert any size Youtube video (320x240, 640x480?, and 1280x768?) into a size that can fit on a screen 220x176 in MPG format in the highest quality I can manage, from such a low-quality source. (I want to be able to load videos onto my Sansa e280, and that's what Rockbox can use.)

Thanks,

*EDIT*

Ok. I figured out how to do the transcoding stuff, but now I need to know how to make it not mess up the audio. I tried doing a video over an hour and a half long, and it slowly, or incrementally, ends up playing the audio several seconds before the video it's meant to be with. How am I supposed to fix this?
Here's the code, if you need it...

```
ffmpeg -i inconnw1-01.ogv -s 220x104 01-TheIncredibles-WIDE.mpg
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:48:10, gcc: 4.3.2
[theora @ 0xb7e172f0]Theora bitstream version 30201
[theora @ 0xb7e172f0]344 bits left in packet 81
[theora @ 0xb7e172f0]7 bits left in packet 82
Input #0, ogg, from 'inconnw1-01.ogv':
  Duration: 01:37:20.5, start: 0.000000, bitrate: 2183 kb/s
    Stream #0.0: Video: theora, yuv420p, 720x356 [PAR 32:27 DAR 640:267], 29.97 tb(r)
    Stream #0.1: Audio: vorbis, 44100 Hz, stereo, 128 kb/s
Output #0, mpeg, to '01-TheIncredibles-WIDE.mpg':
    Stream #0.0: Video: mpeg1video, yuv420p, 220x104 [PAR 247:218 DAR 1045:436], q=2-31, 200 kb/s, 29.97 tb(c)
    Stream #0.1: Audio: mp2, 44100 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[theora @ 0xb7e172f0]Theora bitstream version 30201
[theora @ 0xb7e172f0]344 bits left in packet 81
[theora @ 0xb7e172f0]7 bits left in packet 82
Press [q] to stop encoding
[mpeg1video @ 0xb7e172f0]warning, clipping 1 dct coefficients to -255..255s     
[mpeg1video @ 0xb7e172f0]warning, clipping 1 dct coefficients to -255..255s     
[mpeg1video @ 0xb7e172f0]warning, clipping 1 dct coefficients to -255..255
[mpeg1video @ 0xb7e172f0]warning, clipping 1 dct coefficients to -255..255/s     
[mpeg1video @ 0xb7e172f0]warning, clipping 1 dct coefficients to -255..255
[mpeg1video @ 0xb7e172f0]warning, clipping 1 dct coefficients to -255..255
[mpeg1video @ 0xb7e172f0]warning, clipping 1 dct coefficients to -255..255
[mpeg1video @ 0xb7e172f0]warning, clipping 1 dct coefficients to -255..255
[mpeg1video @ 0xb7e172f0]warning, clipping 1 dct coefficients to -255..255
[mpeg1video @ 0xb7e172f0]warning, clipping 1 dct coefficients to -255..255
frame=176182 fps= 60 q=2.0 Lsize=  191230kB time=5839.3 bitrate= 268.3kbits/s    
video:142350kB audio:45619kB global headers:0kB muxing overhead 1.734645%
```

What's going wrong?

*EDIT* It seems I've found the solution. I think it was actually the video that was slowing down, and that because of video settings on my Sansa. Thanks for...uh...no help? Anyway.


!Dr. Dixie!

---

