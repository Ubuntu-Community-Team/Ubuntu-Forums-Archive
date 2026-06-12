---
title: "locked DVB-S SkyStar2 card"
date: 2010-07-27
forum: Multimedia Software
---

### Post by ddragas on 2010-07-27
Hi all

I've installed MythTV on my HTPC and setup-ed program channels for terestrial and satelite (SkyStar2) receivers

On satelite reciver I have 2 diseque's 
1. is for Astra 19.2
2. is for HotBird 13.0

I've managed to scan for Astra but when I try to scan for HotBird I get following error

```


silver@HTPC:~$ scan /usr/share/dvb/dvb-s/Hotbird-13.0E > channels.conf
scanning /usr/share/dvb/dvb-s/Hotbird-13.0E
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2273: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 16 Device or resource busy



```

It seams that card is locked by some process

How can I unlock card?

---

