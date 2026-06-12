---
title: "vanilla kernel problems"
date: 2006-08-10
forum: Multimedia &amp; Video
---

### Post by mixandgo on 2006-08-10
Hello,

I've installed the vanilla kernel (2.6.17) with the realtime ( rt8 ) patch on  my ubuntu dapper, following the instructions from ubuntustudio.com.
Everything seems to work ok, but I don't see my audio interface no more (rme multiface II/cardbus).

Thanks.

---

### Post by floogy on 2006-08-13
You may find your card in the alsa matrix:
[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-RME#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-RME#matrix)

```
 egrep -i "(hdsp|rme)" /boot/config-`uname -r`|grep -v HERMES
```
Tells you, if you've got your card enabled by `make menuconfig` .
```
modprobe -l | egrep -i "(hdsp|rme)"
```
gives similar info.

---

