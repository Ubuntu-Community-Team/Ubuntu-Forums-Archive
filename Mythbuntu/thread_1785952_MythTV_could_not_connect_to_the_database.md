---
title: "MythTV could not connect to the database"
date: 2011-06-19
forum: Mythbuntu
---

### Post by milesnorth on 2011-06-19
Have been using mythtv under kubuntu for 3-4 years now.  Watched Alien last night, shutdown, logged on today, and mythtv fails to connect to the database.  Both mythtv frontend and backend setup popup a "countries of the world" screen I've never seen before, then go to a screen that says "no upnp", then go to the database configuration screen.  The database server settings were hostname: localhost - Port: -blank- - Database name: mythconverge - User: mythtv - Password: -assigned-.

Went to konsole and got the following message:
```
mysql -u root mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2).
```I don't futz around with mythtv much or mysql ever.  I checked the root partition and noticed the partition was almost 100% full.  So I ran bleachbit and cleared off several gigs of crude.  All the same problems remain.  

My linux knowledge is mediocre to moderate and any suggestions would be greatly appreciated.

Kurt

---

### Post by klc5555 on 2011-06-19
It would appear that when your root partition maxed out, you corrupted your mythconverg database. At least. Maybe additional stuff as well.

Usual first attempt at a repair would consist of running from a prompt:
 mysqlcheck --databases mythconverg --auto-repair

as described in the mysqlcheck man page (or here: [http://linuxcommand.org/man_pages/mysqlcheck1.html](http://linuxcommand.org/man_pages/mysqlcheck1.html)) and see how it goes.

---

