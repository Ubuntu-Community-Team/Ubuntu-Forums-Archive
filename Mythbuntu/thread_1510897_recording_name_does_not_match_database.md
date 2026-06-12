---
title: "recording name does not match database"
date: 2010-06-16
forum: Mythbuntu
---

### Post by zagor on 2010-06-16
Hi all,

I have a mythbuntu 9.04 64bit working installation.
For several reasons I had to reinstall from scratch, sitll 9.04 64bit.
Before doing that, I did run the backup script [mythconverg_backup.pl]("http://svn.mythtv.org/trac/browser/trunk/mythtv/programs/scripts/database/mythconverg_backup.pl?format=txt") as suggested [here]("http://www.mythbuntu.org/upgrading").
After 9.04 reinstallation, I stopped the backend, drop the database, created a new one and finally restored the database with the twin script [mythconverg_restore.pl]("http://svn.mythtv.org/trac/browser/trunk/mythtv/programs/scripts/database/mythconverg_restore.pl?format=txt").

All recordings are there, as well as channels ids and so on.
But the recordings point to the wrong filenames!
It seems somewhere in the process of backup/restore, the database was converted from "numbered filenames" to "pretty filenames".
For instance, a "dr house" manual recording previously pointing to "1000_20100613211000.mpg" now points to a file named "dr house (Manual Record) - 2010-06-13, 9-10 PM - Sun Jun 13 21-10-00 2010.mpg".

Is there any way I can rebuild the correct links between the database and the real files?

I've tried renaming a file to the name the database expects, and it works, but doing that for 100+ recordings drives me crazy!!!

Thanks for your help.

---

