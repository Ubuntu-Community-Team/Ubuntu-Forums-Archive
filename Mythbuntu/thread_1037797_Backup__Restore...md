---
title: "Backup / Restore.."
date: 2009-01-12
forum: Mythbuntu
---

### Post by davecurtains on 2009-01-12
Hi all,

I looked on Wiki's, google etc but could not find this info..

I'm migrating to a new Backend, and was testing my a restore to a new system.  It seemed to work, and I then dropped the mythconverg database.

Whats now the best way to create a new empty mythconverg database so I'm ready for my _real_ backup/restore in a few days time.  I can't seem to find this info anywhere :-(

Thanks all!
Steve

---

### Post by klc5555 on 2009-01-12
> **davecurtains said:**
> Hi all,

I looked on Wiki's, google etc but could not find this info..

I'm migrating to a new Backend, and was testing my a restore to a new system.  It seemed to work, and I then dropped the mythconverg database.

Whats now the best way to create a new empty mythconverg database so I'm ready for my _real_ backup/restore in a few days time.  I can't seem to find this info anywhere :-(

Thanks all!
Steve

From the user manual at the Mythtv wiki; page on "Periodic Maintenance", "Back up Your Database" (a page which has all sorts of useful stuff): 
[http://mythtv.org/wiki/index.php/User_Manual:Periodic_Maintenance](http://mythtv.org/wiki/index.php/User_Manual:Periodic_Maintenance)
                    ....

To restore: (assuming that you've dropped the database)

$ mysql -u root
  mysql>create database mythconverg;
  mysql>exit
$ mysql -u mythtv -pmythtv mythconverg < mythtv_backup.sql

                   ......

Note when you get to the database restore stage, that there is no space between -p and your actual MySQL password (which won't be "mythtv") That alone could save an hour of frustration!

Cheers! :)

---

### Post by davecurtains on 2009-01-15
What I was actually looking to do was bring mythtv back to a completely empty, freshly installed database.  So I guess I'm looking for the mythconverg.sql file.

I'll have a rummage and see what I can find in the mythbuntu file system on the CD as it must be on there somewhere.  Then I'm going to do a partial restore of recorded programs only.

---

### Post by klc5555 on 2009-01-15
> **davecurtains said:**
> What I was actually looking to do was bring mythtv back to a completely empty, freshly installed database.  So I guess I'm looking for the mythconverg.sql file.

I'll have a rummage and see what I can find in the mythbuntu file system on the CD as it must be on there somewhere.  Then I'm going to do a partial restore of recorded programs only.

Eh? Guess I don't understand.

The two commands  

$ mysql -u root
mysql> create database mythconverg;

give you a new, completely empty mythconverg database. You can just exit the MySQL prompt from there.

---

