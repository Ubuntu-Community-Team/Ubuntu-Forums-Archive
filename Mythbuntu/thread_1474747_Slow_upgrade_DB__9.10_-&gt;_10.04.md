---
title: "Slow upgrade DB  9.10 -&gt; 10.04"
date: 2010-05-06
forum: Mythbuntu
---

### Post by digiital on 2010-05-06
Anyone know or have experience a slow, and I mean SLOW upgrade of the database from .22 to .23? I let it run over night for a good 6 hrs and it still didn't seem to have upgraded the database. I killed the process this morning. Did another reboot and when the frontend loaded up it asked to upgrade the database again which I did and left if running while I'm at work. 

Is it normal to run this long?

---

### Post by digiital on 2010-05-07
Ok I found the problem. 

I ran frontend via a shell to see what was going on  and found this. 


**2010-05-07 06:51:53.280 Hash () generated for file (/var/lib/mythtv/videos/media/nas/old-nas/David Laptop Backup/david/AppData/Roaming/Apple Computer/MobileSync/Backup/504fbaf8239b1a90310da0f75c519f4cc0af1ea0/a84eb29c2debaaa5b7e3c33374878d19f14ac452.mddata)**

At one time I had linked my NAS to the video directory, which its not anymore(not even turned on), but some how its on the database. Now it's going through THOUSANDS of "Hash () generated for file"  how can I  stop this?? Clean up the DB? Which table?

---

### Post by uncle hammy on 2010-05-07
If I understand correctly you had at one time "Videos are stored in" set to you NAS?  ALl video stuff is stored in the videometadata table in the DB, so theoretically, I supposed you could....

1. Make a backup of that table and then a backup of the entire database.
2. Delete all data from that table.
3. Do your upgrade.
4. Put your data back into the (now empty) new videometadata table.  This table has some schema changes, so it would take a little sql work (not much really, I believe all the changes are field additions) to make sure you get the data in the old columns to line up with the new ones.
5. Do some fancy SQL to update file paths to the proper paths.  If you're now using storage groups, it will take a little more thought, but it can be done, becuase I've done it.
6. Jamu should take care of populating most of the missing info in the new fields.

or...

Delete all the data out of videometadata and then rescan your video collection and re-download your metat data after you upgrade.

Just a thought.

---

### Post by uncle hammy on 2010-05-07
I should add, if you're using storage groups, as I recall, the file names would be literally, just the file name with no path.  Then there's a "host" (I think) filed that you put the machine name of the backend with the storage group the file belongs to.

---

