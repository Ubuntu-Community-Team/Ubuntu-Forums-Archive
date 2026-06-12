---
title: "My backend is repeatedly restarting"
date: 2013-01-16
forum: Mythbuntu
---

### Post by dannyboy79 on 2013-01-16
I was trying to access my recordings thru XBMC last night, which was the first time in a long time, and it showed me my recordings but they wouldn't play. 

So I went down to my workstation and ssh'd into the headless mythtv server, it's running 10.04.4 mythbuntu and 0.23.1+fixes I believe. (i am writing this thread from work just get this kicked off) I, restart the machine and then on my current computer try to access mythweb. it says the webserver doesn't exist or something to that effect, so I ssh'd in and checked that apache2 was running and it was. I tried to run mythtv-status within the ssh terminal session and it failed to connect to the 127.0.0.1 local backend. hmmmm? 

Then I checked the syslog and there were a million repeating messages about the backend mythtv service being terminated due to error 251 (or something with that number in it) and then the mythbackend service was started again but then it was terminated again. So it's starting and stopping. I don't know what changed, can anyone possibly suggest a solution to this issue?
Thanks


UPDATE: here is the specific error within syslog
```
Jan 16 21:56:58 dell init: mythtv-backend main process (1523) killed by TERM signal
Jan 16 21:57:22 dell init: mythtv-backend main process (1550) terminated with status 251
Jan 16 21:57:22 dell init: mythtv-backend main process ended, respawning
Jan 16 21:57:51 dell init: mythtv-backend main process (1597) terminated with status 251
Jan 16 21:57:51 dell init: mythtv-backend main process ended, respawning
Jan 16 21:58:12 dell init: mythtv-backend main process (1611) terminated with status 251
Jan 16 21:58:12 dell init: mythtv-backend main process ended, respawning
Jan 16 21:58:26 dell init: mythtv-backend main process (1621) terminated with status 251
Jan 16 21:58:27 dell init: mythtv-backend main process ended, respawning
```

---

### Post by dannyboy79 on 2013-01-16
UPDATE:
here's the ending log file of mythbackend.log
```
2013-01-16 22:39:44.290 Console is non-interactive, can't prompt user...
2013-01-16 22:39:44.290 Upgrading.
2013-01-16 22:39:44.291 Newest MythTV Schema Version : 1254
QString::arg: Argument missing: ERROR: Unable to acquire database upgrade lock, Driver error was [2/130]:
QMYSQL: Unable to execute query
Database error was:
Incorrect file format 'schemalock'

2013-01-16 22:39:44.293 ERROR: Unable to acquire database upgrade lock
2013-01-16 22:39:44.297 Couldn't upgrade database to new schema
2013-01-16 22:39:46.287 mythbackend version: branches/release-0-23-fixes [26863] www.mythtv.org
2013-01-16 22:39:46.288 Using runtime prefix = /usr
2013-01-16 22:39:46.289 Using configuration directory = /home/mythtv/.mythtv
2013-01-16 22:39:46.290 Empty LocalHostName.
2013-01-16 22:39:46.290 Using localhost value of dell
2013-01-16 22:39:46.305 New DB connection, total: 1
2013-01-16 22:39:46.348 Connected to database 'mythconverg' at host: 192.168.0.5
2013-01-16 22:39:46.349 Closing DB connection named 'DBManager0'
2013-01-16 22:39:46.355 Connected to database 'mythconverg' at host: 192.168.0.5
2013-01-16 22:39:46.361 DataDirectProcessor::FixProgramIDs() -- begin
2013-01-16 22:39:46.367 New DB DataDirect connection
2013-01-16 22:39:46.372 Connected to database 'mythconverg' at host: 192.168.0.5
2013-01-16 22:39:46.801 DataDirectProcessor::FixProgramIDs() -- end
2013-01-16 22:39:46.805 No current database version?
2013-01-16 22:39:46.810 MythTV database schema is old. Waiting to see if DB is being upgraded.
2013-01-16 22:39:47.810 New DB connection, total: 2
2013-01-16 22:39:47.816 Connected to database 'mythconverg' at host: 192.168.0.5
QString::arg: Argument missing: ERROR: Unable to acquire database upgrade lock, Driver error was [2/130]:
QMYSQL: Unable to execute query
Database error was:
Incorrect file format 'schemalock'

2013-01-16 22:39:47.820 ERROR: Unable to acquire database upgrade lock
2013-01-16 22:39:47.821 Waiting for Database Upgrade to complete.

```

---

### Post by dannyboy79 on 2013-01-17
UPDATE: ok, after a couple hours within the mythtv-users IRC channel on freenode.not, it's back up and running. i had total mysql table coruption and i am sure even sure why? without sphery in the IRC chat, I wouldn't have solved this along, no way.

now mythweb isn't working but I am starting a new thread for that.

---

### Post by daone on 2013-02-16
You probably want to avoid this, but have found with experience you will spend far more time trying to fix your corrupted mysql tables, then to re-install mythtv.

Would appreciate an update post if you had success fixing your corrupted tables or ended up starting from scratch?

---

### Post by dannyboy79 on 2013-02-17
i had fixed the corrupted table with the help of mythtv-users channel on freenode IRC server. Everything is still working as it should. I will post back if stuff stops working again but all is well for now. Have scheduled plenty of recordings since using mythweb, watched them, and deleted them.

---

