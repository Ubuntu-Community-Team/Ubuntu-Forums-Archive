---
title: "SANSA M250 &quot;No space left on device&quot; after upgrade to 9.10"
date: 2010-04-20
forum: Multimedia Software
---

### Post by smcleish on 2010-04-20
I've just upgraded to kubuntu 9.10, and I'm getting strange errors when trying to copy files onto my MP3 player, a SANSA M250 (2GB). df claims it's at 57% capacity (and the figures make sense for that, as well as having about the quantity of music which half fills the SANSA) but when I try to copy a file - from the command line, from exaile, or with the file manager, I get a "No space left on device" error:

```
$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             73939452  42184580  27998880  61% /
udev                    512472       264    512208   1% /dev
none                    512472      1752    510720   1% /dev/shm
none                    512472        96    512376   1% /var/run
none                    512472         0    512472   0% /var/lock
none                    512472         0    512472   0% /lib/init/rw
/dev/sdc               1996000   1125056    870944  57% /media/SANSA M250
$ cp test.mp3 /media/SANSA\ M250/
cp: cannot create regular file `/media/SANSA M250/test.mp3': No space left on device
```

The MP3 being copied is 2MB in size so should fit easily.

There were no problems until upgrading, when I also moved from amarok to exaile - because amarok2 doesn't have the functionality I want from a player. But this happens even if exaile isn't running, so exaile shouldn't be the problem.

How can I diagnose what's going on, and (hopefully) fix it?

---

### Post by smcleish on 2010-05-06
I've fixed this problem - it's due to exaile's device managment script. This doesn't put the MP3 files on the player in separate directories, and the SANSA player only allows up to 128 files in a directory. So the device is "full" even though it still has empty space. Hierarchical organisation of files is a feature request on exaile, so it will eventually be sorted, but in the meantime manual sorting of files seems to be the way forward for me.

---

