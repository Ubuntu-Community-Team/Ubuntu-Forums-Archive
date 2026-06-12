---
title: "Restoring an old and mature database"
date: 2014-09-16
forum: Mythbuntu
---

### Post by Adam_Jacobs on 2014-09-16
I have decided that the time has come to upgrade my Mythbuntu 10.04 system to the latest version. I plan to do this as a clean install (I'll actually be treating my machine to some new hard disks at the same time, so a clean install is pretty much mandatory).

Now, I have a couple of questions about restoring my existing backend database on the new system.

First, I'm no doubt several versions of MythTV behind the latest one (I'm using 0.23), and I gather that the schema changes from one version to the next. Will the latest version be able to cope with my ancient database and convert whatever needs converting to the latest schema, or might that cause problems?

Second, I'm slightly wondering about the wisdom of simply restoring my existing database, given how old it is. I've been using the same machine for over 5 years now. Perhaps there's a load of stuff in my database that's no longer needed and just cluttering stuff up? Is it actually sensible to just keep restoring the same database year after year, or does there come a point where it's sensible to just start again with a fresh one?

Obviously there is some stuff in the database that I need, such as details of all the various programmes I have recorded and have yet to watch. I'm reasonably confident with SQL and wouldn't be scared of inserting data into individual tables in the new system based on what was in the old database. Is there anything to be gained from going down that route?

Thanks
Adam

---

### Post by tgm4883 on 2014-09-16
> **Adam_Jacobs said:**
> I have decided that the time has come to upgrade my Mythbuntu 10.04 system to the latest version. I plan to do this as a clean install (I'll actually be treating my machine to some new hard disks at the same time, so a clean install is pretty much mandatory).

Now, I have a couple of questions about restoring my existing backend database on the new system.

First, I'm no doubt several versions of MythTV behind the latest one (I'm using 0.23), and I gather that the schema changes from one version to the next. Will the latest version be able to cope with my ancient database and convert whatever needs converting to the latest schema, or might that cause problems?

Second, I'm slightly wondering about the wisdom of simply restoring my existing database, given how old it is. I've been using the same machine for over 5 years now. Perhaps there's a load of stuff in my database that's no longer needed and just cluttering stuff up? Is it actually sensible to just keep restoring the same database year after year, or does there come a point where it's sensible to just start again with a fresh one?

Obviously there is some stuff in the database that I need, such as details of all the various programmes I have recorded and have yet to watch. I'm reasonably confident with SQL and wouldn't be scared of inserting data into individual tables in the new system based on what was in the old database. Is there anything to be gained from going down that route?

Thanks
Adam

I believe you need to upgrade to 0.24 first, then you can go straight to 0.27. There isn't any reason to start with a fresh DB.

---

### Post by Adam_Jacobs on 2014-09-19
Thanks for that. Is upgrading from 0.23 to 0.24 a reasonably straightforward thing to do?

---

### Post by tgm4883 on 2014-09-19
> **Adam_Jacobs said:**
> Thanks for that. Is upgrading from 0.23 to 0.24 a reasonably straightforward thing to do?

It would have been, but IDK where you can find 0.24 packages anymore. If you can find the packages, it should be as simple as installing them, running mythtv-setup to upgrade the DB. Start the frontend and use any plugins you normally would (to upgrade any other DB tables that is necessary), then upgrade to 0.27.

Remember to always take a DB backup first.

---

### Post by mattlach on 2014-09-19
Speaking of possibly cluttered / inefficient databases....

Is there any script or anything that allows you to run a database and drive cleanup by scanning data folders and the database and correlating them?   (Autoremoving video files not in the database, and autoremoving database entries for which there are no longer files?

This would seem like a useful tool, especially for someone like me who prefers to completely avoid mucking with SQL or any database at all for that matter.

---

### Post by tgm4883 on 2014-09-19
> **mattlach said:**
> Speaking of possibly cluttered / inefficient databases....

Is there any script or anything that allows you to run a database and drive cleanup by scanning data folders and the database and correlating them?   (Autoremoving video files not in the database, and autoremoving database entries for which there are no longer files?

This would seem like a useful tool, especially for someone like me who prefers to completely avoid mucking with SQL or any database at all for that matter.

For recordings, there shouldn't be any need as you shouldn't be mucking with the recordings folder (mythtv expects that it's the only one managing that folder). As for videos, you should just need to "Scan for changes" and let mythtv handle removing the old stuff that you've removed.

---

### Post by mattlach on 2014-09-19
> **tgm4883 said:**
> For recordings, there shouldn't be any need as you shouldn't be mucking with the recordings folder (mythtv expects that it's the only one managing that folder). As for videos, you should just need to "Scan for changes" and let mythtv handle removing the old stuff that you've removed.

A few scenarios:

1.)  MythTV has many dependencies and is know for thus being a little sensitive when it comes to package upgrades.  User images install partition prior to upgrade "just in case".  Recordings are stored on a separate partition.  User uses mythbuntu with upgraded packages for a day or two, before determining something in the upgrade has resulted in an instability, and downgrades by restoring partition image.   Now recordings exist on storage device for which there is no corresponding entry in the database.

2.) MythTV's database is known to be sensitive to corruption, to the point where the MythTV wiki recommends frequent backups, and the software comes with an automated script to make these backups easier.  The database is found to be corrupt, and is restored from a backup by the user.  Recordings since the last backup exist in file storage, but not in the restored database.

3.) The MythTV guide recommends using standalone drives rather than RAID for recordings to be stored.   Even with RAID file systems are prone to corruption in some circumstances.  Either one physical drive fails, resulting in the loss of all recordings on that drive, or the file system corrupts after an event (lets say a power outage).  User runs fsck to fix any issues.  This results in the loss of some non-recoverable recordings that are removed.   Now database entries exist for which there are no files.

These are all not very uncommon scenarios, and there really ought to be a way to do an automatic scan to fix them.   Something that would be really nice, would be some metadata included with each recording, and a way to scan any data drives to rebuild/repair recording entries in the database.

---

### Post by tgm4883 on 2014-09-19
> **mattlach said:**
> A few scenarios:

1.)  MythTV has many dependencies and is know for thus being a little sensitive when it comes to package upgrades.  User images install partition prior to upgrade "just in case".  Recordings are stored on a separate partition.  User uses mythbuntu with upgraded packages for a day or two, before determining something in the upgrade has resulted in an instability, and downgrades by restoring partition image.   Now recordings exist on storage device for which there is no corresponding entry in the database.

2.) MythTV's database is known to be sensitive to corruption, to the point where the MythTV wiki recommends frequent backups, and the software comes with an automated script to make these backups easier.  The database is found to be corrupt, and is restored from a backup by the user.  Recordings since the last backup exist in file storage, but not in the restored database.

3.) The MythTV guide recommends using standalone drives rather than RAID for recordings to be stored.   Even with RAID file systems are prone to corruption in some circumstances.  Either one physical drive fails, resulting in the loss of all recordings on that drive, or the file system corrupts after an event (lets say a power outage).  User runs fsck to fix any issues.  This results in the loss of some non-recoverable recordings that are removed.   Now database entries exist for which there are no files.

These are all not very uncommon scenarios, and there really ought to be a way to do an automatic scan to fix them.   Something that would be really nice, would be some metadata included with each recording, and a way to scan any data drives to rebuild/repair recording entries in the database.

None of those scenarios hit the spirit of what the initial post questioned, which was whether just having an old database necessitated a script to clear out any cruft from many DB upgrades (which IMO there isn't a need)

Now to answer your new questions/scenarios, all of those are handled by the Find_orphans.py script. See [http://www.mythtv.org/wiki/Find_orphans.py](http://www.mythtv.org/wiki/Find_orphans.py)

---

