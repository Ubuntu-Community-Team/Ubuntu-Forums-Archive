---
title: "Mythtv - backend failing to write to log file"
date: 2009-09-17
forum: Multimedia Software
---

### Post by wooddealer on 2009-09-17
I'm relatively new to Linux, so please bear with me.

I believe recent upgrades to something, I suspect either mythtv-backend or mysql, are causing errors which result in the logging for my backend to stop working at times, and occasionally my backend doesn't start up at all.

Earlier today, I tried a few things here and there to try and figure out what errors I had.  I was not able to get the backend to startup via the commandline, since it wasn't logging this was my only way to see what was wrong, finally I changed the permissions for /var/log/mythtv/mythbackend.log to:

```
-rw-rw-r-- 1 mythtv mythtv 4.0K 2009-09-17 21:34 mythbackend.log
```

After restarting my box, the backend is running, and it appears to be logging.  However when I look more closely at the backend log file, it's clear that the logging stopped.  Here are the last few lines of that file:

**backend.log**
```
2009-09-17 21:16:53.583 Using runtime prefix = /usr
2009-09-17 21:16:53.669 Empty LocalHostName.
2009-09-17 21:16:53.704 Using localhost value of hobie-desktop
2009-09-17 21:16:53.770 New DB connection, total: 1
2009-09-17 21:16:53.862 Connected to database 'mythconverg' at host: localhost
2009-09-17 21:16:53.960 Closing DB connection named 'DBManager0'
2009-09-17 21:16:54.040 Connected to database 'mythconverg' at host: localho
```

Even when I force the backend to do something which should cause it to write to the log file, like record a show, nothing new appears.

I'm running mythbuntu 8.04, any help is greatly appreciated.

---

### Post by wooddealer on 2009-09-18
Turns out my / partition was full.  emptying trash allowed the log file to be written to again.

---

