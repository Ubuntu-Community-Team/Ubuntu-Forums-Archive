---
title: "Need help migrating from FC6 MythTV"
date: 2009-08-15
forum: Mythbuntu
---

### Post by huffcs on 2009-08-15
I have a running FC6 + MythTV 0.20.2 system, but it's long in the tooth and I want to use a newer version of MythTV.

I have installed MythBuntu 9.04 onto a spare hard drive in the same system while I had the old drives disconnected.  I skipped the mythtv-setup step before rebooting the system (on purpose).

After successfully booting into the MythBuntu system I mounted the old system disk partition containing all my recordings.

I'm stuck trying to drop the mythconverg database so I can restore the one from my old system's mysqldump backup.  It won't let me in to drop the mythconverg database without the mysql root password and I can't find any info on what it is set to.  I also tried to redefine the password, but the help page I found on the MythBuntu website doesn't work for me either.

The intent is to bring over all the settings and recording metadata from the old system so I can use all the recordings I still haven't watched ;-).

Am I going about this the wrong way or what?

Need help.

---

### Post by ian dobson on 2009-08-16
Hi,

Why do you want to drop mythconv. Just import the dumped database. I use this script to "backup the database":-
 
#!/bin/bash
mysqldump -uXXX -pYYY --all-databases --opt | bzip2 > /data/backup/backup-sql.bz2

Which I can then restore using 
bzip2 /data/backup/backup-sql.bz2 | mysql -uXXX -pYYY 

The backup command adds a drop table XXX if exists to the SQL so tables that exist are removed before being recreated.

If myth starts and can connect to the new database have a look for the mysql.txt file, that usually contains the information for a user to login and access the mythconv database.

Regards
Ian Dobson

---

### Post by huffcs on 2009-08-16
Ian-

Thanks for the reply, but...

To answer your question, because that's what the documentation said to do ;-)

I still don't have any info on what the mySQL password is for *ANY* mySQL user, so...

I couldn't find anything that tells what the passwords are set to for the root user or if there are any other mySQL users defined and if so, what their password(s) is (are).

Can anyone give me a clue?

TIA,

Craig.

---

### Post by Neon Dusk on 2009-08-16
The mysql root password should be the same as the user password that you entered during the initial set-up.

---

