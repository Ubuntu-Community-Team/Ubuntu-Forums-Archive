---
title: "any issues with 9.04 to 9.10?"
date: 2009-12-28
forum: Mythbuntu
---

### Post by drjenk on 2009-12-28
I am tempted to hit the "install" button when being prompted for the upgrade from 9.04 to 9.10, but am afraid because everything is working pretty good.  I would however like to take advantage of some of the mythtv .22 features, but keep thinking if something goes wrong with the upgrade I'll regret just leaving well enough alone.  I guess my question is should I be concerned with upgrading?  I have had almost no issues other than some occasional unexplained crashes of the frontend on my slave back end, but pretty few and far between.

---

### Post by mickie.kext on 2009-12-28
You better not upgrade if everything works well. 9.04 is still supported, you might go straight to Lucid Lynx when available. 

Karmic has regressions, and you can't see all benefits (like Ext4 and GRUB2) if you do not make clean install. So better stick with Jauntu until Lucid arrives.

---

### Post by drjenk on 2009-12-29
I will probably take that advice.

Do you know if, when doing a clean install, the database can be somehow exported, then imported on the new install?  My database is on my master backend.  I am not very knowledgeable in mysql, maybe there is a walkthrough for this procedure?  Also is there any way possible to avoid re-inputting all of my recording list (would restoring a database backup accomplish this)?

Thanks

---

### Post by mickie.kext on 2009-12-29
Hmm... you basically want to backup and later restore your database? This might help:
[http://www.devshed.com/c/a/MySQL/Backing-up-and-restoring-your-MySQL-Database/](http://www.devshed.com/c/a/MySQL/Backing-up-and-restoring-your-MySQL-Database/)

Study the tut before actually doing it, and I suggest that you make some dummy database for trying out, so you see how it works and and see if that is what you want before actually doing it on you important data.

---

### Post by Flecko on 2009-12-29
Speaking from personal experience of going from 9.04 to 9.10 I must say DON'T DO IT!!

My setup was working fine in 9.04(standalone backend/frontend with HDHomeRun getting OTA channels) and when I "upgraded" to 9.10 everything broke. The display drivers didn't get installed properly, so I attempted to do a fresh install of 9.10. Again, things that used to work didn't. Scanning/adding channels sucks in 9.10. Confusing, and just doesn't work out of the box. Not to mention the Mythfrontend appears to have memory leaks and suffers random crashes.

I'm back on 9.04 until 10.04 comes out. 9.10 as far as Myth goes just sucks, plain and simple.

Best of luck though.
-Flecko

---

### Post by OffAxis on 2009-12-29
There's a more specific how to on the mythtv site here:
[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

I think default keymapping changed in 9.10 as well. But I wouldn't know, because my USB transceiver stopped working as soon as I hit the upgrade button...

---

### Post by mjezell on 2009-12-30
If you are using anything but the basic storage groups in 9.04 they are not compatible with 9.10. Storage groups will not be fully reenabled until mythtv v.23 according to the mythtv [website]("http://www.mythtv.org/wiki/MythVideo").  This really hosed up my myth system.

---

