---
title: "how to safely import mythtv 0.24.1 data into 0.25 ?"
date: 2012-04-30
forum: Mythbuntu
---

### Post by declanmullen on 2012-04-30
Hi

I'm building a new mythbuntu 12.04 combined backend/frontend system to replace my existing mythbuntu 10.10 system.

What is the safe way of importing at least the tv recordings and the recording rules from my old mythbuntu 10.10 mythtv (0.24.1+fixes.20110814.515171d-0ubuntu0mythbuntu2) into my new and separate mythbuntu 12.04 mythtv 0.25 ?

I'm worried that using mythbuntu's mythtv backup and restore tools might might corrupt something in 0.25 or result in some loss of 0.25 functionality due to differences/incompatibilities between 0.25 and 0.24.1. Am i being too paranoid ?

I'm happy to manually recreate the rest of the mythtv configuration in the new 0.25 instance (eg channels, recorders, etc), though if there is a safe way of importing all of those from the old 0.24.1 instance, that would be a bonus. Btw, I'll be moving all of my existing tuners from the old system to the new system.

Thanks,
Declan

---

### Post by azmyth on 2012-04-30
I would make a backup of both the 0.25 db and the 0.24 db. I'd move the 0.24 db over to the new system. I'd stop the backend on the new and then I would drop the 0.25 db and restore the 0.24 db. I'd then restart the backend in a terminal window and watch to make sure it upgraded the db from 0.24 to 0.25. Hopefully, you kept the same username and paths as the 0.24 system otherwise you'd probably have to change them using phpmyadmin.

---

### Post by nickrout on 2012-04-30
> **declanmullen said:**
> Hi

I'm building a new mythbuntu 12.04 combined backend/frontend system to replace my existing mythbuntu 10.10 system.

What is the safe way of importing at least the tv recordings and the recording rules from my old mythbuntu 10.10 mythtv (0.24.1+fixes.20110814.515171d-0ubuntu0mythbuntu2) into my new and separate mythbuntu 12.04 mythtv 0.25 ?

I'm worried that using mythbuntu's mythtv backup and restore tools might might corrupt something in 0.25 or result in some loss of 0.25 functionality due to differences/incompatibilities between 0.25 and 0.24.1. Am i being too paranoid ?

I'm happy to manually recreate the rest of the mythtv configuration in the new 0.25 instance (eg channels, recorders, etc), though if there is a safe way of importing all of those from the old 0.24.1 instance, that would be a bonus. Btw, I'll be moving all of my existing tuners from the old system to the new system.

Thanks,
Declan

You are worrying too much. On 0.24 use the backup tool supplied by mythtv. Then restore that database into the 0.25 machine. See the very thorough article in the wiki.

---

### Post by elliott6 on 2012-04-30
Are there really that many issues/concerns?

Don't mean to hijack, but I am in a somewhat similar boat (although, I am still on 10.04/0.23.1).  Everything that I have searched seemed to indicate that the "safest" method was restoring via the "Database Backup and Restore" wiki - [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

My plan was to simply convert the database to 0.25 first - just don't know if I can go straight to 0.25 from 0.23, and if after being backed up, it's as simple as changing the repos in MCC.  Then, I would do the fresh install of 12.04 and do the recover.

Folks are pretty adamant about this as far as I can search, so don't think you need to be overly concerned.

---

### Post by nickrout on 2012-04-30
> **elliott6 said:**
> Are there really that many issues/concerns?

Don't mean to hijack, but I am in a somewhat similar boat (although, I am still on 10.04/0.23.1).  Everything that I have searched seemed to indicate that the "safest" method was restoring via the "Database Backup and Restore" wiki - [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

My plan was to simply convert the database to 0.25 first - just don't know if I can go straight to 0.25 from 0.23, and if after being backed up, it's as simple as changing the repos in MCC.  Then, I would do the fresh install of 12.04 and do the recover.

Folks are pretty adamant about this as far as I can search, so don't think you need to be overly concerned.

yes you can go straight from 0.23 to 0.25 on ubuntu/mythbuntu 10.04. That will convert the database.

alternately you can import your 0.23 database to a fresh 0.25 install - the choice is yours.

---

### Post by declanmullen on 2012-05-01
Many thanks for all your responses.

I've just read thru the "Database Backup and Restore" wiki - [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore).

So is the process ? :
[LIST]
[*]Create backup of old 0.24.1 mythtv via the mythconverg_backup.pl script.
[*]Install new mythbuntu 12.04 on new server with its mythtv 0.25 frontend and backend.
[*]Restore old server's O.24.1 backup on to the new server via the mythconverg_restore.pl script.
[*]Copy recording files from old server to new server
[/LIST]

If so, assuming that the installation of mythtv 0.25 creates an initial database, should I use the --drop_database and  --create_database options with mythconverg_restore.pl (as mentioned in the "Replacing an existing database" section of the above wiki) to restore my old 0.24.1 data onto the new server ?

Thanks,
Declan

---

### Post by nickrout on 2012-05-01
> **declanmullen said:**
> Many thanks for all your responses.

I've just read thru the "Database Backup and Restore" wiki - [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore).

So is the process ? :
[LIST]
[*]Create backup of old 0.24.1 mythtv via the mythconverg_backup.pl script.
[*]Install new mythbuntu 12.04 on new server with its mythtv 0.25 frontend and backend.
[*]Restore old server's O.24.1 backup on to the new server via the mythconverg_restore.pl script.
[*]Copy recording files from old server to new server
[/LIST]

If so, assuming that the installation of mythtv 0.25 creates an initial database, should I use the --drop_database and  --create_database options with mythconverg_restore.pl (as mentioned in the "Replacing an existing database" section of the above wiki) to restore my old 0.24.1 data onto the new server ?

Thanks,
Declan

yes

---

