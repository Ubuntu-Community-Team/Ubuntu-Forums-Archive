---
title: "Mplayer time OSD in ATSC transport streams"
date: 2013-09-02
forum: Multimedia Software
---

### Post by aun on 2013-09-02
I use my system as a dvr by way of a Hauppauge tuner card with a script and cron entries.  The actual capture of the stream is done by:

```

cat /dev/video0 > $outfile  #(analog)
cat /dev/dvb/adapter0/dvr0 > $outfile  #(digital)

```

When capture is made from analog cable tv the output is a mpeg.  Generally, I play the results with mplayer.  I've done this for a few years now.  Everything works fine.  Mplayer's on screen display will show ElapsedTime/TotalTime correctly.

I have recently switched from analog cable to US over the air broadcast (ATSC 8VSB). Output in this case is a transport stream.  Record and playback still work fine.  However, on playback mplayer's osd shows an inflated elapsed time, and does not correctly determine the total length of the file.  Apparently this is due to ID_START_TIME and ID_LENGTH info being somehow encoded into the transport stream.  

I use the osd for this info all the time, and having it not function properly is a major drawback. I would be happy to simply change my script to remux with mencoder, rather than 'cat'ting, but when I do this I lose AV sync in entirety. 

Sample mplayer output for a file about 1/2 hour long is below:

```
$ mplayer -identify news.mpg
MPlayer svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing news.mpg.
libavformat version 53.21.1 (external)
Mismatching header version 53.19.0
TS file format detected.
VIDEO MPEG2(pid=49) AUDIO A52(pid=52) NO SUBS (yet)!  PROGRAM N. 0
ID_VIDEO_ID=49
ID_AUDIO_ID=52
VIDEO:  MPEG2  1920x1080  (aspect 3)  29.970 fps  24000.0 kbps (3000.0 kbyte/s)
Load subtitles in ./
ID_FILENAME=news.mpg
ID_DEMUXER=mpegts
ID_VIDEO_FORMAT=0x10000002
ID_VIDEO_BITRATE=24000000
ID_VIDEO_WIDTH=1920
ID_VIDEO_HEIGHT=1080
ID_VIDEO_FPS=29.970
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=8192
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=0
ID_AUDIO_NCH=0
ID_START_TIME=78023.26
ID_LENGTH=979.77
ID_SEEKABLE=1
ID_CHAPTERS=0
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 53.35.0 (external)
Mismatching header version 53.32.2
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
ID_VIDEO_CODEC=ffmpeg2
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
ID_AUDIO_BITRATE=384000
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
ID_AUDIO_CODEC=ffac3
Starting playback...
Unsupported PixelFormat 61
Unsupported PixelFormat 53
Unsupported PixelFormat 81
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
ID_VIDEO_ASPECT=1.7778
VO: [vdpau] 1920x1080 => 1920x1080 Planar YV12 
A:78025.9 V:78026.9 A-V: -1.003 ct: -0.240  76/ 76 39% 36%  1.3% 6 0 

```

It would seem at least the osd issue should be a trivial fix, but I have spent fruitless hours trying to solve both of these problems.  Does anyone have a solution, either to correct the osd at playback or to remux a synced version?  Any help would be greatly appreciated!

---

### Post by aun on 2013-09-06
(bump) ... any ideas?

---

### Post by SeijiSensei on 2013-09-07
You're going to have a lot better chance of having the question answered by the mplayer developers than here.  Have you searched any of the [mplayer mailings lists]("http://mplayerhq.hu/design7/mailing_lists.html") to see if this problem has been discusssed there?  

If you are using the version of mplayer that ships with recent Ubuntu versions, you're actually using the [mplayer2]("http://www.mplayer2.org/") fork and should ask your question there instead.

It may simply be a bug in the code as it applies to transport streams.

---

### Post by aun on 2013-09-07
Thanks, Seiji.

You may be right that the questions may require more in depth research, though I think I've spent as much time as I can justify.  I've done quite a bit of searching, and I haven't yet found an answer on the mplayer forums or anywhere else.  

For the benefit of anyone else who may want to take this up, here's a little more info:

Despite what my information says, I'm running Precise, not Jaunty (with the new forum changes I can't update my profile at the moment).  I've enabled medibuntu repository, and that should be the mplayer version I'm using.

The closest I came to a solution on the OSD issue was to try changing the OSD configuration by adding one of these lines to ~/.mplayer/input.conf
```

o osd_show_property_text "${percent_pos} / ${length}"
o osd_show_property_text "${time_pos} / ${length}"

```

See [http://www.mplayerhq.hu/DOCS/tech/slave.txt]("http://www.mplayerhq.hu/DOCS/tech/slave.txt") for more info.  None of the available properties seems to really do what I'm looking for, though. 

As far as remuxing, I think I tried every option combination on mplayer, mencoder and ffmpeg - actually avconv.  The most informative information I found on the confusing relationship between these was at [http://blog.pkh.me/p/13-the-ffmpeg-libav-situation.html]("http://blog.pkh.me/p/13-the-ffmpeg-libav-situation.html").

The issues here are confusing enough without the added variables introduced by developer wars, so I think I'm done for now.  If anyone finds anything please reply.  If I find anything in the future I'll resurrect the thread to point people in the right direction.

---

