---
title: "Database upgrade failure"
date: 2016-11-11
forum: Mythbuntu
---

### Post by pssturges on 2016-11-11
Hi,

The other day I tried to upgrade from 14.04 to 16.04. As far as I could tell, the process went OK until the system hung during reboot. After exhausting all options I did a hard reset and was left with a system that wouldn't boot. Rather than trying again and because my system had been a bit flaky anyway, I decided to do a fresh install of 16.04.1. That went well and I restored my backedup DB to the new system. Problem is when I run backend set up, it tries to update the database as expected but it fails. The error is as follows:

```
Nov 10 21:35:30 htpcserver mythtv-setup.real: mythtv-setup[13157]: C CoreContext dbcheck.cpp:2846 (doUpgradeTVDatabaseSchema) Upgrading to MythTV schema version 1332
Nov 10 21:35:30 htpcserver mythtv-setup.real: mythtv-setup[13157]: E CoreContext mythdb.cpp:183 (DBError) DB Error (CreateNewInputGroup 2):#012Query was:#012INSERT INTO inputgroup        (cardinputid, inputgroupid, inputgroupname) VALUES (?,    ?,     ?    ) #012Bindings were:#012:GROUPID=2, :GROUPNAME="htpcserver|/dev/dvb/adapter1/frontend0", :INPUTID=0#012Driver error was [2/1062]:#012QMYSQL3: Unable to execute statement#012Database error was:#012Duplicate entry '0' for key 'PRIMARY'
Nov 10 21:35:30 htpcserver mythtv-setup.real: mythtv-setup[13157]: E CoreContext dbcheck.cpp:519 (UpgradeTVDatabaseSchema) Database schema upgrade failed.
Nov 10 21:35:30 htpcserver mythtv-setup.real: mythtv-setup[13157]: E CoreContext main.cpp:539 (main) Couldn't upgrade database to new schema.

```

Broadly I can see what the problem is, but I have no idea what I should do to fix it and not cause further problems. TBH I'm not that attached to my old database, I just need it to have all my old recordings. Maybe I can just restore the recordings table?

The entire setup/upgrade log can be found here: [http://paste.ubuntu.com/23455444/]("http://paste.ubuntu.com/23455444/")

Thanks in advance for any help
Phil

---

### Post by Caysho on 2016-11-12
The schema version is associated with the hostname.
Look at 
[https://code.mythtv.org/doxygen/mythtv_2libs_2libmythtv_2dbcheck_8cpp_source.html](https://code.mythtv.org/doxygen/mythtv_2libs_2libmythtv_2dbcheck_8cpp_source.html) 
and you will see it is trying to insert a value that is already present.

I recall having a similar problem when I experimented with a remote front end and, later an upgrade failed due to the DBSchemaVer entry in the settings table did not match due to a hostname mismatch.

You will need to look at the database - install MySQL Workbench and check the settings table for the DBSchemaVer

However, the log indicates that the database backup failed, so I think this is a symptom of a larger corruption.

Due to the issues with the MySQL upgrade on Ubuntu 14.04 to 16.04, I did reinstall with a backup, and then ran into these:
[Access denied for user 'mythtv'@'localhost']("https://forum.mythtv.org/viewtopic.php?f=36&t=67&start=19")  
[config.xml problem]("http://www.gossamer-threads.com/lists/mythtv/users/602081")
But it seems you have not hit these, given it can read the database.

---

