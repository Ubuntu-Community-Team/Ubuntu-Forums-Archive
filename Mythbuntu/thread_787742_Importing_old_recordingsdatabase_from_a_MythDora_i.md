---
title: "Importing old recordings/database from a MythDora install...."
date: 2008-05-09
forum: Mythbuntu
---

### Post by jakev383 on 2008-05-09
I finally moved to a new backend due to issues with the old one (tuners kept disappearing and then would not allow me to re-add then).
Anyway, the new backend is running Mythbuntu 7.10 (it's what my front ends are currently running and I didn't want to update the whole network to 8.04 yet).
I have all my old recordings from my old backend moved over to the new. I also did a backup of the needed tables from the old backend (record, recorded, oldrecorded, recordedprogram, recordedrating, recordedmarkup, and recordseek) and moved them into the Mythbuntu machine.  I tried to import the backed up database into my new machine, but I get the following error:
```

root@mainmyth:~# mysql -f -u mythtv -pmythtv mythconverg < restore.sql 
ERROR 1054 (42S22) at line 1: Unknown column 'storagegroup' in 'field list'
ERROR 1054 (42S22) at line 2: Unknown column 'storagegroup' in 'field list'
ERROR 1054 (42S22) at line 4: Unknown column 'audioprop' in 'field list'

```
Which I'm assuming is an extra field on the MythDora machine that the Mythbuntu machine does not have.
I then rsync'ed over my old recordings onto the new machine into /var/lib/mythtv/recordings.
Problem is, my old recordings do not show in the recorded programs view. My NEW recordings do.  At least the DB import told it what shows I've already recorded so I don't have to go through that again.
I tried to use myth.rebuilddatabase.pl, and got a perl error. I can fix that, but I was thinking this wouldn't help me anyway. I tried to do a query like this page suggests:
[http://mythtv.org/wiki/index.php/Myth.rebuilddatabase.pl](http://mythtv.org/wiki/index.php/Myth.rebuilddatabase.pl)
But my filenames are all things like 1063_20080426020000.mpg, not show names.
Is there a somewhat easy way to get my shows into the new machine that anyone may know of?
Thanks.

* edit - I said my new backend was running MythDora 7.10 which was incorrect; I was tired! It's running Mythbuntu 7.10.

---

