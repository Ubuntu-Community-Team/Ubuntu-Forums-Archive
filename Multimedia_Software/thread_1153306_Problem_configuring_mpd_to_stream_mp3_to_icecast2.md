---
title: "Problem configuring mpd to stream mp3 to icecast2"
date: 2009-05-08
forum: Multimedia Software
---

### Post by retrovelo on 2009-05-08
Hi.

I'm having trouble getting mpd to stream in mp3 format to icecast. 

The machine is question is running Ubuntu 9.0.4 and version .14 of mpd.

According to the mpd wiki, this version should stream mp3 if the optional parameter 'encoding' is set to 'mp3' in the shout output section if mpd.conf. 

However, when the paramter is set, mpd returns the following error when started: 

```
 shout: couldn't find shout encoder plugin "mp3"

```

When I remove the parameter from mpd.conf, mpd streams fine, but only in Ogg format.

Any advice or direction to help me solve this problem is appreciated.




~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Solved: I compiled mpd from source and shout mp3 is enabled.

Only problem is that MPD v.14.2 and Icecast2 now claim ~40% CPU. With v.13.2, streaming Ogg, CPU hovers around ~4%.

As I compiled mpd from source, I now have two mpd executables -- the original v.13.2 (/usr/bin/mpd) and the freshly compiled v.14.2 (/usr/local/bin/mpd). Switching between them is as easy as changing the DAEMON path in the init script and restarting MPD.

---

