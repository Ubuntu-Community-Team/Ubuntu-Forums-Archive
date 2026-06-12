---
title: "Two mythbuntu problems ..."
date: 2010-05-30
forum: Mythbuntu
---

### Post by badger_fruit on 2010-05-30
I have been having problems with the Windows 7 "MythTV Player" for some time so decided to whack on the new Ubuntu 10.4 LTS.  All went well, I am using it wirelessly with no problem and very happy.  I then tried to set up Myth TV and now, things are going really wrong!

Problem 1. Myth front-end on 10.4 laptop tells me that "The server uses Network protocol 50 but this client only understands version 56".  Figuring it may be because my back-end server was running Mythbuntu 8.04 I decided to upgrade this to 9.10 and then it should work.

More fool me. I have just spent the afternoon upgrading and the client PC still is showing me the same error and now (Problem 2) the MYTHBACKEND  won't even load as it says the schema is wrong ...

```

badgerfruit@bgrsvr-v:~$ mythbackend 
2010-05-30 15:33:54.842 mythbackend version: branches/release-0-22-fixes [23766] www.mythtv.org
2010-05-30 15:33:54.843 Using runtime prefix = /usr
2010-05-30 15:33:54.843 Using configuration directory = /home/badgerfruit/.mythtv
2010-05-30 15:33:54.844 Empty LocalHostName.
2010-05-30 15:33:54.844 Using localhost value of bgrsvr-v
2010-05-30 15:33:54.853 New DB connection, total: 1
2010-05-30 15:33:54.873 Connected to database 'mythconverg' at host: localhost
2010-05-30 15:33:54.873 Closing DB connection named 'DBManager0'
2010-05-30 15:33:54.877 Connected to database 'mythconverg' at host: localhost
2010-05-30 15:33:54.895 Current MythTV Schema Version (DBSchemaVer): 1254
2010-05-30 15:33:54.907 New DB connection, total: 2
2010-05-30 15:33:54.908 Connected to database 'mythconverg' at host: localhost
2010-05-30 15:33:56.258 Backing up database with script: '/usr/share/mythtv/mythconverg_backup.pl'
2010-05-30 15:34:26.549 Database Backup complete.
2010-05-30 15:34:26.696 Backed up database to file: '/home/badgerfruit/recordings/recordings/mythconverg-1254-20100530153356.sql.gz'

Error: MythTV database has newer TV schema (1254) than expected (1244).

Database Host: localhost
Database Name: mythconverg

2010-05-30 15:34:26.717 Couldn't upgrade database to new schema

```
Mythtv-setup gives me:-
"Error: MythTV database has newer TV Schema than expected"

HELP!!!!!
(Please)

---

### Post by ian dobson on 2010-05-30
Hi,

The backend and frontend must run the same version of mythtv (0.22 or 0.23). As your frontend is now running Ubuntu 10.04 which contains MythTV version 0.23, you'll need to upgrade your backend to 0.23.

I'm not sure if version 0.23 is available as a package for ubuntu 9.10, have a look at the mythbuntu web page. Or maybe upgrade your backend to 10.04

Regards
Ian Dobson

---

### Post by badger_fruit on 2010-05-30
Bah, of course, silly me I should have realised that 10.x and 9.x are still different front/back ends.
I am upgrading the server to 10.4 LTS now and see if that helps ....

Strange how the front end on the back-end server wouldn't work but perhaps this will sort it.

---

### Post by klc5555 on 2010-05-30
> **badger_fruit said:**
> Bah, of course, silly me I should have realised that 10.x and 9.x are still different front/back ends.
I am upgrading the server to 10.4 LTS now and see if that helps ....

Strange how the front end on the back-end server wouldn't work but perhaps this will sort it.

Moot now, of course with all the upgrading, but 10.04 runs the older Mythtv 0.21 packages from 9.04 quite well. So a second option would have been to leave your 8.04 Master backend alone, remove the Myth 0.23 packages from your remote frontend, and install the Myth 0.21 packages (plus three dependencies) from 9.04 instead. I have a couple of 10.04 laptops now running 0.21 that I use as remote frontends for my 9.04 master server.

---

### Post by badger_fruit on 2010-05-30
woop. Upgrading backend to 10.x has worked and the clients are now connecting again.
Silly me, major panic caused brain to stop working it seems lol!

---

