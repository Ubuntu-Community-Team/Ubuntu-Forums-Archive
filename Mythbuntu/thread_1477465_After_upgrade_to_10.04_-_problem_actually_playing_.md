---
title: "After upgrade to 10.04 - problem actually playing videos"
date: 2010-05-08
forum: Mythbuntu
---

### Post by elliott6 on 2010-05-08
Hey All!

Having a problem after my upgrade to 10.04 with MythVideo.  Guessing it has to do with MythVideo or Mplayer as I am able to launch the videos via VLC or Xine outside of myth.  Wondering if someone could straighten me out specific to just playing videos (avi, ISO, mkv, etc.).  The video actually starts up within mythTV, but does not actually play.  So play starts the video, I can see the opening frame, but it doesn't continue to play.  I can fast forward, rewind, advancing the picture (and can still see the frames.. paused), but the video doesn't actually play. 

Any ideas?  I have tried to run mythfrontend via terminal, and the output is below if it helps.  

Thanks!

Sean

```
2010-05-08 19:36:30.728 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Arclight/video-ui.xml
2010-05-08 19:36:30.746 Unable to find image file: images/popup_darken.png
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /media/videos/24/Season 6/24 - s06e11.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  608x336  24bpp  23.976 fps  1000.1 kbps (122.1 kbyte/s)
Clip info:
 Software: cant touch this
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
[mpeg4 @ 0x7f4d204188a0]Invalid and inefficient vfw-avi packed B frames detected
VDec: vo config request - 608 x 336 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.81:1 - prescaling to correct movie aspect.
VO: [xv] 608x336 => 608x336 Planar YV12  [fs] [zoom]
```

In case any of this is relative - 

I shunned the "if it ain't broke, don't fix it" and went with the upgrade from 8.10 with myth 0.21 to 10.04LTS and 0.23.  Everything runs okay now that I have tackled a few issues, but I still have one question/problem/issue.  

My upgrade path was 8.10->9.04->9.10->10.04 stepping through the upgrade process, and stopping along the way to run and auto update the myth database (after a backup) once upgraded/installed.

---

### Post by superm1 on 2010-05-09
> **elliott6 said:**
> Hey All!

Having a problem after my upgrade to 10.04 with MythVideo.  Guessing it has to do with MythVideo or Mplayer as I am able to launch the videos via VLC or Xine outside of myth.  Wondering if someone could straighten me out specific to just playing videos (avi, ISO, mkv, etc.).  The video actually starts up within mythTV, but does not actually play.  So play starts the video, I can see the opening frame, but it doesn't continue to play.  I can fast forward, rewind, advancing the picture (and can still see the frames.. paused), but the video doesn't actually play. 

Any ideas?  I have tried to run mythfrontend via terminal, and the output is below if it helps.  

Thanks!

Sean

```
2010-05-08 19:36:30.728 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Arclight/video-ui.xml
2010-05-08 19:36:30.746 Unable to find image file: images/popup_darken.png
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /media/videos/24/Season 6/24 - s06e11.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  608x336  24bpp  23.976 fps  1000.1 kbps (122.1 kbyte/s)
Clip info:
 Software: cant touch this
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
[mpeg4 @ 0x7f4d204188a0]Invalid and inefficient vfw-avi packed B frames detected
VDec: vo config request - 608 x 336 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.81:1 - prescaling to correct movie aspect.
VO: [xv] 608x336 => 608x336 Planar YV12  [fs] [zoom]
```

In case any of this is relative - 

I shunned the "if it ain't broke, don't fix it" and went with the upgrade from 8.10 with myth 0.21 to 10.04LTS and 0.23.  Everything runs okay now that I have tackled a few issues, but I still have one question/problem/issue.  

My upgrade path was 8.10->9.04->9.10->10.04 stepping through the upgrade process, and stopping along the way to run and auto update the myth database (after a backup) once upgraded/installed.
You might consider trying to use Internal instead.  It's far improved since 0.21, and most likely can handle your content directly..

---

### Post by elliott6 on 2010-05-09
Superm!!!

Excellent help as always!  Of course, problem SOLVED!

Not sure why it was setup that way (been using this since 2007, so guess it carried over, and my previous 8.10 had been humming along just fine, so hadn't had the issue to fix).  

A lot of times it is the simplest fix, isn't it!?  

Again, thanks for your help.  Went into Media Player Settings, changed the default from mplayer -fs -zoom... to Internal, and she fired it right up.  Racking my brain for quite a bit with this.  Now I can finally move on to my stealth frontends and other remote connections like mythweb, etc.

Sean

------

My backend appears to be running smoothly.  If only I wouldn't have been foolish getting my hardware RAID up (lost music and over 1TB recordings).  Oh well, good to move on now.  I have the following - 

Backend - MythBuntu 10.04LTS with Myth 0.23 (running auto-fixes); OS is on 40GB drive with 8GB OS, 4GB swap, rest home; storage is a Dell Perc 5i with 3x1TB RAID5 for recordings and 3x1.5TB RAID5 for videos, including movies and DVD iso (2TB) and music including FLAC and iPod with share to my other machines (1TB),

Frontend - Works in progress.  One machine runs smooth for the main TV, although I need to swap some hardware.  Working on a Zotac ION board with compactflash install for the bedroom.

---

