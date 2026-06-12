---
title: "restore from mcc"
date: 2012-07-08
forum: Mythbuntu
---

### Post by jim09 on 2012-07-08
I have tryed to restore from the mcc but it doesn't seem to work.  The dialog box said it was successful but it wasn't.  Nothing in the bare-client log.

2012-07-06 08:20:24,007 INFO <backup-task> Backup job finished
-------------------------------------------------------------------

---

### Post by tgm4883 on 2012-07-08
> **jim09 said:**
> I have tryed to restore from the mcc but it doesn't seem to work.  The dialog box said it was successful but it wasn't.  Nothing in the bare-client log.

2012-07-06 08:20:24,007 INFO <backup-task> Backup job finished
-------------------------------------------------------------------

As in the other thread. Is there anything printed to the terminal when you run the restore?

---

### Post by tgm4883 on 2012-07-08
> **tgm4883 said:**
> As in the other thread. Is there anything printed to the terminal when you run the restore?

Actually, are you choosing to restore the database as well when you do the restore?

---

### Post by tgm4883 on 2012-07-08
I think I fixed the issue in version 2.4, which I'm pushing to the PPA now. Can you verify it's resolved in 2.4?

---

### Post by jim09 on 2012-07-08
I launched it a terminal window got 4 done messages.  It looked like it complete successfully but no luck.  No messages in any of the logs that I can see pointing to anything.

mythbuntu-bare-status...contents
40
Restoring database (this could take a few minutes)
------------------------------------------------------

in /tmp there's a compressed database - looks like good data inside

/etc/mythtv

mysql.txt and config.xml look like their good (proper date for restore)

Observation - it doesn't look like its taking very much time if its calling mythconverg_restore.pl

---

### Post by tgm4883 on 2012-07-08
> **jim09 said:**
> I launched it a terminal window got 4 done messages.  It looked like it complete successfully but no luck.  No messages in any of the logs that I can see pointing to anything.

mythbuntu-bare-status...contents
40
Restoring database (this could take a few minutes)
------------------------------------------------------

in /tmp there's a compressed database - looks like good data inside

/etc/mythtv

mysql.txt and config.xml look like their good (proper date for restore)

Observation - it doesn't look like its taking very much time if its calling mythconverg_restore.pl

So the restore is actually going to be done by the mythbuntu control centre backend (mcc-backend), so you'll need to run that portion from the command line instead. You'll need to 

```
sudo killall mcc-backend
/usr/share/mythbuntu/mcc-backend
```

Then open up mythbuntu-control-centre and do a restore and it will print the output to the terminal window running mcc-backend. Also check that you are on mythbuntu-bare-client 2.4

---

### Post by jim09 on 2012-07-08
output...
jim@jim-mythbuntu:~$ sudo /usr/share/mythbuntu/mcc-backend
Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.7/threading.py", line 551, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.7/threading.py", line 504, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/usr/share/mythbuntu-bare/bareclient/mythrestore.py", line 68, in restore_job
    pipe = subprocess.Popen([restorescript, '--drop_database', '--create_database', '--directory', TMPDIR], stdout=subprocess.PIPE).communicate()
NameError: global name 'subprocess' is not defined

---

### Post by jim09 on 2012-07-08
sorry forgot....

mythbuntu-bare-client/precise uptodate 2.4
mythbuntu-common/precise uptodate 0.67
mythbuntu-control-centre/precise uptodate 0.63-0ubuntu2

---

### Post by tgm4883 on 2012-07-08
> **jim09 said:**
> sorry forgot....

mythbuntu-bare-client/precise uptodate 2.4
mythbuntu-common/precise uptodate 0.67
mythbuntu-control-centre/precise uptodate 0.63-0ubuntu2

Not sure how I missed that import. Uploaded 2.5, that should be fixed now.

---

### Post by jim09 on 2012-07-09
Thanks, seems to be fixed now.  :D

---

