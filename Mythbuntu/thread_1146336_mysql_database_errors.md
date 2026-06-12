---
title: "mysql database errors"
date: 2009-05-02
forum: Mythbuntu
---

### Post by phroman on 2009-05-02
Hello all, I'm having database errors and would appreciate any help.  This is a fresh install, I installed Mythbuntu, ran software update, configured my Snapstream remote and USB UIRT blaster.  The default change-channel-lirc.pl script did not work for me, so a friend of mine re-wrote/changed it, and it works from the command line, (I'll post it below for anyone to try out) it doesn't do well changing to some 3 digit channels, but I think this is a problem with the key mapping files, not the script.  Changing to a 3 digit channel from within Mythtv Frontend will result in a crash, so I removed it for now.   So, I'll post my mythtvbackend.log file and the result of typing ```
sudo mysql.d
``` that one's loooong...  Sorry.


mythtvbackend.log

```
2009-05-02 09:34:36.553 Using runtime prefix = /usr
2009-05-02 09:34:36.625 Empty LocalHostName.
2009-05-02 09:34:36.657 Using localhost value of mythtvserver
2009-05-02 09:34:36.808 New DB connection, total: 1
2009-05-02 09:34:36.838 Connected to database 'mythconverg' at host: localhost
2009-05-02 09:34:36.873 Closing DB connection named 'DBManager0'
2009-05-02 09:34:36.875 Connected to database 'mythconverg' at host: localhost
2009-05-02 09:34:36.877 New DB connection, total: 2
2009-05-02 09:34:36.882 Connected to database 'mythconverg' at host: localhost
2009-05-02 09:34:36.913 Current Schema Version: 1214
Starting up as the master server.
2009-05-02 09:34:37.105 New DB connection, total: 3
2009-05-02 09:34:37.107 Connected to database 'mythconverg' at host: localhost
2009-05-02 09:34:37.453 Channel(/dev/video0) Warning: You have not set an external channel changing
			script for a composite or s-video input. Channel changing will do nothing.
2009-05-02 09:34:37.503 New DB scheduler connection
2009-05-02 09:34:37.522 Connected to database 'mythconverg' at host: localhost
2009-05-02 09:34:37.612 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-05-02 09:34:37.613 Main::Registering HttpStatus Extension
2009-05-02 09:34:37.614 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-05-02 09:34:37.615 Enabled verbose msgs:  important general
2009-05-02 09:34:37.636 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-02 09:34:40.545 Reschedule requested for id -1.
2009-05-02 09:34:41.063 Scheduled 0 items in 0.5 = 0.51 match + 0.01 place
2009-05-02 09:34:41.393 Seem to be woken up by USER
2009-05-02 09:34:46.977 DB Error (Error clearing channel locks):
Query was:
DELETE FROM eit_cache WHERE status  = 1
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-02 09:34:47.726 DB Error (JobQueue::CleanupOldJobsInQueue: Error deleting old finished jobs.):
Query was:
DELETE FROM jobqueue WHERE (status in (272, 288, 320) AND statustime < '2009-04-30T09:34:47') OR (status in (304) AND statustime < '2009-04-28T09:34:47')
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-02 09:34:48.137 DB Error (HouseKeeper Cleaning TVChain Table):
Query was:
SELECT DISTINCT chainid FROM tvchain WHERE endtime > '2009-05-02T05:34:48' ;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-02 09:34:48.484 DB Error (Housekeeper Creating Temporary Table):
Query was:
CREATE TEMPORARY TABLE IF NOT EXISTS temprecordedcleanup ( chanid int(10) unsigned NOT NULL default '0', starttime datetime NOT NULL default '0000-00-00 00:00:00' );
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-02 09:34:49.159 New DB connection, total: 4
2009-05-02 09:34:47.560 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-02 09:34:49.265 Connected to database 'mythconverg' at host: localhost
2009-05-02 09:34:49.592 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-02 09:35:57.546 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-02 09:36:01.064 MainServer::HandleAnnounce Monitor
2009-05-02 09:36:01.072 adding: mythtvserver as a client (events: 0)
2009-05-02 09:36:01.073 MainServer::HandleAnnounce Monitor
2009-05-02 09:36:01.073 adding: mythtvserver as a client (events: 1)

```


mysql.d

```
jose@mythtvserver:~/Desktop$ sudo mysqld
[sudo] password for jose: 
090502 10:42:29 [Warning] option 'net_buffer_length': unsigned value 8388608 adjusted to 1048576
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
090502 10:42:30  InnoDB: Retrying to lock the first data file
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
090502 10:44:10  InnoDB: Unable to open the first data file
InnoDB: Error in opening ./ibdata1
090502 10:44:10  InnoDB: Operating system error number 11 in a file operation.
InnoDB: Error number 11 means 'Resource temporarily unavailable'.
InnoDB: Some operating system error numbers are described at
InnoDB: http://dev.mysql.com/doc/refman/5.0/en/operating-system-error-codes.html
InnoDB: Could not open or create data files.
InnoDB: If you tried to add new data files, and it failed here,
InnoDB: you should now edit innodb_data_file_path in my.cnf back
InnoDB: to what it was, and remove the new ibdata files InnoDB created
InnoDB: in this failed attempt. InnoDB only wrote those files full of
InnoDB: zeros, but did not yet use them in any way. But be careful: do not
InnoDB: remove old data files which contain your precious data!
090502 10:44:10 [ERROR] Can't start server: Bind on TCP/IP port: Address already in use
090502 10:44:10 [ERROR] Do you already have another mysqld server running on port: 3306 ?
090502 10:44:10 [ERROR] Aborting

090502 10:44:10 [Note] mysqld: Shutdown complete

jose@mythtvserver:~/Desktop$ 

```

As always, thanks very much. :P

---

### Post by Dewey_Oxberger on 2009-05-02
Alright - A third person have mysql trouble.  All of the problems look the same.

Your log file is showing the results after a system restart or cold boot right?

If so then you are getting what I am getting.  From what I can tell mysql seems to stop working correctly during boot.  About 5-7 sec into boot it goes bonkers, then seems to fix itself.  I found I had to change the boot order: in /etc/rc2.d I moved S31Mythbackend to S99zMythbackend and mysql was mostly up at that point.  I do still get an occational query error during boot but not as often.

If loads of people are having this problem on 9.04 maybe we can get a handle on it.

---

### Post by phroman on 2009-05-02
Hey Dewey, as I'm super new to Linux, I don't understand a lot but I can follow directions...  My /etc/rc2.d directory seems to be full of sim-linked files, I have an S24mythtvbackend file in there, but not sure what to do.  Is there a file to edit or should I be changing a sim-link?  Do you think this could be causing my channel change problems as well?  Thanks for the reply, and any further detailed instructions you could provide are appreciated.  :)

---

### Post by ian dobson on 2009-05-03
Hi,

Just go to the directory and rename S24mythtvbackend to S99mythtvbackend.

sudo cd /etc/rc2.d
sudo mv S24mythtvbackend S99mythtvbackend

mv is the "move"/rename command under linux.
When linux boots it look in the rcX.d directory for all files starting with S and starts them in the order defined by the number. So changing S24 to S99 means that mythtvbackend will startup much later in the boot process after mysql is up and running.

Regards
Ian Dobson

---

### Post by phroman on 2009-05-03
Awsome!  re-boot, no errors at all, thanks Dewey.  :P  Thanks for the explanation of what was happening too, I appreciate it.

---

### Post by Hugolp on 2009-05-10
I am having a lot of mysql errors with mythbackend as well (since I upgraded to a clean Jaunty). Sometimes the system stops working and I have to use mythweb database repair option. But the errors keep coming back. I will post a log later when I can.

---

### Post by Hugolp on 2009-05-22
> **Hugolp said:**
> I am having a lot of mysql errors with mythbackend as well (since I upgraded to a clean Jaunty). Sometimes the system stops working and I have to use mythweb database repair option. But the errors keep coming back. I will post a log later when I can.

Updated to the new proposed mysql packages and it got solved.

---

