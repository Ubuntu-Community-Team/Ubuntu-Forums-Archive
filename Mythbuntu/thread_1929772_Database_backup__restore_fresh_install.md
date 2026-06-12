---
title: "Database backup / restore fresh install"
date: 2012-02-22
forum: Mythbuntu
---

### Post by sbrattonuk on 2012-02-22
_**Background **_
OK, I've really screwed things up with my Mythbuntu install BE&FE on same machine, it was a 10.04 now 11.10 with a 3.2.7 Kernel.

Somewhere along the upgrade process (remote from 2000 miles away) I ended up with Nouveau sickness with a spot of lightdm-unity poisoning, leaving me with no GUI or local terminal, just remote ssh access. (Mythweb part works).  

**_Want to achieve_**
Time to start from scratch and rebuild with a clean install of 11.10.

_**Questions **_
1. How do I backup my database using a remote ssh login to a separate remote server (I've a ftpserver in the house or a windows share).
2. How do I import said database back into a fresh install ?
3. Am I going to see issues with database versions or passwords? if so how to I find my db password before wiping the hdd for the fresh install.
4. Is there any way of saving my current recordings ?  It's all on the same HDD.

Hopefully it's an easy solution but I've not got a clue where to start on this one.

Thanks in advance of any pointers.
Steven

---

### Post by sbrattonuk on 2012-02-22
Ok I'm getting somewhere.

1. I found some db backups at /var/lib/mythtv/db_backups/
I copied these to a mounted directory on a separate machine.
2. I beleive there is an import feature I can use once I have a fresh install (either mythconverg_restore.pl or using the import tool in the MCC GUI).
3. Unknown if I will have a problem importing with version differences.  I found a file mysql.txt which had the db password in plain text.
4. I'm prepared to lose these 

Now time to bite the bullet and do the fresh install.

Thanks for listening.

---

### Post by drdos2006 on 2012-02-22
Use "mysqldump --help | more" for detailed options.

My  usage is "mysqldump -u  root  -p  mydatabase > /media/sda1/mydatabase.sql" to dump my database.

After re-installation of Ubuntu, the command is "mysql -u root -p mydatabase < /media/sda1/mydatabase.sql"

-p is for password.....

regards

---

### Post by nickrout on 2012-02-22
No, wrong answer, the right answer is here:

[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

whats more the backup script is run weekly in mythbuntu by default through /etc/cron.weekly/mythtv-database.

You can run that script at any tme to have an up to the second database backup.

---

