---
title: "uShare &amp; media from Windows partiton"
date: 2009-04-26
forum: Multimedia Software
---

### Post by timstone on 2009-04-26
Is there a way to share media files from a windows partition with uShare?

In ushare.conf i've tried adding my XP directory

```
# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/media/XP/Documents and Settings/Tim/Desktop/Music 
```

but keep getting this when trying to run uShare

```
tim@tim-desktop:~$ sudo /etc/init.d/ushare start
 * Starting uShare UPnP A/V & DLNA Media Server: ushare                         /etc/ushare.conf: 21: and: not found
 * No shares avalaible ...
                                                                         [ OK ]

```

---

