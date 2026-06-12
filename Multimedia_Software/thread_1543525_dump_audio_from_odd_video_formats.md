---
title: "dump audio from odd video formats"
date: 2010-08-01
forum: Multimedia Software
---

### Post by pmooney78 on 2010-08-01
I'd like to use my cell phone (or, if all else fails, my digicam) as a voice recorder. Neither offers the ability to record voice clips, but I can record videos with them.

Problem is, both record unusual video formats ... my phone records .3g2  movies with an audio stream that identifies its audio format as "Qclp" (Qualcomm Purevoice, apparently, but I haven't been able to find out much more than that). Only mplayer manages to play the sound from these videos, and I haven't been able to do much with the sound. WinFF can extract the sound from them, but it sounds ... rougher, or something ... after the conversion. At any rate, I'd prefer to extract the video directly, rather than re-encode it, to avoid losing quality. I can't tell what do do from here.

Alternately, my camera takes Quicktime videos with m-law WAV encoding. I can extract the audio from these videos with

```

ffmpeg -i 100_4001.MOV -f wav -vn -acodec copy output.wav

```

but there's not much I can do with them besides play them in VLC. I'd like to be able to re-encode them as FLAC to save hard drive space, but FLAC complains it doesn't take m-law input files. Can I expand them to PCM WAV losslessly?

Either would be fine, although I'd prefer to be able to extract the audio from the 3g2 file.

---

### Post by andrew.46 on 2010-08-01
Hi pmoomey,

As you have found FFmpeg can decode the audio:

```
andrew@skamandros~$ **[COLOR="Red"]ffmpeg -codecs | grep -i qcelp[/COLOR]**
FFmpeg version SVN-r24596, Copyright (c) 2000-2010 the FFmpeg developers
  built on Jul 30 2010 23:28:22 with gcc 4.4.4
  configuration: --prefix=/usr --mandir=/usr/man --enable-postproc 
--enable-avfilter --enable-pthreads --enable-shared --disable-static 
--disable-ffserver --enable-libtheora --enable-libvorbis --enable-x11grab 
--enable-libmp3lame --enable-libx264 --enable-libfaac 
--enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3
 --enable-zlib --enable-libvpx --enable-libgsm --enable-nonfree 
--enable-gpl
  libavutil     50.23. 0 / 50.23. 0
  libavcore      0. 2. 0 /  0. 2. 0
  libavcodec    52.84. 2 / 52.84. 2
  libavformat   52.77. 0 / 52.77. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.27. 0 /  1.27. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
**[COLOR="Red"] D A    qcelp           QCELP / PureVoice[/COLOR]**
```

So it should be able to easily convert to whatever format you wish. Video would normally be h263 which should not provide any troubles. So the question would be: what sort of container and codecs do wish to convert these 3g2 files to? Ideally you could post one of these files somewhere...

Andrew

---

### Post by pmooney78 on 2010-08-01
My preference would be to munge the audio as little as possible -- the quality is already fairly low. Ideally, I'd like to just dump it into some kind of container that doesn't involve re-coding, or just re-encode into something lossless, like FLAC ... my primary motivation is just not to alter what little quality is already there.

I can't post one of the videos I have on my laptop because what I'm recording is confidential for my own use ... and ironically, I don't have my cell phone with me to make a new recording. I'll post one tomorrow if that's helpful, though. 

I get somewhat different results from the ffmpeg/grep command you posted, which might or might not be relevant:

```

ffmpeg --codecs | grep -i qcelp
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 23 2010 15:05:49, gcc: 4.4.1
ffmpeg: missing argument for option '--codecs'

```

Thanks for your quick response. :)

---

### Post by ron999 on 2010-08-01
Hi
You've put two minus signs in front of codecs, instead of just one.

---

### Post by pmooney78 on 2010-08-01
Whoops! I tried it both ways, actually, but it turns out that they give (essentially?) the same output. I just happened to post the result of the second one.

---

### Post by andrew.46 on 2010-08-02
Hi pmooney,

> **pmooney78 said:**
> Whoops! I tried it both ways, actually, but it turns out that they give (essentially?) the same output. I just happened to post the result of the second one.

Your version of FFmpeg is a little older than mine, the syntax has changed a little over the last little while. Perhaps have a look at Fakeoutdoorsman's guide:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

and if this works out for you could you post the terminal output of:

```
ffmpeg -i *[COLOR="Red"]my_problem_file.3g2[/COLOR]*
```

and it should be pretty straightforward to suggest the best syntax to either strip the audio or transcode the whole thing.

Andrew

---

### Post by ron999 on 2010-08-02
Hi
Maybe I'm missing something here, but isn't the simplest way to use commands like this:-

For wav output:-
```
ffmpeg -i 100_4001.MOV output.wav

```
For flac output:-
```
ffmpeg -i 100_4001.MOV output.flac

```
Both of these methods probably won't degrade the quality any.

---

### Post by pmooney78 on 2010-08-02
<facepalm>

You're right, I've been making it too complicated. I forgot I don't have to look for complex options to drop the video. Just providing an input video file and an output file with an extension specifying an audio format works.

Sometimes the simplest way is the best. :)

</facepalm>

---

