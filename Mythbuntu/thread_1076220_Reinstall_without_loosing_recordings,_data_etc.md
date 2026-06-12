---
title: "Reinstall without loosing recordings, data etc"
date: 2009-02-21
forum: Mythbuntu
---

### Post by laffinet on 2009-02-21
Hi,

my system is behaving badly recently and I'm contemplating a reinstall.

Is there a way I can do this without loosing my recordings, accompanying data (what show the recording is etc.) ?

I know I will have to reconfigure my system (tuner cards, epg, other stuff), but I don't want to loose my recordings and what goes with them.

---

### Post by dsauter on 2009-02-21
Sections 23.5-23.7 on the following link should get you going.

[http://www.mythtv.org/docs/mythtv-HOWTO-23.html#backupdb]("http://www.mythtv.org/docs/mythtv-HOWTO-23.html#backupdb")

I've done it several times, and it has worked well every time.

---

### Post by Freddan101 on 2009-02-21
For the recordings information I've successfully migrated it to a new database using below commands:

Backup

```
mysqldump -u root -p -t mythconverg record recorded oldrecorded recordedprogram recordedrating recordedmarkup recordedseek > recordings.sql
```
Restore

```
mysql -u root -pmythtv mythconverg –p < recordings.sql
```

---

### Post by laffinet on 2009-02-21
Quick question: I'm assuming the recordings have to be in the same folder, with the folder structure exactly the same. Correct ?

---

### Post by dsauter on 2009-02-21
I can't say for sure.  I keep my recordings on their own partition and I've always mounted them to the exact same spot.  I guess that means that your assumption would be the safest one.

If things go wrong or it's important to change the location of the recordings, there are procedures to import existing recordings.  I understand you will lose some data associated with the files, however.  See the following link, if you are still interested in this route.

[http://www.mythtv.org/wiki/Myth.rebuilddatabase.pl]("http://www.mythtv.org/wiki/Myth.rebuilddatabase.pl")

---

### Post by crez79 on 2009-02-22
As long as the filenames themselves aren't changed, myth will look in all the storage locations to try to find it before giving up. You can verify by making a new storage location and moving a recording or two over and check if myth finds it. It should. 

If the database is lost than rebuilding with the rebuild script would be necessary.

---

