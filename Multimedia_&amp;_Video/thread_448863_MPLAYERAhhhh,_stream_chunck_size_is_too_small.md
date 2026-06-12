---
title: "MPLAYER:Ahhhh, stream_chunck size is too small"
date: 2007-05-19
forum: Multimedia &amp; Video
---

### Post by CyberAngel on 2007-05-19
Hello,

Does anyone know what the error "Ahhhh, stream_chunck size is too small" that mplayer drops me when I am trying to listen on some radio streams is?

I am trying to listen on the radio stations from [this]("http://radiofono.gr/live") site and some of them are playing very nicely but many of them are having the problem below...

```
$ mplayer mms://best.live24.gr/best1222
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3500+ (Family: 15, Model: 31, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing mms://best.live24.gr/best1222.
STREAM_ASF, URL: mms://best.live24.gr/best1222
Resolving best.live24.gr for AF_INET6...
Couldn't resolve name for AF_INET6: best.live24.gr
Resolving best.live24.gr for AF_INET...
Connecting to server best.live24.gr[87.117.203.49]: 1755...
Connected
read error:: Operation now in progress
pre-header read failed
Resolving best.live24.gr for AF_INET6...
Couldn't resolve name for AF_INET6: best.live24.gr
Resolving best.live24.gr for AF_INET...
Connecting to server best.live24.gr[87.117.203.49]: 80...
Resolving best.live24.gr for AF_INET6...
Couldn't resolve name for AF_INET6: best.live24.gr
Resolving best.live24.gr for AF_INET...
Connecting to server best.live24.gr[87.117.203.49]: 80...
Cache size set to 64 KBytes
Cache fill: 12.50% (8192 bytes)   Ahhhh, stream_chunck size is too small: 4
Error while parsing chunk header
Cache fill: 14.93% (9783 bytes)
ASF file format detected.
Clip info:
 name:
 author:
 copyright:
 comments:
==========================================================================
Forced audio codec: mad
Requested audio codec family [acelp] (afm=dshow) not available.
Enable it at compilation.
Cannot find codec for audio format 0x130.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Video: no video


Exiting... (End of file)

```

If I try to listen on the above station (mms://best.live24.gr/best1222) for about 30 times then maybe I will be lucky and it will start playing without this error so it is not a codec problem but something else that is very annoying....

The mms://broadcast.hol.gr/deejay does not have any problems... I can always listen to it.

The same error occurs for the most stations from this site...

Any suggestion?

---

