---
title: "OSSv4 install problems"
date: 2008-03-12
forum: Multimedia &amp; Video
---

### Post by Revenant86 on 2008-03-12
Well, I was followings Temujins guide to install OSSv4 at [http://ubuntuforums.org/showthread.php?t=599320&highlight=Sound+Issues&page=6](http://ubuntuforums.org/showthread.php?t=599320&highlight=Sound+Issues&page=6) (last post on page) and I did everything up to sudo soundon. When I typed soundon in it said that the alsa drivers were still loaded. I tried rebooting once again, just to make sure, and soundon crashed the system. Any ideas?

---

### Post by krylon on 2008-03-13
Try

```
sudo /etc/init.d/alsa-utils stop
sudo soundon

```

---

