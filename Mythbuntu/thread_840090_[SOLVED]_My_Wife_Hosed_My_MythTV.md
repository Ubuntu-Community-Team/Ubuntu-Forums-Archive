---
title: "[SOLVED] My Wife Hosed My MythTV"
date: 2008-06-25
forum: Mythbuntu
---

### Post by yonkiman on 2008-06-25
It was the first time I'd left her alone with it.  Here's the story as best I can piece together:  Apparently she was trying to close MythTV to get to the desktop to watch a movie with VLC (I don't have Myth configured to play movie files yet - just the Tivo functionality) and didn't think to try the escape key.  She managed to get to the Quit menu and decided "Hibernate" was the right option.  I've never tried it before.  Then at some point she hit the power or maybe reset button to turn it back on and the machine booted up into the state it's currently in:

- hard disk chattering nonstop.  I thought it might be rebuilding from an error or something so I let ig go all last night, but I woke up in the morning and it was still chattering away.  Is there any way to tell what process is accessing the disk?  I booted from another disk and did the maximum fsck on it I could - down to looking for bad blocks.  The drive is clean.  SMART info says the drive is OK, too.  But I reboot and it's back to the chatter.

- When I reboot I get the ubuntu desktop, but the automatic launch of Mythfrontend (or maybe it's the backend) doesn't go so well.  I get a config screen, badly overscanned (which means it can't find the config settings it was using that shrank the window), open to the "Select Your Preferred Language" page.  I select English and get a "No UPnP backends found" error.  I press OK (only choice) and go to the database settings, which all seem to be OK localhost/mythconverg/mythtv/<correct password>.  I "Next" two more times to the end and get a "Cannot login to database?" error, so I press OK (again, only selection), and it takes me back to the database settings, etc.

- When I launch MythTVBackend Setup and tell it it's OK to close any running mythTV backend processes...the drive chatter immediately stops.  So I guess that solves that mystery (anyone know how to make mythtv backend start/stop thrashing the drive?).  I get the same "select language screen" and subsequent loop documented above.  In fact I get the exact same sequence whether I start the front or the backend...

So MythTVBackend seems to be thrashing my harddisk continuously due to some unknown thing my sweet but completely linux-illiterate wife did.  I'd like to fix this if possible, but I may settle for salvaging the recorded programs...though I guess the MySQL database is probably hosed.  That's what I think I'll do next - copy the MySQL database from my backup over onto this one.  That will work, right?  

Any ideas welcome.  Thanks for listening.  :-)

---

### Post by yonkiman on 2008-06-25
I think the nonstop chatter was Mythbackend writing to the log file.  It was 350MB when I looked at it!  I deleted it and restarted mythbackend, and here's what I saw (over and over and over...):

```
2008-06-25 00:27:57.152 Using runtime prefix = /usr, libdir = /usr/lib
2008-06-25 00:27:57.196 Empty LocalHostName.
2008-06-25 00:27:57.197 Using localhost value of mythtv
2008-06-25 00:27:57.208 New DB connection, total: 1
2008-06-25 00:27:57.219 Unable to connect to database!
2008-06-25 00:27:57.220 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-06-25 00:27:57.273 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
................................................................................
2008-06-25 00:27:59.685 UPnPautoconf() - No UPnP backends found
2008-06-25 00:27:59.690 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [yes]  
[console is not interactive, using default 'yes']
Database host name: [localhost]  
[console is not interactive, using default 'localhost']
Should I test connectivity to this host using the ping command? [yes]  
[console is not interactive, using default 'yes']
Database non-default port: [0]  
[console is not interactive, using default '0']
Database name: [mythconverg]  
[console is not interactive, using default 'mythconverg']
Database user name: [mythtv]  
[console is not interactive, using default 'mythtv']
Database password: [WsxqsxM3]  
[console is not interactive, using default 'WsxqsxM3']
Unique identifier for this machine (if empty, the local host name will be used):  
[console is not interactive, using default '']
Would you like to use Wake-On-LAN to retry database connections? [no]  
[console is not interactive, using default 'no']
2008-06-25 00:27:59.702 Unable to connect to database!
2008-06-25 00:27:59.703 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-06-25 00:27:59.755 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2008-06-25 00:27:59.805 Cannot login to database?
2008-06-25 00:27:59.806 Cannot login to database?

Cannot login to database?

Would you like to configure the database connection now? [yes]  
```

...looping back to near the top.

---

### Post by DutchLoki on 2008-06-25
Try checking/repairing your mysql database, that might do the trick. See the MythTV wiki for more info about this.

p.s. yah, wives and computers are some mix. Some time ago my computer fan failed because of an extreme ammount of hair in the system :S seriously... how was that possible?!?

---

### Post by netslacker on 2008-06-25
Sounds like your database (MySQL) is in a "crashed" state (all tables marked as "crashed"). If the db/tables are marked as crashed then they are not accessible by myth until they are repaired.

You can try this command:
mysqlcheck -r -u mythtv -pmythtv mythconverg

which I got from here:
[http://www.mythtv.org/wiki/index.php/Category:MySQL](http://www.mythtv.org/wiki/index.php/Category:MySQL)

---

### Post by yonkiman on 2008-06-25
> **netslacker said:**
> mysqlcheck -r -u mythtv -pmythtv mythconverg

Thanks for the suggestion!  However I get a
[INDENT]mysqlcheck: Got error: 2002: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) when trying to connect[/INDENT]
error.

So I googled around that error message for a while, and finally came to the conclusion that completely uninstalling MySQL (which also uninstalls the MythTV front and back ends) might work.  So I tried it.  And lo and behold, it worked!!!  Amazingly, all my old recordings were still there. 

Thanks for the tip!

-Fred

---

### Post by yonkiman on 2008-06-25
> **DutchLoki said:**
> p.s. yah, wives and computers are some mix. Some time ago my computer fan failed because of an extreme ammount of hair in the system :S seriously... how was that possible?!?

LOL!  Thanks for the tip and the sympathy!

---

### Post by mrand on 2008-06-26
> **yonkiman said:**
> Thanks for the suggestion!  However I get a
[INDENT]mysqlcheck: Got error: 2002: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) when trying to connect[/INDENT]
error.

So I googled around that error message for a while, and finally came to the conclusion that completely uninstalling MySQL (which also uninstalls the MythTV front and back ends) might work.  So I tried it.  And lo and behold, it worked!!!  Amazingly, all my old recordings were still there. 

Thanks for the tip!

-Fred
Not that I'm having this problem, I'm curious to the exact steps/commands you took to fix your problem (uninstall and reinstall commands)?

You said all your old recordings were still there - are you saying they were still in the myth listings/database, or just that the recording files remained there?  If they were still in myths listings, it sounds like uninstall + reinstall of MySQL does not delete anything in the database.

   [INDENT]Marc[/INDENT]

---

### Post by DutchLoki on 2008-06-26
> **mrand said:**
> Not that I'm having this problem, I'm curious to the exact steps/commands you took to fix your problem (uninstall and reinstall commands)?

You said all your old recordings were still there - are you saying they were still in the myth listings/database, or just that the recording files remained there?  If they were still in myths listings, it sounds like uninstall + reinstall of MySQL does not delete anything in the database.

   [INDENT]Marc[/INDENT]

simply put MySQL consist of an engine and the database file(s). When uninstalling/installing MySQL you don't need to delete your database file(s). This way you don't loose any information.

Of course after reinstalling MySQL you need to tell the engine where it can find the database files for MythTV.

---

### Post by dsegel on 2008-06-26
> **yonkiman said:**
> Thanks for the suggestion!  However I get a
[INDENT]mysqlcheck: Got error: 2002: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) when trying to connect[/INDENT]
error.


-Fred

This sounds like MySQL isn't running. You could try 'sudo /etc/init.d/mysql start' and then watch the log files to see what/if there is an error. After it's started try running mythfrontend again from a terminal window.

(Yes, I realize the OP's problem has been fixed but thought I would post this for others who find their way to this thread)

---

### Post by yonkiman on 2008-06-26
> **mrand said:**
> Not that I'm having this problem, I'm curious to the exact steps/commands you took to fix your problem (uninstall and reinstall commands)?

I used the Synaptic GUI to uninstall MySQL.  At some point it asked if I wanted to delete my databases, and I said no.  Since I actually completely uninstalled MySQL and MythTV, I was a little surprised (though a posting I read somewhere indicated all would be OK) and delighted that it all came up instantly...

---

### Post by mrand on 2008-06-30
> **yonkiman said:**
> I used the Synaptic GUI to uninstall MySQL.  At some point it asked if I wanted to delete my databases, and I said no.  Since I actually completely uninstalled MySQL and MythTV, I was a little surprised (though a posting I read somewhere indicated all would be OK) and delighted that it all came up instantly...

Wow.  You uninstalled myth (and mysql) using synaptic, reinstalled, and everything you already had in your database survived?  I'm impressed!  Thanks for the update.

   [INDENT]Marc[/INDENT]

---

### Post by yonkiman on 2008-07-01
> **mrand said:**
> Wow.  You uninstalled myth (and mysql) using synaptic, reinstalled, and everything you already had in your database survived?  I'm impressed!

Me too!  Looking back, I probably could have told it not to uninstall all the Myth stuff (it got automatically selected for uninstall when I asked to uninstall MySQL), but half of me wanted to start over again from scratch anyway, so I rolled the dice.  It *is* good to know that your database and settings will survive...

---

