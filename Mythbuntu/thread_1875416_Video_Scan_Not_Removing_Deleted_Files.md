---
title: "Video Scan Not Removing Deleted Files"
date: 2011-11-04
forum: Mythbuntu
---

### Post by fullmoonguru on 2011-11-04
New videos appear but some old ones won't go away.  I think it has to do with some backup/restore operations I did.  I tried fixing the tables but no luck.  I actually renamed the entire folder & the old folder & files are still listed when I scan.

---

### Post by fdrake on 2011-11-04
2 cases are possible:
1. the files are being used by another process
2. you don't have the right permissions to remove them.
(3.they have a bit-block enabled)

can you post the "ls -l" of you folder?

---

### Post by fullmoonguru on 2011-11-05
```
drwxrwxrwx 5 mammy mammy 4096 2011-10-29 15:35 Griffin
drwxrwxrwx 8 mammy mammy 4096 2011-10-11 22:51 Home Videos
drwxrwxrwx 6 mammy mammy 4096 2011-11-02 10:50 Jeseph's Movies
drwxr-xr-x 4 mammy mammy 4096 2011-11-02 10:49 J's Movies
drwxrwxrwx 5 mammy mammy 4096 2011-11-05 21:47 Torrent Downloads
drwxrwxrwx 7 mammy mammy 4096 2011-08-27 13:50 Watched Movies
```

---

### Post by fdrake on 2011-11-06
can you try to remove Griffin folder (or another old folder/movie)
```

rm -vr Griffin
ls -l

```
if you have any errors, post them here.

---

### Post by fullmoonguru on 2011-11-06
Not sure why I'm doing this.  Remvoing files from the desktop is not a problem.  I forgot to mention that mythtv is in the mammy group.  Thanks for your help.


```
mammy@mammy:/media/Data/mythtv/videos/Griffin$ rm -vr Shrek.avi
removed `Shrek.avi'
mammy@mammy:/media/Data/mythtv/videos/Griffin$ ls -l
total 21749676
-rwxrwxrwx 1 mammy mammy  728705294 2009-11-12 15:05 A Bugs Life.avi
-rwxrwxrwx 1 mammy mammy 1777355195 2010-06-03 10:36 Advantures of Milo & Otis.m4v
-rwxrwxrwx 1 mammy mammy  811525260 2010-01-03 00:40 Chicken Run.avi
-rwxrwxrwx 1 mammy mammy  756622489 2010-03-14 10:59 Curious George.m4v
drwxrwxrwx 2 mammy mammy       4096 2010-07-31 08:07 Disney Classics
-rwxrwxrwx 1 mammy mammy  725874688 2009-11-12 14:51 Finding Nemo.avi
-rwxrwxrwx 1 mammy mammy  733693952 2010-01-13 22:14 Flushed.Away.avi
-rwxrwxrwx 1 mammy mammy 1139113658 2008-07-23 05:30 Ice Age 2 - The Meltdown.avi
-rwxrwxrwx 1 mammy mammy  733190144 2009-11-19 14:22 Ice Age 3 - Dawn Of The Dinosaurs.avi
-rwxrwxrwx 1 mammy mammy  962831508 2008-07-23 05:29 Ice Age.avi
-rwxrwxrwx 1 mammy mammy  734892032 2010-01-13 20:47 Madagascar 2 - Escape From Africa.avi
-rwxrwxrwx 1 mammy mammy  735746048 2010-01-13 21:27 Madagascar.avi
-rwxrwxrwx 1 mammy mammy  372007488 2010-11-19 21:49 Operation Christmas Child.avi
-rwxrwxrwx 1 mammy mammy 1079428239 2010-12-12 15:22 Polar Express.m4v
-rwxrwxrwx 1 mammy mammy  736024576 2010-01-13 22:23 Ratatouille.avi
-rwxrwxrwx 1 mammy mammy  734117888 2010-01-13 21:59 Shrek 2.avi
-rwxrwxrwx 1 mammy mammy  734230528 2010-01-13 20:56 Shrek 3.avi
-rwxrwxrwx 1 mammy mammy  717381632 2009-11-12 15:03 The Incredibles.avi
drwxrwxrwx 7 mammy mammy       4096 2010-02-21 16:11 The Muppet Show
-rwxrwxrwx 1 mammy mammy 1171984384 2008-10-30 23:10 The Water Horse.avi
drwxrwxrwx 2 mammy mammy       4096 2010-02-20 19:39 The Wizard of Oz
-rwxrwxrwx 1 mammy mammy  737748992 2009-11-12 14:38 Toy Story 2.avi
-rwxrwxrwx 1 mammy mammy  734418944 2009-11-12 14:57 Toy Story.avi
-rwxrwxrwx 1 mammy mammy  735990840 2010-01-02 23:48 Up.avi
-rwxrwxrwx 1 mammy mammy 1249772610 2010-08-09 23:37 Wallace And Gromit - Curse of the Were Rabbit.m4v
-rwxrwxrwx 1 mammy mammy  390153508 2010-08-03 22:46 Wallace & Gromit - A Matter of Loaf and Death.m4v
-rwxrwxrwx 1 mammy mammy 1467629454 2008-10-21 02:17 Wall-E.avi
-rwxrwxrwx 1 mammy mammy 1571071941 2010-05-22 12:32 Willy Wonka.m4v
 
```

---

### Post by fdrake on 2011-11-06
are u able to watch the movie cars in myth? maybe the file is in cache state, and it is not sync to the folder index correctly?

---

### Post by fullmoonguru on 2011-11-06
Sorry, I edited the post above becaus I figured you intended me to remove a file that was there instead of trying to remove a file from the command line that had already been removed.

Once I delete the files they don't even start in Myth.

---

### Post by Slacker3k on 2011-11-08
Is there a chance that when you did your backup/restore that the name of the machine has changed?  Mythvideo stores the path to videos using the hostname, and will only delete files that it doesn't find when it rescans the original host.  If that's the case, the easiest way to remove them is with SQL.

(This is much better than before where it always deleted if it couldn't find it - which meant a backend that was offline would cause a lot of things to be deleted.)

---

### Post by fullmoonguru on 2011-11-12
Same hostname.  How would I delete them through SQL?

---

### Post by nickrout on 2011-11-13
The videos are in the videometadata table.

---

### Post by fullmoonguru on 2011-11-14
Emptying the table and rescanning did it.  Thanks very much!

---

