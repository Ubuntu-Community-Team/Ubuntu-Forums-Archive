---
title: "ubuntu 10.04 ubable to upgrade mythconverg  DB from 9.10"
date: 2010-03-27
forum: Mythbuntu
---

### Post by odror on 2010-03-27
I have just installed mythbuntu 10.04 beta

I copied the data base file from 9.10 ubuntu system using mysql-admin

and then I resored this data base into the 10.04 system. This methord worked from me in passed upgrades. This time it failed.

mythbackend generates the following error
> 2010-03-26 23:09:20.507 Connected to database 'mythconverg' at host: localhost
2010-03-26 23:09:20.507 Closing DB connection named 'DBManager0'
2010-03-26 23:09:20.507 Connected to database 'mythconverg' at host: localhost
2010-03-26 23:09:20.551 Protocol version mismatch (frontend=56,backend=50)

QCoreApplication::postEvent: Unexpected null receiver
2010-03-26 23:09:20.551 Master backend is incompatible with this backend.
Cannot become a slave

How can I force mythbackend to upgrade the database to version 56

when I type mythfrontend I get the following error
> 2010-03-26 23:14:49.450 New DB connection, total: 2
2010-03-26 23:14:49.451 Connected to database 'mythconverg' at host: localhost
2010-03-26 23:14:49.452 Current MythTV Schema Version (DBSchemaVer): 1244
2010-03-26 23:14:50.453 Current MythTV Schema Version (DBSchemaVer): 1244
2010-03-26 23:14:51.454 Current MythTV Schema Version (DBSchemaVer): 1244
2010-03-26 23:14:52.455 Current MythTV Schema Version (DBSchemaVer): 1244
2010-03-26 23:14:53.456 Current MythTV Schema Version (DBSchemaVer): 1244
2010-03-26 23:14:53.456 Timed out waiting.
2010-03-26 23:14:53.456 Not allowed to upgrade the database. Skipping backup.


Does anyone knows how can I force the DB upgrade

Thanks

---

### Post by ian dobson on 2010-03-27
Hi,

Try starting mythtv-setup on the box (when myhbackend is not running), that should do it.

Regards
Ian Dobson

---

### Post by *drew on 2013-01-21
Hi,

I had a similar problem after upgrading Mythbuntu 9.10 to 10.04, so I thought I'd post my solution in case somebody else finds it helpful.

Every time I started the front end, it would want to upgrade the **video** database schema.
However it would warn me that other clients were using the database, so I didn't upgrade.

All the forum posts I found relating to this issue suggested stopping mythbackend and then running **mythtv-setup** to upgrade the database schema.

mythtv-setup is the backend configuration utility, and didn't provide any options to update the video database schema.
This may be different for the **mythtv** database schema, but I haven't encountered this problem.

The solution that worked for me was to stop mythbackend, and then run **mythfrontend** which detected the database schema issue and gave me the option to upgrade.
In this instance, (without the backend running) I was able to proceed with the upgrade, and the problem was resolved.

Of course, mythfrontend will then complain about not being able to connect to the (back end) database, so you need to stop mythfrontend, restart mythbackend, and then restart mythfrontend.

---

