---
title: "Upgrade to 10.10 FAILED.  Now the system is screwed"
date: 2010-11-30
forum: Mythbuntu
---

### Post by MonsterMaxx on 2010-11-30
I ran the update to 10.10 and it failed.  Now the system won't update anything, won't complete the upgrade and is pretty much hosed.

Anything I can do or is my entire myth backend gone?

---

### Post by thatguruguy on 2010-11-30
Did you upgrade to 10.10 from 10.04, or did you do a new install?

Do you have your /home directory on a separate partition?

---

### Post by MonsterMaxx on 2010-11-30
upgrade from 10.04

no, home is on the main partition

I can't even get to a terminal window w/o killing x all together

---

### Post by 0N3 on 2010-11-30
You should always do a fresh install as its not uncommon upgrade fail and id definitely look into creating 3 partitions in future that way you keep your settings. Use a live Cd if you have one to get what you need back. 
And good luck!

---

### Post by thatguruguy on 2010-11-30
> **0N3 said:**
> You should always do a fresh install as its not uncommon upgrade fail and id definitely look into creating 3 partitions in future that way you keep your settings. Use a live Cd if you have one to get what you need back. 
And good luck!

This.

If you run a live CD, you should still be able to mount your drive and get your data.  Now would be a good time to back it up, if you don't already have a back-up.  Then, do a fresh install of 10.10 on the system, and make sure you put your /home directory in a separate partition.  I only allocate 10-15 gigs for my root directory (including all my programs), 4 gigs or so for my swap file, and allocate the rest of my disk to /home.  After you've done the fresh install, you can restore all your data from the back-up you just made.

---

### Post by nickrout on 2010-11-30
> **thatguruguy said:**
> This.

If you run a live CD, you should still be able to mount your drive and get your data.  Now would be a good time to back it up, if you don't already have a back-up.  Then, do a fresh install of 10.10 on the system, and make sure you put your /home directory in a separate partition.  I only allocate 10-15 gigs for my root directory (including all my programs), 4 gigs or so for my swap file, and allocate the rest of my disk to /home.  After you've done the fresh install, you can restore all your data from the back-up you just made.
you really really need to back up the database too. Use these utilities (and ONLY these utilities!!)

[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

---

