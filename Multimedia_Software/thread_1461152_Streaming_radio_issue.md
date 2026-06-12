---
title: "Streaming radio issue"
date: 2010-04-23
forum: Multimedia Software
---

### Post by squid68 on 2010-04-23
Been fine for months and now can't stream from Sirius Radio's online webplayer and cannot stream from wbal.com.  I used to use xgine and vlc to overcome this when I was in Feisty and Gusty but Hardy came with windows media player plugin and have been fine until yesterday. But it seems all of the other stations I listen to and all my video seems to be fine. Please, anyone have any suggestions on why all of a sudden my streams fail?

---

### Post by squid68 on 2010-04-23
Maybe this is related but I can no longer listen to two or more video/audio files at the same time. Used to be able to have a music file or radio stream going and could still watch/listen to at the same time a news story, youtube video or whatever. But have not been able to do that lately either. Please, some help here!

---

### Post by tgalati4 on 2010-04-23
Open a terminal:

pulseaudio -k

Then try to replay your streams.

---

### Post by mc4man on 2010-04-23
Becuase it's wma2 it may be related to some borked security updates - see the links here
[http://ubuntuforums.org/showthread.php?p=9161231#post9161231](http://ubuntuforums.org/showthread.php?p=9161231#post9161231)

If you have mplayer (uses it's own libavcodec in hardy) try from terminal to test

```
mplayer mmsh://bdcast-hearstradio-wbal-am.wm.llnwd.net/bdcast_hearstradio_wbal-am?MSWMExt=.asf
```

---

### Post by squid68 on 2010-04-23
Thanks. But the -k thing did not work. And the Output I got from the mplayer inquiry is

dcast_hearstradio_wbal-am?MSWMExt=.asf
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 4000+ (Family: 15, Model: 55, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing mmsh://bdcast-hearstradio-wbal-am.wm.llnwd.net/bdcast_hearstradio_wbal-am?MSWMExt=.asf.
No stream found to handle url mmsh://bdcast-hearstradio-wbal-am.wm.llnwd.net/bdcast_hearstradio_wbal-am?MSWMExt=.asf

---

### Post by mc4man on 2010-04-24
> And the Output I got from the mplayer inquiry is....

I'm on lucid with my own builds but happen to have a hardy install I never modded.

It turns out the repo mplayer won't play the stream, shows the same as you see.
If you were to build or use probably any ppa mplayer then you could.

A quick test with the mplayer build for hardy from rvm ppa (smplayer) and there was no issue.

With the non-updated ffmpeg libs (libavcodec1d, libavformat1d - 5ubuntu7.3), your streams played fine both in the browser and in totem
(gstreamer0.10-ffmpeg, gstreamer0.10-plugins-bad, gstreamer0.10-plugins-ugly and totem mozilla plugin

After updating the ffmpeg libs playback failed in both.

I'd look for updates to libavcodec1d, libavformat1d next week to hopefully resolve this.

I was able to force the versions back and playback was restored ( had the medibuntu versions, though no diff. in this case from hardy repo ones

---

### Post by squid68 on 2010-04-24
I guess I can be patient for an update. Thanks folks for the advice and your time!

---

