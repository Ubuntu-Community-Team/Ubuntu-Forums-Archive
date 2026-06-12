---
title: "MPlayer problem with Firefox--help please!"
date: 2008-03-18
forum: Multimedia &amp; Video
---

### Post by caljohnsmith on 2008-03-18
I can't seem to get my MPlayer fully functional in Firefox. I'm trying to view this video:

[http://newyears.earthcam.com/ts/](http://newyears.earthcam.com/ts/)

Note that it begins with an ad and then it switches over to a mms stream of the main video (or at least it's supposed to). For me, it just perpetually says that it is trying to connect to the server.

I copied the URL it is trying to access:
[http://wms1.earthcam.com/events/nye/2008/balldrop_multi.wmv?MSWMExt=.asf](http://wms1.earthcam.com/events/nye/2008/balldrop_multi.wmv?MSWMExt=.asf)
And tried to open it manually with Mplayer at the command line. Still no go, here is what it says:

==========================================
john@HOME1:/$ mplayer [http://63.229.55.52/events/nye/2008/balldrop_multi.wmv?MSWMExt=.asf](http://63.229.55.52/events/nye/2008/balldrop_multi.wmv?MSWMExt=.asf)
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) Processor (Family: 6, Model: 4, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 0 SSE2: 0
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing [http://63.229.55.52/events/nye/2008/balldrop_multi.wmv?MSWMExt=.asf](http://63.229.55.52/events/nye/2008/balldrop_multi.wmv?MSWMExt=.asf).
Resolving 63.229.55.52 for AF_INET6...
Couldn't resolve name for AF_INET6: 63.229.55.52
Connecting to server 63.229.55.52[63.229.55.52]: 80...
Cache size set to 320 KBytes


Playing [http://63.229.55.52/events/nye/2008/balldrop_multi.wmv?MSWMExt=.asf](http://63.229.55.52/events/nye/2008/balldrop_multi.wmv?MSWMExt=.asf).
Resolving 63.229.55.52 for AF_INET6...
Couldn't resolve name for AF_INET6: 63.229.55.52
Connecting to server 63.229.55.52[63.229.55.52]: 80...
Cache size set to 320 KBytes


MPlayer interrupted by signal 2 in module: handle_playlist
=================================
Any ideas? Thanks for any help!

---

