---
title: "Dish Network DVR (VIP622) External HD and Linux"
date: 2008-01-23
forum: Multimedia &amp; Video
---

### Post by Admoseley on 2008-01-23
I have dish network, and their VIP622 Dvr console.
This DVR allows you to attach an external hard drive of your choosing to be able to record/move your shows for extra storage. This is great and it works like it should...

I've removed the HD and attached it back to my Ubuntu 7.10 system.. The File system is ext3 and I am able to read the FS... But can i play these shows from my computer.. if so how?

The disk was formatted by the DVR, and created the following directories under the DishArc folder (These are my Terminator: Sarah Connor Chronicles shows)

user@ub710:/media/disk-2$ ls -lR ./
./:
total 20
drwxr-xr-x 5 root root  4096 1999-12-31 18:36 DishArc
drwx------ 2 root root 16384 2000-01-01 12:20 lost+found

./DishArc:
total 12
drwxr-xr-x 2 root root 4096 1999-12-31 18:49 205b2ec0
drwxr-xr-x 2 root root 4096 1999-12-31 18:36 205d3ec0
drwxr-xr-x 2 root root 4096 1999-12-31 18:23 206b3ec0

./DishArc/205b2ec0:
total 4344392
-rw-r--r-- 1 root root       3576 1999-12-31 18:49 bm
-rw-r--r-- 1 root root        560 1999-12-31 18:49 cat
-rw-r--r-- 1 root root 4440866816 1999-12-31 18:49 tsp
-rw-r--r-- 1 root root    3428352 1999-12-31 18:49 wtt

./DishArc/205d3ec0:
total 3858460
-rw-r--r-- 1 root root       3576 1999-12-31 18:36 bm
-rw-r--r-- 1 root root        560 1999-12-31 19:06 cat
-rw-r--r-- 1 root root 3943800832 1999-12-31 18:36 tsp
-rw-r--r-- 1 root root    3391488 1999-12-31 18:36 wtt

./DishArc/206b3ec0:
total 3814808
-rw-r--r-- 1 root root       3576 1999-12-31 18:23 bm
-rw-r--r-- 1 root root        560 1999-12-31 18:23 cat
-rw-r--r-- 1 root root 3899138048 1999-12-31 18:23 tsp
-rw-r--r-- 1 root root    3399680 1999-12-31 18:23 wtt
ls: ./lost+found: Permission denied


bm, cat, tsp, and wtt ??? crazy file names that dont look like much.. I figured to tsp file must be the actual show just because it is the largest... but this might encrypted in some way.. hopefully this looks remotely familar to someone that may be able to point me in the right direction.. Eventually I just want to burn these to disk.


Thanks in advance.

---

### Post by flat4 on 2008-06-12
i have trying to find a way to convert the file for dvd burning, anyhow someone said that vlc should be able to play it.

---

