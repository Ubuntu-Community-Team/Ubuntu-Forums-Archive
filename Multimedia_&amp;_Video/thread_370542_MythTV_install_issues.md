---
title: "MythTV install issues"
date: 2007-02-25
forum: Multimedia &amp; Video
---

### Post by djrobthaman on 2007-02-25
Hi,

One more question.  I'm trying to install mythTV using the instructions at [http://www.mythtv.org/wiki/index.php/Ubuntu_Edgy_Installation]("http://www.mythtv.org/wiki/index.php/Ubuntu_Edgy_Installation"),

I've done everything so far, but when I type "sudo apt-get build-dep mythtv" I get a message saying:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/packages.freecontrib.org_plf_dists_dapper_free_source_Sources - open (2 No such file or directory)

What can I do to fix this?

Thanks again,
Douglas

---

### Post by Titus A Duxass on 2007-02-26
Try using the guides in the community documentation, you will find it easier.

[https://help.ubuntu.com/community/MythTV?highlight=%28Mythtv%29](https://help.ubuntu.com/community/MythTV?highlight=%28Mythtv%29)

---

### Post by superm1 on 2007-02-26
I've been very tempted to go put a header on the top of those "from source" guides on the mythtv.org wiki linking to the ubuntu community pages, but I think that the author of the from source pages would take offense to that.  Would just save so many people so much trouble :)

---

### Post by SyvanX on 2007-02-26
It looks like djrob's problem might be with a 3rd party repository.  I can't even resolve packages.freecontrib.org, and EasyUbuntu says they're using medibuntu repos now.

---

### Post by djrobthaman on 2007-02-26
Thanks for the reply Titus and so far it has been easier, but I don't think my mysql is working correctly.

If I type in "sudo /etc/init.d/mysql restart", I get:

* Stopping MySQL database server mysqld                                 [ ok ] 
 * Starting MySQL database server mysqld                                 [fail] 

(fail never sounds good).

And when I start up mythtv-setup I get the following:


QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-02-26 22:20:16.510 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-02-26 22:20:16.563 Unable to connect to database!
2007-02-26 22:20:16.563 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

 a few gazillion times.

What do you think I should do?

Douglas

---

### Post by superm1 on 2007-02-26
> **djrobthaman said:**
> Thanks for the reply Titus and so far it has been easier, but I don't think my mysql is working correctly.

If I type in "sudo /etc/init.d/mysql restart", I get:

* Stopping MySQL database server mysqld                                 [ ok ] 
 * Starting MySQL database server mysqld                                 [fail] 

(fail never sounds good).

And when I start up mythtv-setup I get the following:


QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-02-26 22:20:16.510 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-02-26 22:20:16.563 Unable to connect to database!
2007-02-26 22:20:16.563 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

 a few gazillion times.

What do you think I should do?

Douglas
Check out /var/log/mysql* (there are a bunch of mysql related files there).
If nothing in those logs, then i would say easiest solution is to just purge all mysql stuff and reinstall it.  Not sure what happened that mysql-server got messed up though.

---

### Post by djrobthaman on 2007-02-26
So, I've narrowed it down to the guilty culprit.  I fixed mysql with a reinstall, but mythtv-database is not installing correctly.  The following error comes up constantly.

E: mythtv-database: subprocess post-installation script returned error exit status 1

I get the popup that asks me for the password to mysql and after that the error.

Any advice?

---

### Post by superm1 on 2007-02-26
> **djrobthaman said:**
> So, I've narrowed it down to the guilty culprit.  I fixed mysql with a reinstall, but mythtv-database is not installing correctly.  The following error comes up constantly.

E: mythtv-database: subprocess post-installation script returned error exit status 1

I get the popup that asks me for the password to mysql and after that the error.

Any advice?
Purge mythtv-database as well and reinstall.  See if that resolves it.  The default password for mysql is no password.  The default user is root.

---

### Post by djrobthaman on 2007-02-26
Hi there,

You posted before I could go again.  It's mysql-server.  The install said it was ok, but whenever I try to start it there is a failure notification.  So that must be it.  How would I get this working?  Is there a log file somewhere that says why it's failing?

Thanks,
Douglas

---

### Post by djrobthaman on 2007-02-26
Does this mean anything to anybody?

I'm still not quite sure what's happening

```

~$ sudo /usr/sbin/mysqld --user=root

070226 23:37:30 [Warning] Ignoring user change to 'root' because the user was set to 'mysql' earlier on the command line

070226 23:37:30  InnoDB: Database was not shut down normally!
InnoDB: Starting crash recovery.
InnoDB: Reading tablespace information from the .ibd files...
InnoDB: Restoring possible half-written data pages from the doublewrite
InnoDB: buffer...
070226 23:37:30  InnoDB: Starting log scan based on checkpoint at
InnoDB: log sequence number 0 36808.
InnoDB: Doing recovery: scanned up to log sequence number 0 43655
mysqld got signal 4;
This could be because you hit a bug. It is also possible that this binary
or one of the libraries it was linked against is corrupt, improperly built,
or misconfigured. This error can also be caused by malfunctioning hardware.
We will try our best to scrape up some info that will hopefully help diagnose
the problem, but since we have already crashed, something is definitely wrong
and this may fail.

key_buffer_size=0
read_buffer_size=131072
max_used_connections=0
max_connections=100
threads_connected=0
It is possible that mysqld could use up to 
key_buffer_size + (read_buffer_size + sort_buffer_size)*max_connections = 217599 K
bytes of memory
Hope that's ok; if not, decrease some variables in the equation.

```

Thanks,
Douglas

---

### Post by Titus A Duxass on 2007-02-27
I have no idea how you got that failure nor do I have a simple fix for you.

I recommend reinstalling, during MythTV installations most problems occur because of misreading the instructions.

It took me about 4 installation runs before I crack it.

---

