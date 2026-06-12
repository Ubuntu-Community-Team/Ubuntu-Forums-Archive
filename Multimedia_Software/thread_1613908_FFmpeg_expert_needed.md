---
title: "FFmpeg expert needed"
date: 2010-11-05
forum: Multimedia Software
---

### Post by nickTaylor1181 on 2010-11-05
Hello.

I'm trying to use ffmpeg to clip off bits of chaff from h.264 clips - from a Canon T2i / EOS 550

I'm trying to use this

ffmpeg -ss 00:00:23 -i input.MOV -t 10 -r 23.98 -vcodec copy -acodec copy hai.MOV

and it dutifully prduces the clipped clip... but the sound is out of sync... and it's giving me an error message 
> 
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 23 2010 15:38:06, gcc: 4.4.1

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (48000/1001) -> 23.98 (24000/1001)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'MVI_3342.MOV':
  Duration: 00:04:03.03, start: 0.000000, bitrate: 45605 kb/s
    Stream #0.0(eng): Video: h264, yuv420p, 1920x1080, 23.98 tbr, 23.98 tbn, 47.95 tbc
    Stream #0.1(eng): Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s
Output #0, mov, to 'hai.MOV':
    Stream #0.0(eng): Video: libx264, yuv420p, 1920x1080, q=2-31, 90k tbn, 23.98 tbc
    Stream #0.1(eng): Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame=  240 fps=  0 q=-1.0 Lsize=   56040kB time=9.55 bitrate=48065.0kbits/s    
video:53972kB audio:2065kB global headers:0kB muxing overhead 0.005591%



I've been told by... the internet that "The error is saying that the codec doesn't support the framerate you are trying to encode at" ( [http://ubuntuforums.org/archive/index.php/t-646028.html](http://ubuntuforums.org/archive/index.php/t-646028.html) )

But none of the solutions on that page make any difference.


Any ideas?

---

### Post by nowardev on 2010-11-05
> **nickTaylor1181 said:**
> Hello.

I'm trying to use ffmpeg to clip off bits of chaff from h.264 clips - from a Canon T2i / EOS 550

I'm trying to use this

ffmpeg -ss 00:00:23 -i input.MOV -t 10 -r 23.98 -vcodec copy -acodec copy hai.MOV

and it dutifully prduces the clipped clip... but the sound is out of sync... and it's giving me an error message 


I've been told by... the internet that "The error is saying that the codec doesn't support the framerate you are trying to encode at" ( [http://ubuntuforums.org/archive/index.php/t-646028.html](http://ubuntuforums.org/archive/index.php/t-646028.html) )

But none of the solutions on that page make any difference.


Any ideas?


ffmpeg -i INPUTFILE  2>&1 | grep Stream

give me the output

---

### Post by FakeOutdoorsman on 2010-11-05
> **nickTaylor1181 said:**
> 
I'm trying to use this
```
ffmpeg -ss 00:00:23 -i input.MOV -t 10 -r 23.98 -vcodec copy -acodec copy hai.MOV
```
... but the sound is out of sync
The *-r* option is not compatible with the *-vcodec copy* option, so therefore *-r 23.98* is being ignored.  If you want to change the frame rate then you must re-encode.  Sometimes you need to move the *-ss* option after the *-i*, as in:
```
ffmpeg -i input.MOV -ss 23 -t 10 -vcodec copy -acodec copy hai.MOV
```
Does that resolve the audio sync issue?  If not, then I suggest trying a more recent FFmpeg:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

> **nickTaylor1181 said:**
> ... and it's giving me an error message
What's the error message?

---

### Post by nickTaylor1181 on 2010-11-05
@nowardev 

Stream #0.0(eng): Video: h264, yuv420p, 1920x1080, 23.98 tbr, 23.98 tbn, 47.95 tbc
Stream #0.1(eng): Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s



@FakeOutdoorsman

Ah - that makes sense... 

...the error message was the bit that said "Seems stream 0 codec frame rate differs from container frame rate: 47.95 (48000/1001) -> 23.98 (24000/1001)" in my first post. More a warning than an error

What I'm trying to do is reproduce the clip... without any quality loss, but with bits edited out - it's not uncommon to have 20 secs of greatness in a 2 minute clip. So I'd like a way of trimming all but the 20 seconds.

That was the reason I wasn't re-encoding... do you know of a way of re-encoding (rather than copying) without a loss in quality?

---

### Post by FakeOutdoorsman on 2010-11-05
> **nickTaylor1181 said:**
> That was the reason I wasn't re-encoding... do you know of a way of re-encoding (rather than copying) without a loss in quality?

Did my example command not work for you?  You can re-encode to a "lossless" format such as lossless x264, ffv1, or huffyuv. These will usually give lossless results (color space conversion can cause some "loss") but the output file sized can be very large.

---

### Post by nickTaylor1181 on 2010-11-05
LOL - sorry... just give me a minute or two while I teach myself to read again.


Yes, that worked perfectly - thank you from Sunny New Zealand. :)

---

