---
title: "Restore recordings after mysql restore"
date: 2015-08-12
forum: Mythbuntu
---

### Post by BarnOwl on 2015-08-12
I'm using mythbuntu 14.04

My mythconverg database was corrupted.  So I restored from my 2:00AM backup.  That did get all my recordings back prior to the backup.  However, there were some recordings done after the backup and before the restore.  Those files are on disk but, not in the database.  Is there a way to get them in?

Thanks

---

### Post by aelfric55 on 2015-08-13
For mythtv 0.25 and earlier there were more-or-less supported scripts to add content of this sort to the recordings database by creating new database entries for them. But since 0.26 the only supported method has been to add this sort of content to the Videos library instead. This is the method you should use. 

However, on one occasion I had a single recording file I really wanted to re-add to recordings, since I don't use Mythvideo. So I manually-recorded a five-minute junk recording on that same channel to create a database entry, copied my real recording on top of the 5-minute junk recording file, renaming the real file to the name of the junk file, for which there was now a database entry. I then manually rebuilt the seektable and commflagged this patched-in recording with mythcommflag, and edited most of the patched recording's metadata (Series name, episode, plot) from the on screen Edit Metadata menu in Watch recordings on Mythfrontend. It wasn't a perfect solution since the start and end times were listed incorrectly (consistent with the manual junk recording) and the procedure was obviously too cumbersome to do for more than one or two recordings. But it worked for me satisfactorily and I didn't have to muck around in the database.

---

### Post by BarnOwl on 2015-08-14
Thanks for the reply.

I was wondering about those scripts.  I've seen them mentioned but, they don't appear to be on my system.  I see what you're getting at.  I'm actually an Oracle database administrator.  Maybe it's time to get familiar with MySQL.  I'm not sure it's worth it in this case.  OTOH you never know when something like this will happen again.  Besides it might be interesting.

---

