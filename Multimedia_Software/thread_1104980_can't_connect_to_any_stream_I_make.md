---
title: "can't connect to any stream I make"
date: 2009-03-24
forum: Multimedia Software
---

### Post by oyankee on 2009-03-24
Hi, this is my problem>

I made vlc stream through http like this > [http://www.n00tz.net/2008/07/vlc-media-server-ubuntu-hardy/]("http://www.n00tz.net/2008/07/vlc-media-server-ubuntu-hardy/")

I start it for example at udp://192.168.6.60:1234 and I can play it at this port from this local machine using mplayer or xine. But when I try to play it on machine on lan, this is what mplayer says>

> onovotny@S-012-09:~$ mplayer udp://192.168.6.60:1234
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E7300  @ 2.66GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing udp://192.168.6.60:1234.
STREAM_UDP, URL: udp://192.168.6.60:1234
Failed to connect to server
udp_streaming_start failed
No stream found to handle url udp://192.168.6.60:1234


No firewall is installed on that 'server'. But why I can't connect?
Thanks for help

---

### Post by albandy on 2009-03-24
are you sure your router is not blocking udp connections?

---

### Post by oyankee on 2009-03-24
Yes, I'm sure. rtp should also work, but not. I tried it from another computer through quick time stream server and it worked.



EDIT> No, I'm sorry. You were right I think. I tried it through http an it works. Thank you.

---

