---
title: "mt-daapd Misc SQL Error: unable to open database file"
date: 2009-05-03
forum: Multimedia Software
---

### Post by map7 on 2009-05-03
I keep getting mt-daapd errors when I start mt-daapd, like this:

```
marvin@marvin:~$ sudo mt-daapd -f
Firefly Version svn-1696: Starting with debuglevel 2
Error loading plugin /usr/lib/mt-daapd/plugins/ssc-script.so: plugin declined to load
Plugin loaded: daap/svn-1696
Plugin loaded: ssc-ffmpeg/svn-1696
Plugin loaded: rsp/svn-1696
Starting rendezvous daemon
*** WARNING *** The program 'mt-daapd' uses the HOWL compatibility layer of Avahi.
*** WARNING *** Please fix your application to use the native API of Avahi!
*** WARNING *** For more information see <http://0pointer.de/avahi-compat?s=howl&e=mt-daapd>
Starting signal handler
db_sqlite3_open: Misc SQL Error: unable to open database file (/usr/var/cache/mt-daapd/songs3.db)
Error opening db: Misc SQL Error: unable to open database file
Rendezvous socket closed (daap server crashed?)  Aborting.
Aborting

```

I've tried reinstalling mt-daapd but I keep getting the same error.  This file doesn't exist, is there a way to recreate this database file?

---

