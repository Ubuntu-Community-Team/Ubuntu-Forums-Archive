---
title: "can't delete recorded files"
date: 2009-12-24
forum: Mythbuntu
---

### Post by neutron68 on 2009-12-24
I'm running Mythbuntu 9.10 and I am trying to delete recorded shows (using the i key in the Manage Recordings screen).  It looks like they are going to delete, but they never get deleted.  Has this happened to anyone else?  How can I "gracefully" delete them, so the database gets updated with their deletion?

The files I want to delete are
```
eric@Mythbuntu8:/var/lib/mythtv/recordings$ ls -l
total 56964524
-rw-r--r-- 1 mythtv mythtv           0 2009-09-19 21:51 1021_20090919215107.mpg
-rw-r--r-- 1 mythtv mythtv 13553152368 2009-09-27 21:00 1021_20090927190000.mpg
-rw-r--r-- 1 mythtv mythtv        9533 2009-09-27 21:23 1021_20090927190000.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv       81622 2009-12-24 18:07 1021_20090927190000.mpg.png
-rw-r--r-- 1 mythtv mythtv 16531093612 2009-09-29 00:00 1021_20090928213000.mpg
-rw-r--r-- 1 mythtv mythtv       14362 2009-10-03 20:48 1021_20090928213000.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv       87490 2009-12-24 18:07 1021_20090928213000.mpg.png
-rw-r--r-- 1 mythtv mythtv 13401413996 2009-09-29 21:00 1021_20090929190000.mpg
-rw-r--r-- 1 mythtv mythtv       11225 2009-10-03 20:48 1021_20090929190000.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv       86432 2009-12-24 18:07 1021_20090929190000.mpg.png
-rw-r--r-- 1 mythtv mythtv 13379082416 2009-09-30 21:00 1021_20090930190000.mpg
-rw-r--r-- 1 mythtv mythtv       14083 2009-10-03 20:48 1021_20090930190000.mpg.100x56.png
-rw-rw-rw- 1 mythtv mythtv      128287 2009-12-24 18:07 1021_20090930190000.mpg.png
-rw-r--r-- 1 mythtv mythtv           0 2009-10-10 14:36 1021_20091010143640.mpg
-rw-r--r-- 1 mythtv mythtv    30344516 2009-10-10 14:37 1021_20091010143642.mpg
-rw-r--r-- 1 mythtv mythtv           0 2009-12-24 18:10 1021_20091224181039.mpg
-rw-r--r-- 1 mythtv mythtv    52419476 2009-12-24 18:11 1021_20091224181040.mpg
-rw-r--r-- 1 mythtv mythtv     1944108 2009-09-19 21:51 1024_20090919215058.mpg
-rw-rw-rw- 1 mythtv mythtv       63769 2009-09-19 21:51 1024_20090919215058.mpg.png
-rw-rw-rw- 1 mythtv mythtv       72238 2009-04-05 00:05 1051_20090404233500.mpg.png
-rw-r--r-- 1 mythtv mythtv  1366120800 2009-11-12 22:30 2079_20091112221200.mpg
-rw-rw-rw- 1 eric   mythtv       85333 2009-11-14 16:35 2079_20091112221200.mpg.png
-rw-r--r-- 1 mythtv mythtv     2702643 2009-10-28 20:40 mythconverg-1214-20091028204007.sql.gz
-rw-r--r-- 1 eric   mythtv     2703958 2009-10-28 20:42 mythconverg-1244-20091028204207.sql.gz
-rw-r--r-- 1 eric   mythtv     9985468 2009-11-02 20:52 mythconverg-1244-20091102205227.sql.gz
```

Thanks,
Eric

---

### Post by SiHa on 2009-12-26
Are these, by any chance, recordings migrated from a previous install?

I found that I had exactly this problem with migrated recordings, the permissions were wrong, for some reason. ```
chmod 666 *.mpg *.png
```...should allow you to delete the recordings from the frontend.

Edit: Just another thought, it might be that you have 'Auto-Expire instead of delete' checked in the frontend setup screens, can't remember where it is though, probably TV Settings -> General.

---

### Post by neutron68 on 2009-12-26
It turned out that the files eventually deleted.  It took several minutes from clicking DELETE for each file to be removed from the list.

I've always had Mythtv set to "DELETE FILES SLOWLY", but I've never seen any files take so long to disappear from the list before.  Maybe the speed of deleting is a Myth 0.22 version difference?

Eric

---

### Post by Zeedok on 2009-12-28
> **SiHa said:**
> Are these, by any chance, recordings migrated from a previous install?

I had this very issue with new recordings, but my setup is an upgrade from 9.04 to 9.10 MythBuntu.

> **SiHa said:**
> I found that I had exactly this problem with migrated recordings, the permissions were wrong, for some reason. ```
chmod 666 *.mpg *.png
```...should allow you to delete the recordings from the frontend.

This worked for me, but  . . .

> **SiHa said:**
> Edit: Just another thought, it might be that you have 'Auto-Expire instead of delete' checked in the frontend setup screens, can't remember where it is though, probably TV Settings -> General.

I didn't have this selected.

Thanks for the tip.

---

