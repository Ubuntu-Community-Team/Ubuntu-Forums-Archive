---
title: "Recovering from HDD failure /w old backup"
date: 2012-05-12
forum: Mythbuntu
---

### Post by Digicrat on 2012-05-12
**Lesson Learned:** Backup everything, *backup often* and routinely *verify* those backups are complete.  

I've been thinking I should update my backups "this weekend" for a while now but kept putting it off ... and now a few days ago the primary HDD on my mythTV box died without warning.  My recordings are safe on a seperate drive (~800+GB of backlogged shows at last count), however the latest mythtv DB backup I can find is just over a year old.  It was supposed to be set to automatically export DB backups to the same drive the recordings are on, but apparently that configuration broke a few upgrades ago and I never noticed.  


I'm planning on buying a new primary HDD tommorow (possibly a SSD).   I'll do a fresh install of Mythbuntu 12.04 and then follow the procedures to restore my outdated 0.24 DB backup.  

The question is A) How will mythTV behave for recordings that are listed in the restored DB but long deleted?  B) How will mythTV treat recordings on the disk but NOT in the DB?  And is there any feasible way to attempt to rebuild the DB, or at least manually name the untracked recordings as I identify them?  Based on timestamp and old tv listings I should be able to at least identify a fair number of the shows by series.  


Any other suggestions on how best to rebuild the system?

thanks,
- David

---

### Post by nickrout on 2012-05-12
Shame about the dB backup. Bummer.

For recordings in the database that have been deleted run find_orphans.py - script that you can download from the wiki.

For recordings you still have and which were made since the backup was made, the experts say that the best thing to do is put them into videos as opposed to recordings. 

To make sure metadata lines up become familiar with the myth naming scheme. Basically you want something like:

/videos/TV/The Beverly Hillbillies/Season 1/The Beverly Hillbillies S01E01.mpg

/videos/Movies/The Life of Brian.mpg

But there is a wiki article on naming and pay attention to changes for 0.25. If your language setting is GB as opposed to US the parser will ook for Series instead of Season (or something like that, it's Saturday night, I have a glass of wine and my in home jazz singer has started singing)

---

### Post by Digicrat on 2012-05-13
The freshly installed system is apparently making backups automatically without my explicitly setting anything up ... yet my old install where I had set it up wasn't ... Anyway:

Thanks for the info.  

I checked out the find_orphans.py script which at least removed all of the orphaned entries in the database.   

Do you have a link to that wiki article on video naming conventions in mythtv?  (Google is not revealing it to me).  



I haven't begun trying to identify my orphaned recordings yet...or moving them into place. I may try extending the find_orphans.py script, or make my own Perl version to aide my recovery process.  I may be able to take a good guess at batch naming some recordings based on time/day/length. To bad there's no metadata in the files or their names...a station number or tuner id would have been quite helpful.  

I've also just discovered that somehow I now have 3 entries in the database for each actual tuner, even though the mythtv-setup only shows the new ones I added since restoring the database.  Which explains why after scanning channels there are a lot more stations than I expected.  Oh, the fun of restoring a system...

---

### Post by nickrout on 2012-05-14
> **Digicrat said:**
> The freshly installed system is apparently making backups automatically without my explicitly setting anything up ... yet my old install where I had set it up wasn't ... Anyway:

Thanks for the info.  

I checked out the find_orphans.py script which at least removed all of the orphaned entries in the database.   

Do you have a link to that wiki article on video naming conventions in mythtv?  (Google is not revealing it to me).[http://www.mythtv.org/wiki/Video_Library](http://www.mythtv.org/wiki/Video_Library) and [http://www.mythtv.org/wiki/MythVideo_File_Parsing](http://www.mythtv.org/wiki/MythVideo_File_Parsing)>   

I haven't begun trying to identify my orphaned recordings yet...or moving them into place. I may try extending the find_orphans.py script, or make my own Perl version to aide my recovery process.  I may be able to take a good guess at batch naming some recordings based on time/day/length. To bad there's no metadata in the files or their names...a station number or tuner id would have been quite helpful.the start of the filename is related to the channel (the first four digits) - the rest is the date and time>  I've also just discovered that somehow I now have 3 entries in the database for each actual tuner, even though the mythtv-setup only shows the new ones I added since restoring the database.  Which explains why after scanning channels there are a lot more stations than I expected.  Oh, the fun of restoring a system... Are you sure each tuner isn't presenting as 3 virtual tuners?

---

