---
title: "mplayer live stream"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by andrei048 on 2007-05-07
Hello! I have isntalled mplayer and the codec pack using automatix. I can play most videos, but i get this when trying to play some links.

```
Win32 LoadLibrary failed to load: avisynth.dll
```

and the full output is this:

```
~$ mplayer http://www.theloltv.com/video7.asx
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing http://www.theloltv.com/video7.asx.
Resolving www.theloltv.com for AF_INET6...
Couldn't resolve name for AF_INET6: www.theloltv.com
Resolving www.theloltv.com for AF_INET...
Connecting to server www.theloltv.com[91.121.34.40]: 80...
Cache size set to 320 KBytes
Cache fill:  0.13% (419 bytes)   
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll


Exiting... (End of file)

```

Thanx.

---

### Post by alef13 on 2007-05-12
try -playlist !

---

### Post by samitheberber on 2007-07-18
> **alef13 said:**
> try -playlist !
This worked with me. Thanks a lot!

---

