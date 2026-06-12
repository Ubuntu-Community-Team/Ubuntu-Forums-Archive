---
title: "front end can't connect to backend on same machine"
date: 2016-09-04
forum: Mythbuntu
---

### Post by scharkalvin on 2016-09-04
I'm running a single machine with BOTH a backend and a frontend (the usual default setup out of the box for a first time install).
I'm running the latest mythbuntu as of today.

I have both ip addresses under the general setup entered as the address reported by ifconfig for my ethernet card (my router always issues the same dhcp address to all machines based on mac address). I followed the setup instructions from the mythbuntu site.  I did have a problem with the storage directories, somehow I have an entry suck at '/' and the 'default' option generated 'no storage directories defined'

Now with the backend running, and starting the frontend, the watchtv command generates the big red X can't connect to backend.  
I checked the mysql bind address (changed it from "::" to the actual machine lan IP address), still same.

Any ideas?  Thanks.

---

### Post by uteck on 2016-09-04
Did you set the Frontend role using the control center?  That should set all the permissions needed.

---

### Post by nexzzt on 2016-09-05
Hello,

Have you checked the backend and frontend logs. They can found in:

/var/log/mythtv/mythbackend.log
/var/log/mythtv/mythfrontend.log

Cheers
Ben

---

### Post by buckh on 2016-09-27
Hi

I don't think this has any to do with the O.P. but i was looking for someplace to dump this, in case anybody ever manages to Google it up who's in the same predicament

Long story short:  I think i managed to change my backend server IP in mythtv-setup to my machine's "global" (RFC 1918-global) IP address rather than its loopback (127.0.0.1).  I was getting failures messages like these in syslog:

> Sep 27 00:35:31 mythbox gnome-session[2632]: 2016-09-27 00:35:31.126180 E  MythSocket(7f0f34003a80:-1): ReadStringList: Connection died.
Sep 27 00:35:31 mythbox gnome-session[2632]: 2016-09-27 00:35:31.126333 C  Protocol version check failure.
Sep 27 00:35:31 mythbox gnome-session[2632]: #011#011#011The response to MYTH_PROTO_VERSION was empty.
Sep 27 00:35:31 mythbox gnome-session[2632]: #011#011#011This happens when the backend is too busy to respond,
Sep 27 00:35:31 mythbox gnome-session[2632]: #011#011#011or has deadlocked due to bugs or hardware failure.
Sep 27 00:35:36 mythbox gnome-session[2632]: 2016-09-27 00:35:36.377808 I  MythCoreContext::ConnectCommandSocket(): Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
Sep 27 00:35:43 mythbox gnome-session[2632]: 2016-09-27 00:35:43.425697 E  MythSocket(7f0f34010200:50): ReadStringList: Error, timed out after 7000 ms.


after a long while and many clues from the net, i finally checked to see what my server IP was set as

> 
mysql> select * from settings where value like '%ServerIP';
+-----------------+----------------+-------------+
| value           | data           | hostname    |
+-----------------+----------------+-------------+
| BackendServerIP | 127.0.0.1      | OLDHOSTNAME |
| MasterServerIP  | 127.0.0.1      | NULL        |
| BackendServerIP | 127.0.0.1      | OLDHOSTNAME |
| BackendServerIP | 10.110.210.100 | mythbox     |
+-----------------+----------------+-------------+
4 rows in set (0.01 sec)

mysql> update settings set data = '127.0.0.1' where value like '%ServerIP' and data = '10.110.210.100';
Query OK, 1 row affected (0.01 sec)
Rows matched: 1  Changed: 1  Warnings: 0


and now it works.  (i shutdown the backend and frontend before doing the above, in case that's necessary)

whereas before (rest of the Google-fodder), nothing had recorded for the last 5 days, when i'd go to Schedule Recordings in the Program Finder, it wouldn't change the indicator colors to indicate that any of the programs were due to record, all the songs in my current playlist in mythmusic were causing errors, with big red X's popping up saying the path couldn't be found, etc.

---

