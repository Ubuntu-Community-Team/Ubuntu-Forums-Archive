---
title: "Migrate Recordings from one machine to another"
date: 2009-12-08
forum: Mythbuntu
---

### Post by dualboot on 2009-12-08
Hi All,
I've given up trying to upgrade my existing 8.10 to 9.10.  It has an ATI graphics card built on the motherboard and won't play with an add on card.

I now have a new machine built from scratch running 9.10, and I have mounted the old box's /var/lib/ via NFS.  I was planning to use the archive recordings to archive on the old box and import on the new.

Having done one recording I now realise this is going to be the labour of Hercules for half a terabyte's worth.  

Is there any cunning way to copy the old 8.10 database and files  en-mass to the new system ?

---

### Post by OffAxis on 2009-12-08
ya.

The easiest thing to try is to copy the recordings over to the new machine (maintain the same relative path; i.e. /var/lib/mythtv/recordings)

and then copy the old db over. In
**/var/lib/mysql** is a folder called **mythconverg**, which contains the tables and data for mythtv.
copy that folder to your new system and and **chown** it to **mysql:mysql**
Next, run **mythtv-setup** or mythbackend.
It should give you a popup and tell you that it needs to upgrade your database.

9.10 (mythtv version .22) uses a slightly different database scheme, so there's no going back once you upgrade (without doing it manually; major PITA).

If you screw anything up there's a sql script in 
**/usr/share/mythtv/sql/** that you can run and generate a new (blank) mythconverg database.

---

### Post by SiHa on 2009-12-08
Personally, after copying the recordings over, as in OffAxis' suggestion,  I would prefer to export the relevant tables from your 8.10 database, and import them into your new 9.10 database. IMHO, much more prefereble to upgrading the old database.

Have a look at post #16 [[COLOR="Blue"]_here_[/COLOR]](http://ubuntuforums.org/showthread.php?t=1292030&page=2) for how I did it.

---

### Post by dualboot on 2009-12-08
Thanks OffAxis, 
I'll set off the copy running overnight.  First though I'll archive the few recordings I have on the new box.  A lot easier this way 'round.

---

### Post by nickrout on 2009-12-08
> **OffAxis said:**
> ya.

The easiest thing to try is to copy the recordings over to the new machine (maintain the same relative path; i.e. /var/lib/mythtv/recordings)

and then copy the old db over. In
**/var/lib/mysql** is a folder called **mythconverg**, which contains the tables and data for mythtv.
copy that folder to your new system and and **chown** it to **mysql:mysql**


NO NO NO NO do not do this! Warning!

There are binary incompatibilities between versions of MySQL. You CANNOT just copy the binary database files. You MUST backup your database using the provided commands and restore the backup to the new machine.

Read this thread very carefully!!

[http://www.gossamer-threads.com/lists/mythtv/users/405443](http://www.gossamer-threads.com/lists/mythtv/users/405443)

---

### Post by tgm4883 on 2009-12-08
While moving the database dir to a new machine may work for some databases, there are other things in the database that are tied to the original machine (and thus need changed). I would recommend using the MythTV database and restore scripts. Take a look at [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

---

