---
title: "Minidlna help"
date: 2014-02-02
forum: Multimedia Software
---

### Post by davidjmorin on 2014-02-02
I had this working and then after a reboot it has stopped.  here is my error log. 
 
```

david@david-SVD11225CXB:~$ service minidlna restart
 * Restarting DLNA/UPnP-AV media server minidlna                                start-stop-daemon: warning: failed to kill 3052: Operation not permitted
rm: cannot remove &#8216;/var/run/minidlna/minidlna.pid&#8217;: Permission denied
chown: changing ownership of &#8216;/var/log/minidlna.log&#8217;: Operation not permitted
                                                                         [fail]
david@david-SVD11225CXB:~$ 



```
```

[2014/02/02 14:22:08] minidlna.c:898: warn: Starting MiniDLNA version 1.0.24 [SQLite 3.7.17].
[2014/02/02 14:22:08] minidlna.c:1006: warn: HTTP listening on port 8200
[2014/02/02 14:23:27] minidlna.c:155: warn: received signal 15, good-bye
[2014/02/02 14:23:28] minidlna.c:898: warn: Starting MiniDLNA version 1.0.24 [SQLite 3.7.17].
[2014/02/02 14:23:28] minidlna.c:1006: warn: HTTP listening on port 8200
[2014/02/02 14:24:00] daemonize.c:101: error: Unable to open pidfile for writing /run/minidlna.pid: Permission denied
[2014/02/02 14:24:00] minidlna.c:898: warn: Starting MiniDLNA version 1.0.24 [SQLite 3.7.17].
[2014/02/02 14:24:00] sql.c:41: error: SQL ERROR 8 [attempt to write a readonly database]
pragma default_cache_size = 8192;
[2014/02/02 14:24:00] minidlna.c:132: error: bind(http): Address already in use
[2014/02/02 14:24:00] minidlna.c:1004: fatal: Failed to open socket for HTTP. EXITING

```

Thanks for the help

---

### Post by Bashing-om on 2014-02-03
davidjmorin; Hi !

Too soon to tell a whole lot, But,
this:
> 
‘/var/run/minidlna/minidlna.pid’: Permission denied

says do this:
```

sudo service minidlna restart

``` so that you have the permissions to do this on your system.

Now what results ?

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

