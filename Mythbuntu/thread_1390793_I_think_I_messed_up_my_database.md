---
title: "I think I messed up my database"
date: 2010-01-26
forum: Mythbuntu
---

### Post by IceCap on 2010-01-26
I upgraded my system from 8.04 to 9.10 and made two types of backups of my database.

  First I followed the directions [here]("http://www.mythpvr.com/mythtv/tips/migrate-recordings.html") (probably not a good idea).  Then I also used the mythconverg_backup script and created a .gz file.

  Then I installed my new system, setup the directories, copied the actual media files over and then tried re-installing the database using the .sql file based on the site in the link above.  That seemed to work but came with an error (which now I have forgotten).  I started the frontend and checked the recordings and they all seemed to be there.  Fine, I moved on and started recording more shows.
  Now I realize that the database is corrupt because Mythtv can't find some of the files (they are there but it looks like the filename might be missing in the database).

  So, how can I fix this without loosing the information of the recordings that I just made after the move?  Can I apply the mythconverg_restore on the database as it is, and will it detect duplicates?  Or do I need to start from scratch, use the mythconverg_restore and manually (is that even doable?) insert the info about the recent recordings?

 Thanks in advance

  IceCap

---

### Post by klc5555 on 2010-01-26
If what you have are some recordings from tv, for which the recorded files are in place but the database does not know about them, the tool you'd normally use would be the script myth.rebuilddatabase.pl

The wiki page is at [http://www.mythtv.org/wiki/Myth.rebuilddatabase.pl](http://www.mythtv.org/wiki/Myth.rebuilddatabase.pl)

If the script cannot find the title/subtitle (and you don't know it) for the file being added to the database, this information may be edited later from the mythtv frontend. The script will supply mythtv's 4-digit code for the channel rather than a neat channel number. You probably should not change this as the script will rename the file in accordance with the channel information you provide --the recording will still play fine but will become indigestible to other utilities like mythtranscode.

---

