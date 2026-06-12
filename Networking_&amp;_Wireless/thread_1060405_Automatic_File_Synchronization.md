---
title: "Automatic File Synchronization"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by marsdend on 2009-02-04
Hi guys,

I am wanting to synchronize my files on my laptop (running ubuntu) with my Freecom NAS Hard Drive attached to my wireless router,

I am looking for some software to do this automatically maybe even realtime if possible.

I have tried both Unison and Conduit with conduit being my favourite but they do not sync automatically.

Any ideas?

Much Appreciated!

---

### Post by icheyne on 2009-02-05
[http://www.getdropbox.com](http://www.getdropbox.com)

---

### Post by msimon1960 on 2009-12-11
> **icheyne said:**
> [http://www.getdropbox.com](http://www.getdropbox.com)

This is a fee-for-service option with a free 2Gb of web storage.  It's not really a tool for syncing laptops to servers.

Matt.

---

### Post by falconindy on 2009-12-11
You could write a script using [inotifywait]("http://linux.die.net/man/1/inotifywait") to watch the directories you're interested in and pass the file to rsync as its modified to be copied to the NAS.

---

### Post by CharlesA on 2009-12-11
Bah, I was going to suggest running rsync in cron. *hides*

---

### Post by sgosnell on 2009-12-11
Or if you want a gui, grsync.  It's a frontend for rsync, cron will run it for you at whatever schedule you specify.

---

