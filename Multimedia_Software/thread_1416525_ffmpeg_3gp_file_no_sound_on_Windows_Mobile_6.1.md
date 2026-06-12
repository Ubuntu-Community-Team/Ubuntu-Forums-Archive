---
title: "ffmpeg 3gp file no sound on Windows Mobile 6.1"
date: 2010-02-26
forum: Multimedia Software
---

### Post by amsterdamharu on 2010-02-26
```
ffmpeg -i in.avi -s 352x288 -vcodec h263 -r 25 -b 100k -ab 64 -acodec mp3 -t 60 out.3gp
```

The file plays with sound on a Lenovo phone but not on Windows Mobile Media player. Somehow the Media player is not good enough (missing codecs).

Does anyone know a way to encode it so it will play with sound, hard to believe that the mp3 encoding cannot be played by media player.

If I play the file with vlc on my desktop and check the encoding I get:
codec: mpga
channels:2
sample rate: 44100 Hz
Bits per sample: 16
Bitrate: 1411 Kb/s

---

### Post by andrew.46 on 2010-02-26
Hi amsterdamharu,

I am not familiar with Windows Mobile 6.1 so unfortunately I am not aware of what codecs are available for playback. However I note that you are placing mp3 sound in a 3gp container which could possibly be one problem. Perhaps try to use aac sound instead and substitute your mp3 syntax for something like:

```
-acodec libfaac -ab 128k
```

and your mobile device *might* be happier. aac encoding is problematic in Karmic at least and this page might help out with that:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

But can I ask if you are limited to a 3gp container? I believe many modern devices are happy with an mp4 container and this should give you substantial more flexibility. Another thing to consider is that 3gp containers can also take h264 video which again increases your options...

All the best,

Andrew

---

### Post by amsterdamharu on 2010-02-26
Hi Andrew, thank you for your reply. I would love to try other formats if I can figure out how ffmpeg works and/or if there is documentation that I can understand.

The command I got from the Internet about how to convert to 3gp since most mobile phones play that. Thre was some problem converting to mp3 but after adding medibuntu software source and did an update it worked ok.

On Microsofts website it says something like mobile player only supports wma wmv and flv.

I had to change libfaac to aac since ffmpeg I use doesn't have libfaac (they must have changed it). And it plays video and sound now. Thank you.

```
ffmpeg -formats | grep aac
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 17 2009 21:37:49, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
 D  aac             ADTS AAC
 DEA    aac
 D A    mpeg4aac
 

ffmpeg -i in.avi -s 352x288 -vcodec h263 -r 25 -b 100k -acodec aac -ab 128k -t 60 out.3gp
```
I think D stands for decode and E for encode but do you know what's the A for (DEA    aac)?

---

### Post by andrew.46 on 2010-02-26
Hi amsterdamharu,

> **amsterdamharu said:**
> Hi Andrew, thank you for your reply. I would love to try other formats if I can figure out how ffmpeg works and/or if there is documentation that I can understand.

My own journey into FFmpeg started on these forums:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

and if you want to learn a little more about FFmpeg this is the place to go to.

> 
The command I got from the Internet about how to convert to 3gp since most mobile phones play that. Thre was some problem converting to mp3 but after adding medibuntu software source and did an update it worked ok.

Certainly in older times mobile phones would play 3gp files that had h263 video and amr sound, but this has changed a lot in more recent times.

> I had to change libfaac to aac since ffmpeg I use doesn't have libfaac (they must have changed it). And it plays video and sound now. Thank you.

Excellent news :). Looks like you are running a quite aged version of FFmpeg and as you have suspected the naming convention has changed more than a little. If you use *-acodec aac* with a modern FFmpeg you would be invoking the new native aac encoder...

> 
I think D stands for decode and E for encode but do you know what's the A for (DEA    aac)?

The A stands for Audio. 

All the best,

Andrew

---

### Post by amsterdamharu on 2010-02-27
Thanks again Andrew, I will check on how to use ffmpeg when I have more time. Will try to encode the video in better quality since the phone should be able to handle higher bitrate or better encoder. Resolution is about as high as it will get on the phone screen.

---

