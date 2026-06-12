---
title: "youtube flash videos"
date: 2011-02-23
forum: Multimedia Software
---

### Post by linuxien. on 2011-02-23
i am running ubuntu 10.10 and wanna download youtube flash videos, i acted like this:
to get the firefox PID i used the command ps 
£  ps -ef | grep firefox
then
ls -lu /proc/pid (its a number) /fd  grep flash*
normally it may give something like /tmp/flashGYPxSW    but it gives nothing the video is maybe deleted 
i dont know why? anyone has ever used this method i am waiting you help

---

### Post by An Sanct on 2011-02-23
Why don't you use [Download Helper]("http://www.downloadhelper.net/")? It automates video download.

---

### Post by shantiq on 2011-02-24
youtube-dl is very good

```
youtube-dl -t url
```


will grab highest quality version
but you can downscale

```
youtube-dl -t -f 35  url    for 480


youtube-dl -t -f 28  url    for 720
```


also and a new discovery for me   [jdownloader]("http://jdownloader.org/")

---

### Post by lisati on 2011-02-24
It's against the Youtube terms of service to download videos using means other than their "approved" players.

Thread closed.

---

