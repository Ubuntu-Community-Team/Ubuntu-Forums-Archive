---
title: "[SOLVED] Permission settings for ' /var/lib/mythtv/recordings' ?"
date: 2007-08-07
forum: Multimedia &amp; Video
---

### Post by armin00as on 2007-08-07
Hi,
I'm still having issues getting MythTV to work...

When checking the **usr/bin/mythbackend** output in Terminal, I came across this error:

> 2007-08-06 22:56:39.116 Enabled verbose msgs:  important general
/var/lib/mythtv/recordings/nfslockfile.lock: Permission denied
Unable to open lockfile!
Be sure that '/var/lib/mythtv/recordings' exists and that both 
the directory and that file are writeable by this user.
By default, only mythtv showed as the owner of the **/recordings** folder, so I *chown -R 'ed* myself (and mythtv as 'group') to it.
This had the result that the files inside (..they were not playing anyways...) did change from two 'fake mpg' to one 'fake mpg' (note: they turn out to be empty .txt documents when clicking). 

After changing permissions, the *folder permissions* tab now shows:

> Owner: armin
Folder Access: Create and delete files

Group: mythtv
Folder Access:  Create and delete filesThe lockfile, by the way, is an empty, "plain text document" ...

Is this correct??? :confused:

-- Thanks!

---

### Post by armin00as on 2007-08-07
Seems like changing the permissions was right/correct (?).
Before, backend reported a problem with the permission...

> 
2007-08-06 22:56:39.116 Enabled verbose msgs:  important general
/var/lib/mythtv/recordings/nfslockfile.lock: [B]Permission denied
Unable to open lockfile!
Be sure that '/var/lib/mythtv/recordings' exists and that both 
the directory and that file are writeable by this user.[/B]Now, it shows this one:

```
armin@E6400-UBUNTU:~$ /usr/bin/mythbackend
2007-08-07 00:00:36.422 Using runtime prefix = /usr
2007-08-07 00:00:36.427 New DB connection, total: 1
2007-08-07 00:00:36.430 Connected to database 'mythconverg' at host: localhost
2007-08-07 00:00:36.431 Current Schema Version: 1160
Running as a slave backend.
2007-08-07 00:00:36.433 New DB connection, total: 2
2007-08-07 00:00:36.434 Connected to database 'mythconverg' at host: localhost
2007-08-07 00:00:36.434 EITHelper: localtime offset -5:00:00 
2007-08-07 00:00:36.436 New DB connection, total: 3
2007-08-07 00:00:36.436 Connected to database 'mythconverg' at host: localhost
2007-08-07 00:00:36.628 Main::Starting HttpServer
QServerSocket: failed to bind or listen to the socket
2007-08-07 00:00:36.629 Main::HttpServer Create Error
2007-08-07 00:00:36.629 Main::Registering HttpStatus Extension
2007-08-07 00:00:36.629 mythbackend version: 0.20.20060828-3 www.mythtv.org
2007-08-07 00:00:36.630 Enabled verbose msgs:  important general
2007-08-07 00:00:36.630 AutoExpire: Found 1 recorders w/max rate of 72 MiB/min
2007-08-07 00:00:36.630 AutoExpire: Required Free Space: 2.1 GB w/freq: 10 min
QServerSocket: failed to bind or listen to the socket
2007-08-07 00:00:36.630 Failed to bind port 6543. Exiting.
```[B]

"Failed to bind port 6543"[/B]. -- Does that say *anything* to *anyone*..?
:confused:

---

### Post by armin00as on 2007-08-07
-- THAT'S IT, I'M THROWING IN THE TOWEL...!! :mad:

---

### Post by isaksen on 2007-09-19
I had the same problem as #1
all I had to do was to 

sudo /etc/init.d/mythtv-backend restart

---

### Post by iczman on 2007-09-29
[EDIT]
Sorry, I posted to the wrong thread.

---

