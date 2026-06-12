---
title: "Good alternative to VLC?"
date: 2009-11-27
forum: Multimedia Software
---

### Post by themusicalduck on 2009-11-27
I need an alternative to VLC, because VLC seems to have a bug that stops it from playing HD .mkv files properly.

I know there are plenty of players that can handle .mkv files, but none of the players I have tried can also handle subtitles properly. Only VLC seems to show subtitles with the proper formatting.

I've heard that mplayer is good, but mplayer seems to lock up whenever I try to open a file on it.

---

### Post by themusicalduck on 2009-11-27
bump

---

### Post by andrew.46 on 2009-11-27
Hi themusical,

> **themusicalduck said:**
> I've heard that mplayer is good, but mplayer seems to lock up whenever I try to open a file on it.

This is not normal for MPlayer. Could you open a file with the following syntax:

```
mplayer -v **[COLOR="Red"]*myfile.avi*[/COLOR]**

```

and this should give a few hints as to what is going on.

Andrew

---

### Post by themusicalduck on 2009-11-28
Opening an avi or mkv file from the command line did let me play a video. It seems like opening a .mkv file using gmplayer (.avi files are fine) doesn't work. (It eats up a load of cpu too)

This is the output of the command line when I run gmplayer and open a .mkv ```
Error while decoding frame!
[h264_vdpau @ 0x93dc780]B picture before any references, skipping
[h264_vdpau @ 0x93dc780]decode_slice_header error
[h264_vdpau @ 0x93dc780]no frame!
Error while decoding frame!
[h264_vdpau @ 0x93dc780]B picture before any references, skipping
[h264_vdpau @ 0x93dc780]decode_slice_header error
[h264_vdpau @ 0x93dc780]no frame!
Error while decoding frame!
[h264_vdpau @ 0x93dc780]B picture before any references, skipping
[h264_vdpau @ 0x93dc780]decode_slice_header error
[h264_vdpau @ 0x93dc780]no frame!
Error while decoding frame!
[h264_vdpau @ 0x93dc780]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x93dc780]decode_slice_header error
[h264_vdpau @ 0x93dc780]no frame!
Error while decoding frame!
[h264_vdpau @ 0x93dc780]B picture before any references, skipping
[h264_vdpau @ 0x93dc780]decode_slice_header error
[h264_vdpau @ 0x93dc780]no frame!
Error while decoding frame!
[h264_vdpau @ 0x93dc780]B picture before any references, skipping
[h264_vdpau @ 0x93dc780]decode_slice_header error
[h264_vdpau @ 0x93dc780]no frame!
Error while decoding frame!
[h264_vdpau @ 0x93dc780]B picture before any references, skipping
[h264_vdpau @ 0x93dc780]decode_slice_header error
[h264_vdpau @ 0x93dc780]no frame!
Error while decoding frame!
[h264_vdpau @ 0x93dc780]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x93dc780]decode_slice_header error
[h264_vdpau @ 0x93dc780]no frame!
Error while decoding frame!
[h264_vdpau @ 0x93dc780]B picture before any references, skipping
[h264_vdpau @ 0x93dc780]decode_slice_header error
[h264_vdpau @ 0x93dc780]no frame!
Error while decoding frame!
[h264_vdpau @ 0x93dc780]B picture before any references, skipping
[h264_vdpau @ 0x93dc780]decode_slice_header error
[h264_vdpau @ 0x93dc780]no frame!

```

That just gets repeated.
I tried to compile mplayer a while ago to get vdpau support, so I guess it's that which is causing problems.

Opening a .mkv file with the command you mentioned does work, but it still doesn't handle subtitles properly, so it doesn't look like mplayer could fix my problem anyway.

---

### Post by andrew.46 on 2009-11-28
Hi themusicalduck,

> **themusicalduck said:**
> This is the output of the command line when I run gmplayer and open a .mkv 

gmplayer is pretty broken at the best of times, see if the same error appears using SMPlayer.

All the best,

Andrew

---

### Post by SuperSonic4 on 2009-11-28
I'd have a look at compiling mplayer. andrew.46 has a good guide on it somewhere

Perhaps the video file is at fault? Do you have the appropriate codecs installed? As mkv is a container format it would depend on the video codec and audio codec contained therein. Can you paste the output of

```
ffmpeg -i movie.mkv
```

where movie.mkv is a troublesome file

---

### Post by themusicalduck on 2009-11-28
I think the video file itself is problematic, because not all HD .mkv files have the problem. But it definitely happens on more than one .mkv file so it isn't only one specific file but more likely to do with the way the mkv has been put together.

The main problem is that VLC skips to the beginning of the video and the sounds goes off when it encounters a new chapter.
I actually made a thread about it on the vlc forums and on here but didn't get much help. I put more detail about it here - [http://forum.videolan.org/viewtopic.php?f=13&t=68066&sid=cd69a8bd9a2d5575fe55f99e4954920f](http://forum.videolan.org/viewtopic.php?f=13&t=68066&sid=cd69a8bd9a2d5575fe55f99e4954920f)

This is the output from ffmpeg -i movie.mkv - ```
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
[matroska @ 0x95b7700]Unknown entry 0x6E67

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (48000/1001) -> 23.98 (24000/1001)
    Last message repeated 1 times
Input #0, matroska, from '[Chihiro]_K-ON!_-_01_[1280x720_H.264_AAC][646B1AF3].mkv':
  Duration: 00:21:09.86, start: 0.000000, bitrate: N/A
    Stream #0.0(jpn): Video: h264, yuv420p, 1280x720, PAR 1:1 DAR 16:9, 23.98 tbr, 1k tbn, 47.95 tbc
    Stream #0.1(jpn): Audio: aac, 48000 Hz, stereo, s16
    Stream #0.2(eng): Subtitle: 0x0000
    Stream #0.3: Attachment: 0x0000
At least one output file must be specified

```

The subtitle formatting wouldn't be such a big deal, except it misses out entire lines which makes it a bit annoying.

Smplayer can't seem to play mkv either, although it doesn't crash and there is no output on the terminal, it just won't play.

It'd be great if smplayer would work well like playing files from the command line with mplayer and with working subtitles since it runs so nicely with vdpau enabled :/

---

### Post by rvm4000 on 2009-11-28
> **themusicalduck said:**
> Smplayer can't seem to play mkv either, although it doesn't crash and there is no output on the terminal, it just won't play.

I don't have any problems to play mkv files, although I don't use vdpau because my graphic card doesn't support it.

You can try to change the video driver to xv (preferences -> general -> video) to see if you at least can see something.

> **themusicalduck said:**
> 
It'd be great if smplayer would work well like playing files from the command line with mplayer and with working subtitles since it runs so nicely with vdpau enabled :/

You can try to update mplayer:
[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

Some people reported that vdpau works ok with the build.

---

### Post by themusicalduck on 2009-11-28
EDIT: It's great when the simplest of actions can fix things.. I deleted the folder ~/.mplayer and suddenly everything works great. Even subtitles are working properly (probably with the updated version from that repo) :D Thanks for the help with it!





I removed the compiled version of mplayer and installed some updates from the mplayer repo you posted.

Tried changing the output to xv too but with no luck.

I actually found a window that shows a log of mplayer, it comes up with the same error messages I posted above to do with vdpau.

```
Error while decoding frame!
[h264_vdpau @ 0x89d0d40]B picture before any references, skipping
[h264_vdpau @ 0x89d0d40]decode_slice_header error
[h264_vdpau @ 0x89d0d40]no frame!
Error while decoding frame!
[h264_vdpau @ 0x89d0d40]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x89d0d40]decode_slice_header error
[h264_vdpau @ 0x89d0d40]no frame!
Error while decoding frame!
[h264_vdpau @ 0x89d0d40]B picture before any references, skipping
[h264_vdpau @ 0x89d0d40]decode_slice_header error
[h264_vdpau @ 0x89d0d40]no frame!
Error while decoding frame!
[h264_vdpau @ 0x89d0d40]B picture before any references, skipping
[h264_vdpau @ 0x89d0d40]decode_slice_header error
[h264_vdpau @ 0x89d0d40]no frame!
Error while decoding frame!

FATAL: Could not initialize video filters (-vf) or video output (-vo).


Exiting... (End of file)
ID_EXIT=EOF
```

It's strange how it works perfectly well from the command line, but comes up with that error whenever I try to play it with smplayer or gmplayer..

---

