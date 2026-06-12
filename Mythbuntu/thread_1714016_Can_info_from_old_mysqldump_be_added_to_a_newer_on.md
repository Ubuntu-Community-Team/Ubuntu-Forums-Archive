---
title: "Can info from old mysqldump be added to a newer one?"
date: 2011-03-24
forum: Mythbuntu
---

### Post by Panhead Bill on 2011-03-24
Old and new Mythtv servers, same schema, recorded content copied from old server to new server at same location.

Is there some way to get the new server to access all the content?

---

### Post by Panhead Bill on 2011-03-25
Update: I've been able to view the mysqldump from the old server; it appears that if I can cut and paste from the old servers' sql dump to the new servers' sql dump, it may work.  The mysql programs I downloaded are slow and a challenge to figure out.  More to come as I try to figure out the method.

---

### Post by wojox on 2011-03-25
What programs are you using? You should be able to dump it and load it all through the terminal pretty simply.

---

### Post by SeijiSensei on 2011-03-25
Recently I was contracted to recover a Debian box that had died.  I had a backup copy of that machine's /var/lib/mysql but expected I'd need to use mysqldump to create a plain-text backup then recreate the database using the mysql command-line client.  Still, I thought, why don't I just try starting mysqld with the old /var/lib/mysql data.  Well, guess what?  It upgraded the binary database structure to the newer version of MySQL automatically.  

So I'd suggest that, after using mysqldump to insure you have a good backup, you first try copying the /var/lib/mysql structure on the old machine over to the new box and start mysqld.  The worst that can happen is that it fails, and you'd need to delete /var/lib/mysql/* and let the server rebuild it upon restart.

---

### Post by Panhead Bill on 2011-03-26
Wojox: Program MySQL Query Browser seems to get me to the data in the files.  I can select a row of data in the older server's table: "recorded", so I hope it will allow me to copy and paste into the newer server's table.

The mysqldump command I used dumps the tables: record, recorded, oldrecorded, recordedprogram, recordedrateing, recordedmarkup, and recordedseek. 

"recordedprogram" appears to be the data I need to get the newer server to "see" the recordings I transfered to it. Note-I have recordings on the newer server I want to keep, so I can't just upload the older servers sqldump since it will replace the newer recordings on the table.

I need to learn the content of the other tables in the dump, and if I need them all to update the newer server, or if just the "recorded" table will do what I need.


SeijiSensei: I will explore the /var/lib/mysql data to see if that might be an alternative way.

---

### Post by bance on 2011-03-26
You might like to look at [COLOR=Red][this]("http://www.gossamer-threads.com/lists/mythtv/users/475839")[/COLOR] thread!

HTH Steve.

---

### Post by Panhead Bill on 2011-03-28
I found a "brute force" method that works.  The mysqldump files can be opened in a text editor like Gedit.  Due to the size and shape of the files, (all table data is on one line), the editor opens the file slowly - on the order of several minutes.  All movements, edits, and saves are likewise slow. I will either list the steps I used to combine two myth servers' content into one on the following thread, or try to put togeather a "How To". 

[http://ubuntuforums.org/showthread.php?t=1709134](http://ubuntuforums.org/showthread.php?t=1709134)

---

