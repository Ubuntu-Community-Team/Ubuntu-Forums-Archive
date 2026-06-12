---
title: "mplayer hangs playing RTSP stream"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by looby on 2007-10-20
On my ubuntu 7.04 installation mplayer hangs playing any RTSP stream. This happens with mplayer 1.0rc1, rc2 and and latest svn source (dev-SVN-r24815-4.1.2). I have tried this with various RTSP streams that work fine with mplayer 1.0rc1 on Windows XP.

Note that mplayer pauses for quite some time at the output "Connecting to server...."

Help!!!!

The output is show below:

mplayer -playlist [http://www.bbc.co.uk/radio1/realaudio/media/r1live.rpm](http://www.bbc.co.uk/radio1/realaudio/media/r1live.rpm)
MPlayer dev-SVN-r24815-4.1.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU          6320  @ 1.86GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
Resolving [www.bbc.co.uk](www.bbc.co.uk) for AF_INET6...
Couldn't resolve name for AF_INET6: [www.bbc.co.uk](www.bbc.co.uk)
Resolving [www.bbc.co.uk](www.bbc.co.uk) for AF_INET...
Connecting to server [www.bbc.co.uk](www.bbc.co.uk)[212.58.251.201]: 80...
Cache size set to 320 KBytes

Playing rtsp://rmlive.bbc.co.uk/bbc-rbs/rmlive/ev7/live24/radio1/live/r1_dsat_g2.ra?BBC-UID=445721e95804a7bcb2abbda7409018eed29df136e0700194249f869f8234fcfb_n&SSO2-UID=.
Resolving rmlive.bbc.co.uk for AF_INET6...
Couldn't resolve name for AF_INET6: rmlive.bbc.co.uk
Resolving rmlive.bbc.co.uk for AF_INET...
Connecting to server rmlive.bbc.co.uk[212.58.227.86]: 554...

librtsp: server responds: 'rtOPTIONS * RTSP/1.0'
rtsp: read error.

MPlayer interrupted by signal 13 in module: open_stream
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

---

