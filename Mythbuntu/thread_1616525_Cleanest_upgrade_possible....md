---
title: "Cleanest upgrade possible..."
date: 2010-11-08
forum: Mythbuntu
---

### Post by tombongo on 2010-11-08
Hello All,

I am planning an upgrade from 9.10 to 10.10.  I want as close to a fresh install as possible while maintaining my current recordings (recorded table) at a minimum.  I would also like to maintain my recording rules (record table) and recording history (oldrecorded table).

I know that this is doable via a partial restore of the database.  A partial restore only restores the oldrecorded, record, recorded, recordedmarkup, recordedprogram, recordedrating, and recordedseek tables.  I know that my recordedmarkup, recordedprogram, recordedrating, and recordedseek tables are all jacked up because I modified the chanid, starttime, and endtime in the recorded table for many recordings before I realized why that was bad.

I was considering doing the follow:
[LIST=1]
[*]Back up the 9.10 database.
[*]Concatenate the recordedmarkup, recordedprogram, recordedrating, and recordedseek tables.
[*]Back up the 9.10 database again.
[*]Drop the 9.10 database.
[*]Create a new 9.10 database.
[*]Do a partial restore of the 9.10 database (from backup with the concatenated tables).
[*]Back up the 9.10 database again.
[*]Fresh install 10.10.
[*]Drop the 10.10 database.
[*]Restore the 9.10 database (from the latest backup).
[*]Let 10.10 upgrade the database.
[*]Rebuild the recordedseek table with mythcommflag --rebuild.
[*]Rebuild the recordedmarkup table one-by-one with MythWeb.
[/LIST]

Questions for you all:
[LIST=1]
[*]Are there any problems with this approach?
[*]Is there a better method or are there any shortcuts I can take?
[*]Is leaving the recordedprogram and recordedrating tables empty going to be a problem?
[/LIST]

Thanks in advance!

---

### Post by yonkiman on 2010-11-10
I have no idea how well your approach will work, but I tried to upgrade from 9.10 to 10.10 just by using the Update Manager, and it did not work for me.  I upgraded to 9.04, then to 9.10 (vs trying to go straight to 9.10), and it didn't go well.  I'm embarrassed to say I can't remember what all was wrong; it was just enough to make me go back to my working 9.10 installation (I'd cloned my disk first) and consider myself lucky.

I'm not saying this would go badly for everyone, just that it didn't go too well for me.  (Ubuntu is not too crazy about my DFI BloodIron motherboard - I couldn't even get the 10.10 installer CD to boot, which is the reason I tried the upgrade approach.)  I think a clean install of 10.10 and migrating your database settings is a much better idea if you can do it.

So I guess I do have a suggestion:  Clone your hard drive (or at least your boot partition) and then give your plan a shot on the cloned disk.  If anything goes wrong, you haven't lost anything.

Good luck!

---

### Post by wilee-nilee on 2010-11-10
Back it up and do a fresh install, all your un-losable stuff should be saved on a external or a safe partition or something.

Asking the forum members to guarantee any thing is okay but always be prepared.;)

Clone it as the last person suggests, but a straight old usb HD is easy work. I bought a 2 terrabyte external from amazon for about 120$ US I think.

---

### Post by tombongo on 2010-11-11
Thanks for the responses.

My media/db backup/misc drive is separate from my OS drive.  Whenever I do an upgrade, I do a clean install, and import and update the previous database.  Updating the OS via the update manager never worked for me either.

The difference this time is that I know that I have tainted my database with all of my ill-guide tweaks.  These tweaks include making a mess of my markup and seek tables indirectly by manually modifying the channel ID and start/stop time of my current recordings.  This time I want to preserve only a partial database with the minimum amount of data needed to retain my current recordings, recordings history, and recording rules.  I believe only restoring the recorded, oldrecorded, and record tables is all I need.

I am basically asking if my steps outlined above will accomplish that goal, and if they are the most efficient.

---

### Post by novellahub on 2010-11-11
Check out these pages for more info:

[http://www.mythtv.org/wiki/Database_Backup_and_Restore#Partial_restore_of_a_backup](http://www.mythtv.org/wiki/Database_Backup_and_Restore#Partial_restore_of_a_backup)

[http://www.mythbuntu.org/Upgrading](http://www.mythbuntu.org/Upgrading)

---

