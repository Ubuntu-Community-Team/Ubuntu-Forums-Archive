---
title: "How to play C-span.org video streams?"
date: 2008-02-08
forum: Multimedia &amp; Video
---

### Post by nick1 on 2008-02-08
Greetings,

I am trying to watch a video on c-span.org using VLC version 0.8.4 on Ubuntu 6.06 LTS.  Here is the process I am using to try to play the video in VLC:

File > Open Network > select RTSP > URL:

> rtsp://video.c-span.org/archive/c08/c08_020708_cpac2.rm?start=02:46:50&end=03:20:06

And then VLC throws this back at me:

> live555: Nothing to play for rtsp://video.c-span.org/archive/c08/c08 ... d=03:20:06
main: no suitable decoder module for fourcc `RV40'.
VLC probably does not support this sound or video format.
main: no suitable decoder module for fourcc `sipr'.
VLC probably does not support this sound or video format.



Trying to get Mplayer to play the same stream using:

```
mplayer -playlist rtsp://video.c-span.org/archive/c08/c08_020708_cpac2.rm?start=02:46:50&end=03:20:06
[3] 18189

```

Throws this back at me:

> me@mybox:~/Desktop$ MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium M Dothan (Family: 6, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


STREAM_RTSP, URL: rtsp://video.c-span.org/archive/c08/c08_020708_cpac2.rm?start=02:46:50
Resolving video.c-span.org for AF_INET6...
Couldn't resolve name for AF_INET6: video.c-span.org
Resolving video.c-span.org for AF_INET...
Connecting to server video.c-span.org[12.170.145.134]: 554...
Cache size set to 640 KBytes


And then mplayer just hangs at this point.

Unfortunately a Google search does not return much.
Is there no free media player that can play these types of streams?
The thought of installing Real Player makes my stomach turn inside out.

Thank you for your time,

---

