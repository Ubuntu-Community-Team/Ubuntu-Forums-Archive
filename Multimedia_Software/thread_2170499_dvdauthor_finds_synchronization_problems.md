---
title: "dvdauthor finds synchronization problems"
date: 2013-08-26
forum: Multimedia Software
---

### Post by George Heine on 2013-08-26
I have a short video clip (about 35 sec.), which am trying to include on a video DVD.
Get the following messages from dvdauthor:

```

$ dvdauthor  -o ../Test/ -t EE.mpg --video=ntsc
DVDAuthor::dvdauthor, version 0.7.0.
Build options: gnugetopt imagemagick iconv freetype fribidi fontconfig
Send bug reports to <dvdauthor-users@lists.sourceforge.net>

INFO: no default video format, must explicitly specify NTSC or PAL
INFO: dvdauthor creating VTS
STAT: Picking VTS 07

STAT: Processing EE.mpg...
WARN: Audio pts for channel 0 moves backwards by 2879; please remultiplex input.
WARN: Previous sector: 0.500 - 0.564
WARN: Current sector: 0.532 - 0.564
WARN: Audio pts for channel 0 moves backwards by 1; please remultiplex input.
WARN: Previous sector: 0.532 - 0.564
WARN: Current sector: 0.564 - 0.596
WARN: Audio pts for channel 0 moves backwards by 2; please remultiplex input.
WARN: Previous sector: 0.948 - 0.980
WARN: Current sector: 0.979 - 1.011
ERR:  Cannot infer pts for VOBU if there is no audio or video and it is the
ERR:  first VOBU.


```
Apparently 2879 units of audio pts equals 0.032 units of sector, whatever an "audio pts" and a "sector" are.
The message seems to imply that the video and audio are out of sync in three places, although this is not
noticeable when playing the video with mplayer or ffplay.

Anyway, how do I fix the video so dvdauthor stops complaining?

Thanks for any assistance -

FURTHER INFORMATION:
The video was ripped from a DVD, probably using "mplayer -dumpstream,"
ffprobe gives the following information.  Note the last line (in red in the original) about an "unsupported codec".
```
$ ffprobe EE.mpg 
ffprobe version git-2013-08-25-626739e Copyright (c) 2007-2013 the FFmpeg developers
  built on Aug 24 2013 20:38:02 with gcc 4.6 (Ubuntu/Linaro 4.6.3-1ubuntu5)
  configuration: --prefix=/home/gheine/ffmpeg_build --extra-cflags=-I/home/gheine/ffmpeg_build/include --extra-ldflags=-L/home/gheine/ffmpeg_build/lib --bindir=/home/gheine/bin --extra-libs=-ldl --enable-gpl --enable-libass --enable-libfdk-aac --enable-libmp3lame --enable-libopus --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-x11grab
  libavutil      52. 42.100 / 52. 42.100
  libavcodec     55. 29.100 / 55. 29.100
  libavformat    55. 14.102 / 55. 14.102
  libavdevice    55.  3.100 / 55.  3.100
  libavfilter     3. 82.102 /  3. 82.102
  libswscale      2.  5.100 /  2.  5.100
  libswresample   0. 17.103 /  0. 17.103
  libpostproc    52.  3.100 / 52.  3.100
[NULL @ 0xafe11e0] start time is not set in estimate_timings_from_pts
Input #0, mpeg, from 'EE.mpg':
  Duration: 00:00:36.45, start: 0.514689, bitrate: 6504 kb/s
    Stream #0:0[0x1bf]: Data: dvd_nav_packet
    Stream #0:1[0x80]: Audio: ac3, 48000 Hz, stereo, fltp, 448 kb/s
    Stream #0:2[0x1e0]: Video: mpeg2video (Main), yuv420p, 720x480 [SAR 8:9 DAR 4:3], max. 9000 kb/s, 29.97 fps, 29.97 tbr, 90k tbn, 59.94 tbc
**[COLOR=#ff8c00]Unsupported codec with id 1145979222 for input stream 0[/COLOR]**

```

---

### Post by George Heine on 2013-09-02
No replies in this forum, so reposted to the ffmpeg-users forum.  Here is a summary of what I found:

- The error from ffprobe occurs because there is a third input "data" stream (0:0) with dvd-nav information.  This stream can be removed by using -map to specify the other streams (0:1 and 0:2), and omitting  mention of 0:0 on the command line, i.e., ```


$ ffmpeg -i EE.mpg -map 0:1 -map 0:2  -target ntsc-dvd EEout.mpg

``` 

   However, the resulting mpg file still has synchronization problems ("please remultiplex input") when fed to dvdauthor.

- Synchronization problems can be removed by the following procedure:  Copy the video and audio streams to separate files, and reformat the audio stream. Then merge the two files again: ```
 
$ ffmpeg -i EE.mpg -map 0:1    EEaud.wav
$ ffmpeg -i EE.mpg -map 0:2    EEvid.mpg

$ ffmpeg -i EEaud.wav -i EEvid.mpg  -target ntsc-dvd EEout.mpg

```

Marked this thread as 'Solved'.

---

