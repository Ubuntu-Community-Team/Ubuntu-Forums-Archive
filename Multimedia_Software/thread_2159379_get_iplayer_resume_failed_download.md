---
title: "get_iplayer resume failed download"
date: 2013-07-02
forum: Multimedia Software
---

### Post by rsd-17 on 2013-07-02
I'm using get_iplayer version 2.82.

I occasionally see error messages like these:

[I]813979.979 kB / 2482.20 sec (69.9%)
ERROR: RTMP_ReadPacket, failed to read RTMP packet header
814117.019 kB / 2482.68 sec (69.9%)^C
Caught signal: 2, cleaning up, just a second...
814117.019 kB / 2482.68 sec (69.9%)
Download may be incomplete (downloaded about 69.90%), try resuming

INFO: Cleaning up (signal = INT), killing PID=14582:...[/I]

I've looked, but I can't find anything documented that smells like a resume switch.
Am I blind, or is anyone else having this problem? Solutions anyone?

---

### Post by ron999 on 2013-07-03
> **rsd-17 said:**
>  I'm using get_iplayer version 2.82.
Solutions anyone?
Upgrade to  v2.83 first.
```
@ubuntu:~$ get_iplayer
get_iplayer v2.83, Copyright (C) 2008-2010 Phil Lewis
```

---

### Post by dinkypumpkin on 2013-07-03
get_iplayer always configures rtmpdump to resume on glitches in catch-up programme downloads, though there is no guarantee a given recording can successfully be resumed.  It depends on the state of the partially-downloaded file.   The resume option is ignored by rtmpdump for live recording or streaming to an external player.

---

