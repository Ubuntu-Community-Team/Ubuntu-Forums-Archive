---
title: "[SOLVED] Gentoo/mythtv 0.20 to MythBuntu 8.04?"
date: 2008-05-30
forum: Mythbuntu
---

### Post by danbodoh on 2008-05-30
What's the best way to move from mythtv 0.20 on Gentoo on old hardware to mythbuntu 8.04 on new hardware, and retain the recorded history and programs and unwatched recordings?

I've thought of two options:

Option 1: get the mythbuntu 8.04 ISO, build it, and then copy recording files and database tables as described in [http://www.mythpvr.com/mythtv/tips/migrate-recordings.html](http://www.mythpvr.com/mythtv/tips/migrate-recordings.html).  Sounds easy, but I assume the database has changed, and the tables from 0.20 won't cleanly map into 0.21.  Since the new database is already at 0.21, the standard database upgrade scripts won't work.

Option 2: find a mythbuntu 7.10 ISO from somewhere (why isn't it posted anymore????), follow the same database import process but this time it will import to 0.20.  Then follow the standard mythbuntu 7.10 upgrade to 8.04.

I'd love to do option 2, but the mythbuntu 7.10 ISO has been removed.

Suggestions?

---

### Post by tgm4883 on 2008-05-30
Since you are moving to new hardware sounds like we can try just importing those tables into the new database.  I'd setup 8.04 on the new hardware then just copy over the recordings and import only the database tables you need.  Don't do a delete/restore option on the new database, we want the new tables to stay there and for them to just acquire the old data.  While doing this keep the old system together and unmodified just in case this doesn't work, that way you haven't lost anything.

So to sum up.  Try importing it to 8.04 and seeing if it works.  If it does great, if not, since we still have the old system around we haven't lost anything (but a little time).

If that doesn't work i'll link you a copy of 7.10

---

### Post by danbodoh on 2008-06-05
SOLUTION:  How to move from old hardware and old mythtv version to new hardware and a new mythtv version.

Contrary to sources, you can't necessarily just import the various '*record*' tables from the old mythtv setup, because the structure changed.  Even the '-c' option suggested in the comments in the reference above does not work.

The only real solution is to get the entire old mythconverg database, import it into the new system, and run mythtv-setup to upgrade the database.

On old system. get the mythconverg database.  Your database user may be different, but 'mythtv' is common.

```
mysqldump -u mythtv -p mythconverg > old-mythconverg.sql
```

Transfer old-mythconverg.sql to the new system.

On the new system, backup the existing database:

```
mysqldump -u mythtv -p mythconverg > new-mythconverg-backup.sql
```

Then delete the existing database on the new system and create a new empty database.

```
mysql -u mythtv -p

mysql> drop database mythconverg;
mysql> create database mythconverg character set UTF-8
mysql> exit

```

Note that you could use 'latin1' character set; I did because my old data is in latin1.  UTF-8 is probably more common.

Now import the old data in the new system:

```
mysql -u mythtv -p <old-mythconverg.sql
```

Now have mythtv upgrade it to a new format by running mythtv-setup.  Also, you'll have to make any modifications for the new hardware now.

```
mythtv-setup
```

Copy the recordings from the old system to the new system.  This could take a while.  I bought a USB->IDE converter, pulled the drive, and mounted it via USB on the new system and then copied the files.

The new system files go into /var/lib/mythtv/recordings.  If your old system has the recordings in a different place, you'll either have to find the database entry that has the prefix, or simply symlink the old path to the new path.  Mine were in /home/video, so I did the following:

```
sudo ln -s /var/lib/mythtv/recordings /home/video
```

Dan Bodoh

---

