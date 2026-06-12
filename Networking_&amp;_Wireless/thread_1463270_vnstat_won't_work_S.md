---
title: "vnstat won't work :S"
date: 2010-04-26
forum: Networking &amp; Wireless
---

### Post by aCsbD6N5xj on 2010-04-26
Hi.

I installed vnstat a few days ago to replace Net Meter so i could stray away from Wine.

So here is what i'm getting:
 
```
$ vnstat
 eth0: Not enough data available yet.

$ vnstat -u
Error: Unable create database backup "/var/lib/vnstat/.eth0".

$ vnstat -i
Error: Interface for -i missing.
```So i tried installing both from U.S.C and sudo apt-get and i'm having the same issues. I have a wireless home connection.

Any help appreciated. I really need to monitor my upl/dwl history :S

Thx

---

### Post by aCsbD6N5xj on 2010-04-27
Bump

---

### Post by staticsage on 2010-05-31
When you get the "Error: Unable create database backup "/var/lib/vnstat/.eth0".", it is because you do not have write access to the directory.

Run the command as sudo for it the -u option to work.

---

### Post by Ophidion on 2010-12-12
You need either to configure the file /etc/vnstat.conf to put all files to your home directory or run these as a root:
$ sudo vnstat -u -i ppp0
or:
$ sudo vnstat -u -i eth0
make sure then that you run the daemon:
$ sudo vnstatd -d

then check it after 5 minutes (or as you configured for it) with:
$ vnstat

I didn't really checked if the daemon will run with startup, but if not you need to add it.
hope it works for you.

---

