---
title: "Help pls! Mplayer capture screenshot from M2TS failed"
date: 2011-07-14
forum: Multimedia Software
---

### Post by TonyChang on 2011-07-14
Hi:

I'm running Ubuntu 10.04, and installed mplayer, when I tried to SSH and capture a screenshot from a m2ts file,  I always get an error: 
**number of reference frames exceeds max  (probably corrupt input)**
But i'm sure the file isn't corrupt. However, I did captured a picture, but the picture is corrupt. Any ideas?

Here is the log:
```

root@ahdee: ~root@ahdee:~# mplayer -ss 71550 -noframedrop -nosound -vo  jpeg -frames 1 '/home/ahdee/downloads/TEST/BDMV/STREAM/00238.m2ts'
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/ahdee/downloads/TEST/STREAM/00238.m2ts.
TS file format detected.
VIDEO H264(pid=4113) NO AUDIO!  NO SUBS (yet)!  PROGRAM N. 1
FPS seems to be: 23.976025
jpeg: Parsing suboptions.
jpeg: Progressive JPEG disabled.
jpeg: Baseline JPEG enabled.
jpeg: Suboptions parsed OK.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
Audio: no sound
Starting playback...
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
[h264 @ 0x2b1bdb6c98a0]number of reference frames exceeds max (probably corrupt input), discarding one
V:2863.8   1/  1 ??% ??% ??,?% 0 0
V:2863.8   2/  2 ??% ??% ??,?% 0 0
V:2864.0   3/  3 ??% ??% ??,?% 0 0 
V:2863.9   4/  4 ??% ??% ??,?% 0 0
VDec: vo config request - 1920 x 1080 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
[swscaler @ 0x2b1bdc181660]No accelerated colorspace conversion found.
[swscaler @ 0x2b1bdc181660]using unscaled yuv420p -> rgb24 special converter
VO: [jpeg] 1920x1080 => 1920x1080 RGB 24-bit 
jpeg: . - Output directory already exists and is writable.
V:2864.0   5/  5 ??% ??% ??,?% 0 0


Exiting... (End of file)
root@ahdee: ~root@ahdee:~#
```The captured pic (click to enlarge):
[[IMG]http://thumb.phyrefile.com/a/ah/ahdee/2011/07/14/300/00000001.jpg[/IMG]]("http://pic.phyrefile.com/a/ah/ahdee/2011/07/14/00000001.jpg")

Any help would be greatly appreciated!

Thanks

Tony

---

### Post by andrew.46 on 2011-07-16
Perhaps try using the screenshot filter:

```

mplayer -vf screenshot '/home/ahdee/downloads/TEST/BDMV/STREAM/00238.m2ts'

```

and press the default 's' key to save a screenshot in the working directory. Not as usable as *-vo jpeg* but it would be interesting to see if this works...

---

### Post by FakeOutdoorsman on 2011-07-16
FFmpeg is another option to try.
```
ffmpeg -ss 71550 -i /home/ahdee/downloads/TEST/BDMV/STREAM/00238.m2ts -vframes 1 -qscale 2 output.jpg
```
If output.jpg looks crappy, then move -ss so it's an output option. This second command isn't as fast, but it usually more consistent and accurate for some input formats.
```
ffmpeg -i /home/ahdee/downloads/TEST/BDMV/STREAM/00238.m2ts -ss 71550 -vframes 1 -qscale 2 output.jpg
```

---

### Post by SeijiSensei on 2011-07-16
Let's back up a step.  If you play the video with mplayer (e.g, -vo xv), does it display correctly on the screen?  Do you still get the same stream of errors in the terminal as you do with -vo jpeg?  How about -vo png?  What if you don't enforce -noframedrop?

If you use -vf screenshot, you can start and stop capturing a sequence of frames with "S". 

Other people report [this same error]("http://www.google.com/search?q=number+of+reference+frames+exceeds+max+%28probably+corrupt+input"); to learn about "reference frames," visit this page, [http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-x264.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-x264.html), and scroll down to the "frameref" discussion.  It could be that the original was encoded with an unreasonably high number of reference frames, and mplayer is simply complaining.

Another option is to try mplayer2:  [http://www.ubuntugeek.com/install-mplayer2-on-ubuntu-using-ppa.html](http://www.ubuntugeek.com/install-mplayer2-on-ubuntu-using-ppa.html)

---

