---
title: "Help with database back up"
date: 2014-02-23
forum: Mythbuntu
---

### Post by benlyboy on 2014-02-23
Hi i have been trying to work out how to go about backing up the database. I read [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore) and was unable to get it to work at all at first. It kept telling me "mythconverg_backup.pl: command not found" after some looking around i found the script at /usr/share/mythtv and was able to run it from there. it seemed like it may have work, in that i placed a file called "mythconverg-1299-20140223175112.sql" in the directory i had set up but now when i try to run a  mythconverg_restore.pl i get the following error...

ERROR: The specified backup file does not exist.
/media/My Passport//media/My

Invalid backup filename, stopped at ./mythconverg_restore.pl line 845.
graham@myth-box2:/usr/share/mythtv$ sudo./mythconverg_restore.pl 
bash: sudo./mythconverg_restore.pl: No such file or directory

i'm out of ideas:(

thanks

---

### Post by philip7 on 2014-02-24
What command are you running when restoring the database? Copy and paste exactly what you used.

In the past when I have restored the database I also entered the directory and filename to make sure I was restoring the exact file that I wanted.

---

### Post by benlyboy on 2014-02-24
Thanks philip7 for your reply. 
I decided to do as you said you did and add the file address and name to the command so it looked like this 

./mythconverg_restore.pl --directory /media/My Passport --filename mythconverg-1299-20140224212900.sql

This was the result.

The argument you supplied for the database information file is invalid.
If you were trying to specify a backup filename, please use the --directory 
and --filename arguments.

ERROR: Invalid database information file, stopped at ./mythconverg_restore.pl line 710.

Any ideas?

---

### Post by newlinux on 2014-02-24
> **benlyboy said:**
> Thanks philip7 for your reply. 
I decided to do as you said you did and add the file address and name to the command so it looked like this 

./mythconverg_restore.pl --directory /media/My Passport --filename mythconverg-1299-20140224212900.sql

This was the result.

The argument you supplied for the database information file is invalid.
If you were trying to specify a backup filename, please use the --directory 
and --filename arguments.

ERROR: Invalid database information file, stopped at ./mythconverg_restore.pl line 710.

Any ideas?
```

./mythconverg_restore.pl --directory [COLOR="#008000"]**"**[/COLOR]/media/My Passport[COLOR="#008000"]**"**[/COLOR] --filename mythconverg-1299-20140224212900.sql

```
Might work better. The space may cause problems.

---

### Post by benlyboy on 2014-02-24
I tried that but no change...

---

### Post by benlyboy on 2014-02-24
ok getting there took another look at the file and realized that i had left off "gz". I feel like an idiot but there it is...lol
 But it is still not working though i think I'm closer now i get this..

ERROR: Unable to do a full restore. The database contains data.

---

### Post by khPWXxF on 2014-02-25
Here's a restore checklist:

Check out the file/link [COLOR=#000000][FONT=monospace] ~/.mythtv/config.xml
[/FONT][/COLOR]If you run backups or restores under a different user then copy the file/link appropriately.
 
To restore, stop backend first:

```
sudo stop mythtv-backend
```

Restore, dropping database to clear existing data.  Example:
```
/usr/share/mythtv/mythconverg_restore.pl --drop_database --create_database\
    --directory /var/lib/mythtv/db_backups  --filename mythconverg-1214-20080626150513.sql.gz
```

It's a good idea to then check consistency with find_orphans.py and optimize_mythdb.pl 

Finally restart backend:```

sudo start mythtv-backend

```
hth
Phil

---

### Post by benlyboy on 2014-02-25
Thanks guys.

Got it work late last night and i did pretty much what khPWXxF said in the post above. I hadn't done the last step but am going to now,

So thanks again to every one that took the time to post i think this one is solved.

---

