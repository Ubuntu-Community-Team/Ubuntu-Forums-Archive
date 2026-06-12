---
title: "Restoring database from unbootable 9.04 partition?"
date: 2010-04-02
forum: Mythbuntu
---

### Post by JMcFly on 2010-04-02
Something happened to my 9.04 backend when I ran update manager earlier this week resulting in it no longer booting (I think something's wrong with fstab, but it scrolls too quickly for me to catch the actual start of the error before the screen's filled with junk).  I made a 9.10 disk and installed it, repartitioning my 9.04 drive (recordings were safe on a dedicated drive) to make room for it. 

I can mount the 9.04 partition and check out any files on it that I want, I can also mount and browse my recordings drive, but the 9.04 partition will not boot, even in recovery mode.  

Is there anyway to migrate my database from the 9.04 partition and merge it into the 9.10 database? All of the instructions I can find for migrating assume you're able to boot the old system.

---

### Post by nickrout on 2010-04-02
If you formatted the 9.04 partition (specifically /var/lib/mysql ) you have destroyed your database.

If you didn't you should mount your old root partition and then chroot into it and back up the database using the provided routines.

---

### Post by Lepy on 2010-04-02
Check the wiki: [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

If you have followed these directions previously (or have a manual backup of the database), you could easily edit fstab to mount your recording partitions in the new install to the same paths as under your 9.04 install and run a restore. 

If not, hopefully you have not formated the 9.04 partition, and you can chroot and backup the database as nick suggested.

If this is not the case, I think you are out of luck. Hopefully a lesson learned, so make sure to backup your database daily!

---

### Post by JMcFly on 2010-04-02
Thanks, I didnt know chroot was an option ](*,)
A little messing around and I have all my recordings back where they belong, had to repair the database as well because it was marked as crashed and I do not have sound and the video stutters within myth but both are fine in VLC. Typical Myth...

---

### Post by nickrout on 2010-04-03
logs?

---

### Post by JMcFly on 2010-04-04
I'll have to post the logs in a week, leaving on vacation in an hour, but which ones would be helpful?

---

### Post by nickrout on 2010-04-04
the frontend log

---

### Post by JMcFly on 2010-04-13
Solved the problem by removing the standard fglx driver and loading the RadeonHD driver for the ATI x1650, Newegg just dropped off my new MCE USB remote to replace the 1600's non-MCE remote which is not functional in 9.10 (or 10.04 from what I hear). I had to tweak the gamma settings but other than that I'm 100% functional again.

---

