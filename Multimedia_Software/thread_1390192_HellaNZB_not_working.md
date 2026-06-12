---
title: "HellaNZB not working"
date: 2010-01-25
forum: Multimedia Software
---

### Post by junke1990 on 2010-01-25
Hey guys

I'm running Debian on a little Sheeva plug, a ARM based little home server. I recently started to use the news servers and want to use my home server to download and place them on my (shared) hard drives.

I can't get it to work. I have configured the /etc/hellanzb.conf but when I start it it just bumps out:
```
junke@debian:~$ hellanzb 

hellanzb v0.13 (config = /etc/hellanzb.conf, C yenc module)
junke@debian:~$
``` 


I made a debug log that only shows the following:
```
2010-01-25 17:17:37,403 hellanzb v0.13 (config = /etc/hellanzb.conf, C yenc module)
2010-01-25 17:17:37,481 Using: Twisted-8.1.0, TwistedWeb-8.1.0
2010-01-25 17:17:37,483 python: 2.5.2 (r252:60911, Jan  5 2009, 02:00:00) 
2010-01-25 17:17:37,484 [GCC 4.3.2]
2010-01-25 17:17:37,485 os: Linux-2.6.29-2-kirkwood (armv5tel)
2010-01-25 17:17:37,486 initFillServers: fillserver support disabled
```

---

