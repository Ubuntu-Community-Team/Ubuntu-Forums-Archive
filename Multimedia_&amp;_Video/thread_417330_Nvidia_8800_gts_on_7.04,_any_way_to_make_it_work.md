---
title: "Nvidia 8800 gts on 7.04, any way to make it work?"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by atlings on 2007-04-21
Hi, I've seen a lot of posts about Nvidia card trouble on 7.04, but no solution that has worked for me yet. The x server doesn't start, unless I change the "nvidia" entry in xorg.conf to plain "nv". Does anybody have any tips? I've tried Envy and so on already. BTW, I'm a total Linux noob, so please be spesific :p

---

### Post by GeDaMo on 2007-04-22
I believe a couple of files are missing from nvidia-glx-new / restricted modules which are required by the 8800.

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641)
[http://www.nvnews.net/vbulletin/showthread.php?t=83214](http://www.nvnews.net/vbulletin/showthread.php?t=83214)

---

### Post by shrisha on 2007-04-22
check here [http://ubuntuforums.org/showthread.php?t=413961&page=3&highlight=8800](http://ubuntuforums.org/showthread.php?t=413961&page=3&highlight=8800)

---

