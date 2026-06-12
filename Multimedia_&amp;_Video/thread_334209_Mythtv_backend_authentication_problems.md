---
title: "Mythtv backend authentication problems"
date: 2007-01-08
forum: Multimedia &amp; Video
---

### Post by mthaddon on 2007-01-08
Hi Folks,

I'm trying to get MythTV working on my laptop - no TV card or anything, just for managing DVDs using the MythDVD and MythVideo packages.

I have gone through the setup and as far as I can see everything looks good, except that I get the following on startup of the backend:

Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

However, in the log file, I see no authentication errors:

2007-01-08 19:52:20.391 Using runtime prefix = /usr
2007-01-08 19:52:20.482 New DB connection, total: 1
2007-01-08 19:52:20.499 Connected to database 'mythconverg' at host: localhost
2007-01-08 19:52:20.505 Current Schema Version: 1160
Starting up as the master server.
2007-01-08 19:52:20.535 New DB connection, total: 2
2007-01-08 19:52:20.536 Connected to database 'mythconverg' at host: localhost
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2007-01-08 19:52:20.551 Main::Starting HttpServer
2007-01-08 19:52:20.561 New DB connection, total: 3
2007-01-08 19:52:20.563 Connected to database 'mythconverg' at host: localhost
2007-01-08 19:52:20.567 Main::Registering HttpStatus Extension
2007-01-08 19:52:20.586 mythbackend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2007-01-08 19:52:20.587 Enabled verbose msgs:  important general
2007-01-08 19:52:20.588 AutoExpire: Found 0 recorders w/max rate of 0 MiB/min
2007-01-08 19:52:20.592 AutoExpire: Required Free Space: 1.0 GB w/freq: 10 min

Can anyone explain what's going on and how to troubleshoot exactly what connection errors there are?

I have verified that I can connect manually on the command line using the connection parameters in /etc/mythtv/mysql.txt.

Thanks, Tom

---

### Post by majoridiot on 2007-01-08
according to the log you posted, you are connecting to the DB...

```
2007-01-08 19:52:20.482 New DB connection, total: 1
2007-01-08 19:52:20.499 Connected to database 'mythconverg' at host: localhost
...
2007-01-08 19:52:20.535 New DB connection, total: 2
2007-01-08 19:52:20.536 Connected to database 'mythconverg' at host: localhost
...
2007-01-08 19:52:20.561 New DB connection, total: 3
2007-01-08 19:52:20.563 Connected to database 'mythconverg' at host: localhost
```

is the authentication error from an ssh session, etc?  it might be a spurious error... i get them 
from time to time but things still work fine.

i would assume you have a good mythconverg db connection and move forward to see what
happens.

---

### Post by mthaddon on 2007-01-08
The error I'm getting is from a command line when I do

sudo /etc/init.d/mythtv restart

I had thought, ah well, carry on as the logfile looks okay, but when I open up the frontend and try to import a DVD I get a message saying it can't connect to the transcoding backend.

Thanks, Tom

---

### Post by SyvanX on 2007-01-08
It looks like your backend just does not like that you don't have a tuner installed.  Is your mythbackend running?  Usually the frontend doesn't like it when the backend isn't running and will pop-up an error when it starts.
If you're unsure try:  
```
ps -A | grep mythbackend
```

it should return something like:
>  4088 ?        00:05:43 mythbackend

If your backend is working, the MythTranscode Daemon must not be working correctly.  After you've gotten the backend running, you can start the mythtranscode daemon by running
```
mtd -d
```

Then try to rip your DVD.

---

### Post by mthaddon on 2007-01-08
Think I'm making some progress - thanks for the help.

How do I make it so that this daemon is started automatically - is that a config option somehere? 

And when I try to actually rip a DVD I press 0 to start the ripping and it just exits out saying there's no outstanding jobs. I'm sure I'll be able to find some docs that explain something about it, so hopefully I'm almost there...

Cheers, Tom

---

### Post by SyvanX on 2007-01-09
Make sure you can rip DVDs once mtd is running, then you can follow these directions, although they are a little outdated.  It should do the job though.

Was your backend running by the way?

From: [http://www.section6.net/wiki/index.php/Installing_MythTV_on_Ubuntu_Linux](http://www.section6.net/wiki/index.php/Installing_MythTV_on_Ubuntu_Linux)

> 
We should also make sure that the "Myth Transcode Daemon" starts up everytime the system boots.. after all we did go through all the trouble of compiling from source to get this option to work.

We must edit the /etc/init.d/rc.local file and add the following line to the bottom of the file:

```
/usr/local/mythtv/bin/mtd --daemon
```

This will start the service everytime the system boots. 

---

### Post by mthaddon on 2007-01-09
The backend was running, thanks. 

Will post back if I have any more issues.

Thanks, Tom

---

