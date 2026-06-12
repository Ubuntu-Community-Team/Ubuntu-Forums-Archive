---
title: "Mysql Mythtv - Table crash / Repair"
date: 2007-07-22
forum: Multimedia &amp; Video
---

### Post by edward4130 on 2007-07-22
During the updates ad such that many of us have been experiencing, I have corrupted or crashed a table in the database.  Everything works including getting the full schedule from Zap2it.  Only thing is all of my future recordings were blown out and when i tried to add them back mythtv will only allow me to record single recordings.... No longer record all.  I could not find any documenttion on repairing this and mythtv-setup asks, when i tell it to fix it doesn't so I hope that my problem is not too large.

```

2007-07-22 07:40:02.985 Scheduled 0 items in 0.1 = 0.06 match + 0.02 place
2007-07-22 10:20:53.983 MainServer::HandleAnnounce Monitor
2007-07-22 10:20:53.995 adding: mediacenter as a client (events: 0)
2007-07-22 10:20:54.031 MainServer::HandleAnnounce Monitor
2007-07-22 10:20:54.032 adding: mediacenter as a client (events: 1)
2007-07-22 10:22:25.399 Reschedule requested for id 136.
2007-07-22 10:22:25.415 DB Error (UpdateMatches):
Query was:
DELETE FROM program WHERE manualid = 136 OR  (manualid <> 0 AND 136 = -1)
Driver error was [2/1194]:
QMYSQL3: Unable to execute query
Database error was:
Table 'program' is marked as crashed and should be repaired

```

Thanks in advance, 
Edward4130, Kansas city Kansas

---

### Post by edward4130 on 2007-07-23
Since no luck getting help on this issue yet, We did some more digging with mythtv and mysetopbox.  we found this mysql fix code, I will try to repair it with it and the post is below.

```

http://mysettopbox.tv/phpBB2/viewtopic.php?t=1043

If you experience system crash it is probably a good idea to check the MySQL table to ensure your tables have not become corrupted. To do this:
Code:
cd /var/lib/mysql/mythconverg
/etc/init.d/mythtv-backend stop
/etc/init.d/mysql stop
myisamchk *.MYI

It is probably a good idea to send the output to a text file for investigation..
Code:
myisamchk *.MYI >> mythconverg_check.log

After the check is complete you may see something like this:

Quote:
myisamchk: warning: Table is marked as crashed and last repair failed
myisamchk: warning: Size of indexfile is: 1331200 Should be: 1024
myisamchk: error: Found wrong record at 0
MyISAM-table 'recordedmarkup.MYI' is corrupted
Fix it using switch "-r" or "-o"

You should check the log file to see which tables are broken and need to be fixed.
Code:
more  mythconverg_check.log

You should see comething like this:
Quote:
Checking MyISAM file: capturecard.MYI
Data records: 2 Deleted blocks: 0
- check file-size
- check key delete-chain
- check record delete-chain
- check index reference
- check data record references index: 1
- check record links

---------

If a table is corrupt, you see something like this at the end of the check for that table:
Quote:
MyISAM-table 'videometadata.MYI' is usable but should be fixed

To fix the table:
Code:
myisamchk -r videometadata.MYI

Once you have repaired all the broken tables, you should run the check again and verify that all table are ok. You'll know all table are ok, because you should get a message stating that table X needs to be fixed... Don't forget to restart MySQL followed by the backend.
/etc/init.d/mythtv-backend start
/etc/init.d/mysql start

```

I will post later if it works, thought it would be helpful to have this documented on the forums for later use by all.

---

### Post by edward4130 on 2007-07-23
Ok this is too weird.. I could not get into the directory of mythconverg, not through sudo so i attempted to log into mysql user and as root and in both I was denied.... this just doesn't happen.  I am really wondering what did the apt-get updates do to my system.  YES I DO KNOW MY PASSWORDS!!  

Weird, more later when I have time to work through this.

```
edward@mediacenter:/var/lib/mysql$ su -l root
Password: 
su: Authentication failure
Sorry.
edward@mediacenter:/var/lib/mysql$ 
```

---

### Post by MCMcButtah on 2007-07-25
Wow, you saved my day with these posts man. I'v had my recorded programs missing and have been trying on and off to fix it for two weeks. I followed the steps in your second post and it worked great.

I had the same problem as you getting into the mythconverg directory. It needs root permission and when I tried a sudo cd mythconverg it said 'cd' was an unrecognized command...yeah weird... The way I got around it was to just issue an 'su' to get to the # prompt and from there I could cd mythconverg. Good luck and thanks again!

---

### Post by jordanius on 2007-10-17
Yep, same problem here after the upgrade. Broken links to Recordings etc. 

Following the above steps seemed to have sorted everything out. Cheers!

---

### Post by vanadar on 2008-02-15
I also want to say thanks.  A sudo su allowed me to get in and following those steps I was able to fix my problem.

---

### Post by tobycatlin on 2008-07-07
Brilliant. fixed my issue, you are a legend

---

