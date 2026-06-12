---
title: "FFMPEG error"
date: 2007-12-20
forum: Multimedia Production
---

### Post by lsutiger on 2007-12-20
I am using ffmpeg to converty flv to mpg. It usually works, but I came across an error, which is speaking greek to me. Czn somebody explain in detail what this all means and what I need to do to correct it?

Here's the output:
```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Nov 17 2007 21:23:57, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 14.99 (15000/1001)
Input #0, flv, from 'mryxmas.flv':
  Duration: 00:05:46.0, start: 0.000000, bitrate: 56 kb/s
  Stream #0.0: Video: flv, yuv420p, 320x240, 14.99 fps(r)
  Stream #0.1: Audio: mp3, 22050 Hz, mono, 56 kb/s
Output #0, mpeg, to 'mryxmas.mpg':
  Stream #0.0: Video: mpeg1video, yuv420p, 320x240, q=2-31, 200 kb/s, 15.00 fps(c)
  Stream #0.1: Audio: mp2, 22050 Hz, mono, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mpeg1video @ 0xb7e6f3a8]MPEG1/2 does not support 15/1 fps
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

```

Thanx in advance!

---

### Post by yabbadabbadont on 2007-12-20
It is telling you that you need to specify a supported framerate for the output file as mpg does not support 15fps.

---

### Post by FakeOutdoorsman on 2007-12-20
What is the ffmpeg command you are using?

---

### Post by lsutiger on 2007-12-20
ffmpeg -s <inputfilename> <outputfilename>

> yabbadabbadont
Could you elaborate, AKA give instruction?
Thanx!

EDIT: I got it to avi.
But would like an explanation of the output, purely for learning reasons

---

### Post by yabbadabbadont on 2007-12-20
> **lsutiger said:**
> Could you elaborate, AKA give instruction?
Thanx!

Nope.  I never bother to run ffmpeg directly.  The only thing I can suggest, is to read the man page for ffmpeg.  "man ffmpeg"

---

### Post by lsutiger on 2007-12-20
> yabbadabbadont  
Done did dat!
lol
IMO man pages can sometimes be a bit noneducational. It gives you information but it is obviously not a tutorial. I did my google homework before posting, but anything video usually makes me confused. Sorry for the ignorance.

I am trying my best. I love Linux and to date have converted 2 hardcore MS users, so I am doing my part! :)

PS - What do you run for converting vids?

---

### Post by FakeOutdoorsman on 2007-12-21
> **lsutiger said:**
> IMO man pages can sometimes be a bit noneducational. It gives you information but it is obviously not a tutorial. I did my google homework before posting, but anything video usually makes me confused. Sorry for the ignorance.

ffmpeg documentation can be scarce and it doesn't help that the option names often change between versions every couple of months.  Also the mailing list isn't very beginner friendly.

Your command looks wrong because you're omitting the "-i".  Also the error states that your output codec doesn't support 15 fps.  Try this:

```
ffmpeg -i input.flv -sameq -r ntsc outputfile.mpeg
```

The -sameq tells it to make it the same quality as the original file, otherwise it will encode at the default settings which are low.  The -r is the frame rate, so you could say "ntsc" rate or 29.97 which is the same thing basically.

To answer your other question I still use ffmpeg to convert my videos.  It is very powerful but it takes time to learn.  Some ffmpeg gui or frontends include [thinliquidfilm]("http://thinliquidfilm.org/"), [VIVE]("http://sourceforge.net/projects/vive/"), [SIVE]("http://sourceforge.net/projects/sive/") (this might be for mencoder instead of ffmpeg), and [WinFF]("http://biggmatt.com/winff/") (for Linux).  Also see [Avidemux]("http://fixounet.free.fr/avidemux/").

---

### Post by lsutiger on 2007-12-21
> FakeOutdoorsman's Avatar  	
FakeOutdoorsman 
Thank you! May the God that you worship bring many good tidings to you! Thats the response I was waiting for!

Merry Christmas! or Kwanza! or Hannakah! Whatever you believe in!

Just Thank you!

---

### Post by willskills on 2007-12-21
> **FakeOutdoorsman said:**
> 

To answer your other question I still use ffmpeg to convert my videos.  It is very powerful but it takes time to learn.  Some ffmpeg gui or frontends include [thinliquidfilm]("http://thinliquidfilm.org/"), [VIVE]("http://sourceforge.net/projects/vive/"), [SIVE]("http://sourceforge.net/projects/sive/") (this might be for mencoder instead of ffmpeg), and [WinFF]("http://biggmatt.com/winff/") (for Linux).  Also see [Avidemux]("http://fixounet.free.fr/avidemux/").

It does indeed take a little time to learn, but, I also love ffmpeg. It's fantastic!

---

### Post by FakeOutdoorsman on 2007-12-21
> **lsutiger said:**
> Thats the response I was waiting for!

My example might work for you, but if you want I can come up with something better depending on your video source and what you're going to do with the final video.  I learn best from seeing examples.

---

### Post by mersinlii on 2007-12-22
> **lsutiger said:**
> I am using ffmpeg to converty flv to mpg. It usually works, but I came across an error, which is speaking greek to me. Czn somebody explain in detail what this all means and what I need to do to correct it?

Here's the output:
```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Nov 17 2007 21:23:57, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 14.99 (15000/1001)
Input #0, flv, from 'mryxmas.flv':
  Duration: 00:05:46.0, start: 0.000000, bitrate: 56 kb/s
  Stream #0.0: Video: flv, yuv420p, 320x240, 14.99 fps(r)
  Stream #0.1: Audio: mp3, 22050 Hz, mono, 56 kb/s
Output #0, mpeg, to 'mryxmas.mpg':
  Stream #0.0: Video: mpeg1video, yuv420p, 320x240, q=2-31, 200 kb/s, 15.00 fps(c)
  Stream #0.1: Audio: mp2, 22050 Hz, mono, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mpeg1video @ 0xb7e6f3a8]MPEG1/2 does not support 15/1 fps
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

```

Thanx in advance!:confused:

---

### Post by user17 on 2007-12-30
I get the same error from ffmpeg:

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 30.00 (30/1)

It still captures and outputs a nice video file, but there's no sound at all! An older version of ffmpeg on another laptop works perfectly, so I'm not sure what the problem is. Could it be that the problem ffmpeg is running on Gutsy? Could the rather annoying Mozilla Mediaplayerconnectivity be at fault?

---

### Post by DMurray on 2008-01-22
You are not the only one to have this problem.
I also see it when trying to encode videos downloaded from Youtube.

```

ffmpeg -i 6rrCGsecJrk.flv -ab 56 -ar 22050 -b 500 -s 320x240 video2.mpg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jun  3 2007 21:05:21, gcc: 4.1.3 20070528 (prerelease) (Ubuntu 4.1.2-9ubuntu2)

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 8.00 (8/1)
Input #0, flv, from '6rrCGsecJrk.flv':
  Duration: 00:02:13.7, start: 0.000000, bitrate: 8 kb/s
  Stream #0.0: Video: flv, yuv420p, 320x240,  8.00 fps(r)
  Stream #0.1: Audio: mp3, 22050 Hz, mono, 8 kb/s
File 'video2.mpg' already exists. Overwrite ? [y/N] y
Output #0, mpeg, to 'video2.mpg':
  Stream #0.0: Video: mpeg1video, yuv420p, 320x240, q=2-31, 0 kb/s, 10.00 fps(c)
  Stream #0.1: Audio: mp2, 22050 Hz, mono, 0 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mpeg1video @ 0x2ae676239e50]MPEG1/2 does not support 10/1 fps
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

```

This is the complete output after the command:
ffmpeg -i 6rrCGsecJrk.flv -ab 56 -ar 22050 -b 500 -s 320x240 video2.mpg

This very command line worked for another youtube file, but not for some other files.

---

### Post by Creative2 on 2008-01-22
... ehm...i have made fuoco tools to convert...see here 
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=652843](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=652843)

it has most of the command line....
anyway 

this is an exampple 
```

ffmpeg -i INPUT -r 25 -f mpeg -vcodec mpeg2video -ar 48000 -b 500k -acodec mp3 -ab 128k -s 320x240 -y OUTPUT
```

---

### Post by FakeOutdoorsman on 2008-01-22
DMurray,

You're almost there.  The ffmpeg error:
> [mpeg1video @ 0x2ae676239e50]MPEG1/2 does not support 10/1 fps

The error is saying that the mpeg codec doesn't support the framerate you are trying to encode at.  Your source video is encoded at 8 fps and ffmpeg is trying to ecode video2.mpg at 10 fps.  You can get it to work by adding a frame rate such as "-r ntsc" or "-r pal" or a number like "-r 29.97".

Try this:
```
ffmpeg -i 6rrCGsecJrk.flv -ab 56 -ar 22050 -b 500 -s 320x240 -r ntsc video2.mpg
```

---

### Post by Creative2 on 2008-01-23
> **FakeOutdoorsman said:**
> DMurray,

You're almost there.  The ffmpeg error:


The error is saying that the mpeg codec doesn't support the framerate you are trying to encode at.  Your source video is encoded at 8 fps and ffmpeg is trying to ecode video2.mpg at 10 fps.  You can get it to work by adding a frame rate such as "-r ntsc" or "-r pal" or a number like "-r 29.97".

Try this:
```
ffmpeg -i 6rrCGsecJrk.flv -ab 56 -ar 22050 -b 500 -s 320x240 -r ntsc video2.mpg
```

must use KKKKK :) new version of ffmpeg use 500k older 500 


```
ffmpeg -i 6rrCGsecJrk.flv -ab 56k -ar 22050 -b 500k -s 320x240 -r ntsc video2.mpg
```

---

### Post by DMurray on 2008-01-24
First of all, thanks for the replies.
I'd like to say that both solutions, by Creative2 and FakeOutdoorsman worked, but there was a notable file size difference between them. With 500k, the file was 9MB, while 500 resulted in 2.8MB. The -r ntsc was the trick.
Creative2, I will take a closer look at your software, looks quite interesting.
Thanks to both of you.

---

### Post by Creative2 on 2008-01-24
but there was a notable file size difference between them. With 500k, the file was 9MB, while 500 resulted in 2.8MB

this because  my command line uses 500 kbitrate 
instead the other uses 500 bitrate
so...

---

### Post by eye208 on 2008-01-24
> **Creative2 said:**
> this because  my command line uses 500 kbitrate 
instead the other uses 500 bitrate
so...
500 and 500K shouldn't make any difference. The file size was probably affected by something else. Might be worth investigating ...

---

### Post by Creative2 on 2008-01-24
i was in IRC with ffmpeg developer ...and he said that..so..i don't know but if you see ffmpeg man i think you should find out that thing

---

### Post by eye208 on 2008-01-24
It's in the man page indeed. What a stupid idea. This will probably break a lot of applications.

On the other hand, shouldn't a 500 kbit/s encode be 1024 times the size of a 500 bit/s one? ;)

---

