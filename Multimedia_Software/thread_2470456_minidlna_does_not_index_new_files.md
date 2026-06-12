---
title: "minidlna does not index new files"
date: 2021-12-30
forum: Multimedia Software
---

### Post by emoxam on 2021-12-30
I've got kubuntu 21.10 and Package: minidlna Version: 1.3.0+dfsg-2 it seems minidlna does not index new files!


```
cat /etc/minidlna.conf | grep media_dir 
media_dir=/mnt/250 media_dir=/home/minidlna media_dir=/media/mike/500


cat /etc/minidlna.conf | grep inotify
inotify=yes


mount | grep /mnt/250 /dev/sdb1 on /mnt/250 type fuseblk (rw,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096)
```
thats NTFS volume


I want this folder works.


But this one - does not too - /home/minidlna - EXT4 root partiton.


Only restarting the minidlna reindexes new files.


Thanks

---

### Post by emoxam on 2021-12-31
it seems that it's LG TV issue. After leaving current DLNA server to DLNA servers listm and entering DLNA server again new conten become visiblem without restarting DLNA server.

---

