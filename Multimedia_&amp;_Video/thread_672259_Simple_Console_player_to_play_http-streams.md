---
title: "Simple Console player to play http-streams?"
date: 2008-01-19
forum: Multimedia &amp; Video
---

### Post by jo.angel on 2008-01-19
I am trying to write a script to rip predefined audio streams. I havn`t found yet a solution to integrate a very simple console tool, which can just play an audio stream (and not more) while I am ripping (based on streamripper.:guitar:
  This tool should possibly be  some kind of basic console player standard on Linux/unix, so my script could work on other systems as well, without fulfilling additional dependencies.  
I can use `play`from the sox packet to play mp3 from my harddrive, but streaming doesnt seem possible.
Am I asking for too much or did my researches just miss the most obvious point?

Many thanks in advance,

jo.angel

---

### Post by mouseboyx on 2008-01-19
mplayer streamfile.m3u

---

### Post by jo.angel on 2008-01-19
Tried this before - thgis is what I get: (no firewall problem)

mplayer [http://www.distler-tontechnik.de/Radio-Z-Live.m3u](http://www.distler-tontechnik.de/Radio-Z-Live.m3u)
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz (Family: 6, Model: 15, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing [http://www.distler-tontechnik.de/Radio-Z-Live.m3u](http://www.distler-tontechnik.de/Radio-Z-Live.m3u).
Resolving [www.distler-tontechnik.de](www.distler-tontechnik.de) for AF_INET6...
Couldn't resolve name for AF_INET6: [www.distler-tontechnik.de](www.distler-tontechnik.de)
Resolving [www.distler-tontechnik.de](www.distler-tontechnik.de) for AF_INET...
Connecting to server [www.distler-tontechnik.de](www.distler-tontechnik.de)[80.152.137.24]: 80...
Cache size set to 320 KBytes

Any idea why I canz open the socket?

---

