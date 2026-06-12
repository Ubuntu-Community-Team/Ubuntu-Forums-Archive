---
title: "[SOLVED] Upnp Disabled"
date: 2008-06-28
forum: Mythbuntu
---

### Post by CoNMaN on 2008-06-28
I am running Mythbuntu 8.04, frontend and backend.  Machine does no recording, just plays movies, and shows I put on it, and play on my TV.  Works great.  But I would like to use the upnp part to play some music/movies on my laptop.  

I have tried using mediacloud to view the upnp it sees nothing.  So checking the mythtvbackend.log i get this:

```

2008-06-27 21:23:39.641 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP

```

Can anyone explain what a loopback address is, and How can I not specify it so that I can have UPnp running?

---

### Post by ian dobson on 2008-06-28
Hi,

Go into myth-setup and set the IP address of the backend and this backend to be the same as external IP address. That should solve it for you.

Regards
Ian Dobson

---

### Post by CoNMaN on 2008-06-30
Thank you very much.  It now says in the log that Upnp is starting and finds my videos.
```

QDateTime::fromString: Parameter out of range
2008-06-30 07:10:54.522 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos/torrents:
2008-06-30 07:10:55.020 UPnpMedia: BuildMediaMap Done. Found 113 objects
2008-06-30 07:12:04.370 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
QDateTime::fromString: Parameter out of range
root@tv-machine:~# 

```

---

