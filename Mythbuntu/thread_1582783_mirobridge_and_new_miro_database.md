---
title: "mirobridge and new miro database"
date: 2010-09-27
forum: Mythbuntu
---

### Post by davidstoll on 2010-09-27
Does anyone know if there is a new or beta version of mirobridge.py to try out that would be compatible with the new miro database that is out in the beta and nightly builds...and ultimately coming out in the next release?

```

2010-09-27 00:18:50,921 - mirobridge - INFO - Starting Miro Frontend and Backend
2010-09-27 00:18:50,950 INFO     Starting up Miro
2010-09-27 00:18:50,950 INFO     Version:    3.0.1
2010-09-27 00:18:50,997 INFO     OS:         Linux 2.6.32-25-generic i686
2010-09-27 00:18:50,998 INFO     Revision:   ssh://wguaraldi@pcf1.pculture.org/var/git/miro - 247af86e
2010-09-27 00:18:50,998 INFO     Builder:    buildd@rothera
2010-09-27 00:18:50,999 INFO     Build Time: 1271793980.4
2010-09-27 00:18:50,999 INFO     Starting event loop thread
2010-09-27 00:18:51,001 INFO     Restoring database...
2010-09-27 00:18:51,001 INFO     Sqlite3 version:   3.6.22
2010-09-27 00:18:51,001 INFO     Pysqlite version:  2.4.1
2010-09-27 00:18:51,002 INFO     opening database /home/user/.miro/sqlitedb
Startup failure.
2010-09-27 00:18:51,056 - mirobridge - CRITICAL - Starting Miro Frontend and Backend failed: (Database too new)
(You have a database that was saved with a newer version of Miro. You must download the latest version of Miro and run that.)
2010-09-27 00:18:51,056 CRITICAL Starting Miro Frontend and Backend failed: (Database too new)
(You have a database that was saved with a newer version of Miro. You must download the latest version of Miro and run that.)
2010-09-27 00:18:51,057 INFO     Shutting down Downloader...
2010-09-27 00:18:51,057 INFO     Shutting down event loop
2010-09-27 00:18:51,058 INFO     Closing Database...
2010-09-27 00:18:51,058 INFO     closing database
2010-09-27 00:18:51,058 INFO     Vacuuming the db before shutting down.

Shutting down...
```

---

### Post by RDV on 2010-10-05
Mirobridge will require changes to work with the Miro 3.5 release. This is the same thing that has happened in the past between 2.5 to 3.0.

The Miro devs change some of the interfaces that MiroBridge uses. It takes some hacking to figure out what they changed and then adapt MiroBridge. 

I have just started to look into what is required based in the Miro 3.5 RC2. Most definitely a MiroBridge update will NOT be released until Miro's official release of 3.5. It is can be too much of a support hassle if Miro makes last minute changes.

The last time Miro made a release that broke MiroBridge it was corrected in a day or two. I do not anticipate this time to be any different at least as far as my code changes to MiroBridge is concerned.

Please note that there is an extra wrinkle as MythTV is also in the final stages of releasing MythTV 0.24 so I am not sure what the MythTV devs will allow. 

It may be that they delay any MiroBridge code updates until after MythTV 0.24 is officially released.

Doug

---

### Post by davidstoll on 2010-10-06
Would the info in...
tv/lib/databaseupgrade.py 
help?  It lists all the database upgrades.

Or is it really a command line switch of some sort?

I hear what you are saying about update timing, but I'm just trying to help find info that might help to reduce any "hackery".  By the way, this is a new release, so I don't think it will be "fixed".  Changes have been made and although they may change again, that's a guarantee...into eternity.

---

### Post by davidstoll on 2010-10-21
The new miro 3.5 final release is out and the database has been upgraded.  So, mirobridge is now incompatible.

Can I help by testing an updated script?

Thanks!

---

### Post by davidstoll on 2010-10-23
ppa's updated

[http://getmiro.com/download/for-ubuntu/](http://getmiro.com/download/for-ubuntu/)

---

