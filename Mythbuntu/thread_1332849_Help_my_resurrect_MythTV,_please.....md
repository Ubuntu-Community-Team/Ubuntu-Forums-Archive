---
title: "Help my resurrect MythTV, please...."
date: 2009-11-20
forum: Mythbuntu
---

### Post by mbobak on 2009-11-20
So, I had a UPS fail, took down my Myth box and caused some corruption.

So, here's what I did:

box had a boot, root, and swap partition, as well as a huge partition called 'myth-media'.  myth-media appeared to be unscathed.  Also, /var/lib/mysql/* seemed to be ok.  So, I took a tar of /var/lib/mysql, and I gzipped it, and copied it to the /myth-media partition.

Then I copied off my sources.list, as well.

I re-installed Karmic, from scratch, told it to format boot/root/swap, and leave myth-media alone.  Then I copied over my sources.list, did an 'apt-get update && apt-get dist-upgrade', then an 'apt-get mythtv'.

Finally, I copied my tarred up /var/lib/mysql back into place.

And....my database won't start.  I reset my mysql root password, and I can now get mysql to open.

When I try to start mythbackend, I get:

```
2009-11-20 20:15:20.863 New DB connection, total: 1
2009-11-20 20:15:20.866 Unable to connect to database!
2009-11-20 20:15:20.866 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)
```

So, is what I did valid?  Did I miss something?

Thoughts?  Suggestions?

Thanks!

-Mark

---

### Post by mbobak on 2009-11-21
Nevermind....reset the password for mythtv user, made sure it matched what was in /etc/mythtv/mysql.txt, and I'm on my way.

-Mark

---

