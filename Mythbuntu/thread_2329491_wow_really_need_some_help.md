---
title: "wow really need some help"
date: 2016-07-02
forum: Mythbuntu
---

### Post by benlyboy on 2016-07-02
i have a myth back end running what i think is 14.04.2  that was working great till yesterday i think it may have updated. Now when it boots it ends up in busybox.  im way out of my death on this one. if it was my system i would just reinstall and move on...But the system is one i set up for my grandparents, and they really don't want to lose there programs. The recordings are all on a different disk so they are ok, but if i reinstall there is no way to reintegrate them into the system. so i need to try and save this instillation if i can.

i read on like you you can use a instillation drive to do a restore, but wgen i get to that section where it should give me that choice, its not seeing that linux is even installed.

ii would be very grateful for any help thanksi

ok i have done some more digging and have just about decided that its a bas ssd , thats bad new as it most like means i cant save the install, so i guess if thats the case im looking at a fresh install, is there any way to reinstall there recordings, i mean i can drop the dish with att the recordings back in thats easy but how do i set up myth to see them?
 
,

---

### Post by TheFu on 2016-07-02
Fresh install? Why? Just restore from a backup.

I'd nuke it from orbit and reload from a backup prior to the issue.  Versioned backups are fantastic!  Go back a few days and if that isn't sufficient, go back a week or two.  I only keep 2 months of daily backups for unimportant systems, so going back beyond 2 months would be an issue for me.  Fortunately, all you need is the most recent backup that solves this issue. 

If there aren't any backups things become exponentially harder, but if the disk(s) are still spinning, you can get some, much, most, almost all of the data off - how much depends on the failure of the HDD.  All it takes is money and time.

---

### Post by benlyboy on 2016-07-02
As the system is not at home but at my grandparents there are no backup, thats on me:( the disk is a ssd i managed to get it to mount on to one of my systems but can only see some of the files, a lot seem to be missing. any way to move that data base by moving files...?

---

### Post by aelfric55 on 2016-07-03
The raw mythconverg database is to be found under /var/lib/mysql  If none of the automatic mythconverg backups that your system should have been making survived, you will find a directory in /var/lib/mysql called "/mythconverg" You'll needa  this directory and all the files in it. If your crippled installation can recover and retrieve  all these files, you stand a reasonably good chance of being able to plug this directory into a new clean installation, and, once the ownership/permissions on the files and directory are set properly, getting mysql to recognize and manipulate this patched-in database. If a few of the tables turn out to be missing or damaged, you may still end up OK after using the normal mysqlcheck repair routines to repair/reconstitute tables that may be damaged or missing.

Once you get a new mythtv installation you can live with, and have updated it to a stable point, you may wish to consider disabling automatic updates, since this is a system you can't monitor and administer directly most of the time, and some updates will inevitably break things. Save further updating for times when you are physically present to clean up the rubble afterward. Also you may wish to use a simple 3-or-4-line mysqldump backup script to make sure recent mythconverg backups are available when you need them. Such a script could dump copies of the mythconverg backup into your recordings directories, since recordings without a mythconverg are a monumental pain to inventory and use, while if the drive(s) with your recordings on it also fries and dies, you won't have much use for a mythconverg backup anyway. Assuming, of course, that you keep your system and your recordings directory  on separate physical drives.

---

