---
title: "[SOLVED] ffmpeg convert .avi to .mpg error"
date: 2008-11-18
forum: Multimedia Software
---

### Post by jmd9qs on 2008-11-18
hi, im trying to convert an .avi movie to .mpg so i can use dvdauthor and then burn it to a dvdplayer compatible dvd. i just upgraded from Hardy Heron to Intrepid and before this, ffmpeg worked wonderfully. now it doens't work at all.... here is the code and error i get:

```
ffmpeg -i movie.avi -target dvd /media/disk/SAFE/movie.mpg
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Input #0, avi, from 'movie.avi':
  Duration: 01:32:15.2, start: 0.000000, bitrate: 1063 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 692x284 [PAR 1:1 DAR 173:71], 23.98 tb(r)
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, 128 kb/s
Assuming NTSC for target.
Unknown encoder 'mpeg2video'
```

how can i fix this?

---

### Post by Ng Oon-Ee on 2008-11-18
In Intrepid (as in previous versions) the ffmpeg shipped in the repos is gimped to be totally legal. Which basically means many of the more popular formats (such as MP3 and, as you've seen, many video formats) are not supported. In previous versions, a relatively recent and ungimped ffmpeg was provided in the Medibuntu repos, but for Intrepid it has not yet been placed in the repo. Some speculate it may not be in the pipeline.

I'd suggest following [this HOWTO]("http://ubuntuforums.org/showthread.php?t=786095") to compile your own ffmpeg. I've contributed a bit more to the process, on page 22 I believe, but the thread starter's HOWTO will do everything you need.

HINT: Google is your friend with errors like this.

---

### Post by FakeOutdoorsman on 2008-11-18
The Ubuntu multiverse repository has "unstripped" libraries available and should provide mpeg2video encoding ability (and many others) to ffmpeg:
```
sudo apt-get purge ffmpeg
sudo apt-get update
sudo apt-get install libavcodec-unstripped-51 libavdevice-unstripped-52 libavformat-unstripped-52 libavutil-unstripped-49 libpostproc-unstripped-51 libswscale-unstripped-0 ffmpeg
```
Or, as Ng Oon-Ee mentioned, you can compile the latest ffmpeg yourself.

---

### Post by Ng Oon-Ee on 2008-11-18
> **FakeOutdoorsman said:**
> The Ubuntu multiverse repository has "unstripped" libraries available and should provide mpeg2video encoding ability (and many others) to ffmpeg:
```
sudo apt-get purge ffmpeg
sudo apt-get update
sudo apt-get install libavcodec-unstripped-51 libavdevice-unstripped-52 libavformat-unstripped-52 libavutil-unstripped-49 libpostproc-unstripped-51 libswscale-unstripped-0 ffmpeg
```
Or, as Ng Oon-Ee mentioned, you can compile the latest ffmpeg yourself.

Ah, I saw that on another thread, but never worked with me. Nobody mentioned the need to purge ffmpeg prior to installing the unstripped though. Oh well, I now have the latest ffmpeg compiled and running thanks to you, good sir, so its all good :)

---

### Post by ich.zazen on 2009-06-16
Yes, Yes, Yes, it works a lot!
Thank you very much.

---

### Post by alecz20 on 2010-07-23
> **FakeOutdoorsman said:**
> The Ubuntu multiverse repository has "unstripped" libraries available and should provide mpeg2video encoding ability (and many others) to ffmpeg:
```
sudo apt-get purge ffmpeg
sudo apt-get update
sudo apt-get install libavcodec-unstripped-51 libavdevice-unstripped-52 libavformat-unstripped-52 libavutil-unstripped-49 libpostproc-unstripped-51 libswscale-unstripped-0 ffmpeg
```
Or, as Ng Oon-Ee mentioned, you can compile the latest ffmpeg yourself.

I am getting:
```

E: Couldn't find package libavcodec-unstripped-51

```

---

### Post by FakeOutdoorsman on 2010-07-23
> **alecz20 said:**
> I am getting:
```

E: Couldn't find package libavcodec-unstripped-51

```

My last post on this tread was from 2008 and this command is targeted towards Ubuntu Intrepid Ibex 8.10.  See this thread:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by alecz20 on 2010-07-23
> **FakeOutdoorsman said:**
> My last post on this tread was from 2008 and this command is targeted towards Ubuntu Intrepid Ibex 8.10.  See this thread:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

Thanks alot for the very quick reply!

I eventually installed ffmpeg from source, and it all works well, except it complains about threads option.

Do I really need two threads on a core 2 Duo when transcoding HD movies on the fly?

---

### Post by FakeOutdoorsman on 2010-07-23
> **alecz20 said:**
> Thanks alot for the very quick reply!

I eventually installed ffmpeg from source, and it all works well, except it complains about threads option.
What does it say about threads? Show your FFmpeg command and the complete FFmpeg output.
> **alecz20 said:**
> Do I really need two threads on a core 2 Duo when transcoding HD movies on the fly?
It depends on the encoder you're using.  Only *libx264* can currently support *-threads 0*, which automatically chooses an appropriate value.

---

### Post by alecz20 on 2010-07-23
I'm using a script for mediatomb.

The relevant command in the script is:

```

exec /usr/local/bin/ffmpeg -threads 2 -i "${INPUT}" -vcodec ${VIDEO_CODEC} -b ${VIDEO_BITRATE} \
-acodec ${AUDIO_CODEC} -ab ${AUDIO_BITRATE} -ar ${AUDIO_SAMPLERATE} -ac ${AUDIO_CHANNELS} \
-f ${FORMAT} - > "${OUTPUT}" 2>/tmp/mediatomb-ffmpeg.log

```

as you can see I give it the parameter "-threads 2"

in the log I get this:

```

FFmpeg version 0.6, Copyright (c) 2000-2010 the FFmpeg developers
  built on Jul 23 2010 14:09:43 with gcc 4.3.3
  configuration:
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0.11. 0 /  0.11. 0
**Warning: not compiled with thread support, using thread emulation**


```



Also I am using mpeg2video as the video codec

---

### Post by FakeOutdoorsman on 2010-07-23
As the warning states, you didn't tell FFmpeg to compile with support for threads. Your *./configure* was blank and therefore lacking support for threads among other things.  To compile FFmpeg with threads support, see:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

Or use FFmpeg from the Ubuntu repository and enable the additional encoders as shown in my previous link.

---

### Post by alecz20 on 2010-07-23
I tried compiling from source with all those options, and it kept complaining about missing libraries

so I did 
```

sudo apt-get build-dep ffmpeg

```

but it said it needed to download 73 MB of archives.

At this point I decided to go with the repository option.

Now the threads warning is gone, and it works well.

However I get a lot of messages like this:
```

[dvd @ 0x8f8ee80]packet too large, ignoring buffer limits to mux it
[dvd @ 0x8f8ee80]buffer underflow i=0 bufi=235459 size=260781
[dvd @ 0x8f8ee80]buffer underflow i=0 bufi=237483 size=260781
[dvd @ 0x8f8ee80]packet too large, ignoring buffer limits to mux it
[dvd @ 0x8f8ee80]buffer underflow i=0 bufi=237483 size=260781
[dvd @ 0x8f8ee80]buffer underflow i=0 bufi=239507 size=260781

```

what does this mean?

---

### Post by FakeOutdoorsman on 2010-07-23
It's hard to determine how you received those messages without knowing your FFmpeg command.  You can ignore those messages if it creates a playable output.

---

### Post by alecz20 on 2010-07-29
Hi again.

Some .mov files are playable, other are not.

Looking in the logs I see this:

```
Error while decoding stream.
```

What might also help is that the video has aac audio stream, and from the log it does not specifically say that ffmpeg was compiled with aac support.
I did install ffmpeg as you suggested:
```

sudo apt-get install ffmpeg libavcodec-unstripped-52

```

I have attached the log


Also I found this:
[http://lzone.de/aac+decoding+with+ffmpeg+doesn%27t+work](http://lzone.de/aac+decoding+with+ffmpeg+doesn%27t+work)

---

