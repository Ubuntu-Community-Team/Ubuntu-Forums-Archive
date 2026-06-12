---
title: "Upgrade to 8.04 from 7.10 - Database can not upgrade"
date: 2008-04-29
forum: Mythbuntu
---

### Post by hansoffate on 2008-04-29
I tried launching mythfrontend after the upgrade and nothing happened.  After that, I ran mythfrontend in terminal and found out that I need to upgrade the database by running mythtv-setup.  After running mythtv-setup, I try upgrading the database and do a mythfill, but I still have the same issue.

Any ideas on how to fix this?

Thanks,
Hans

---

### Post by laga on 2008-04-29
Hi,

could you please provide some logs or error messages? Eg what does mythtv-setup say in the terminal?

---

### Post by hansoffate on 2008-04-29
```
hansoffate@grunt:~$ mythtv-setup
 * Stopping MythTV server: mythbackend                                          No /usr/bin/mythbackend found running; none killed.
                                                                         [ OK ]
 * Restarting MythTV server: mythbackend                                        No /usr/bin/mythbackend found running; none killed.
                                                                         [ OK ]
hansoffate@grunt:~$ mythfrontend
2008-04-29 11:20:09.786 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-29 11:20:10.432 XScreenSaver support enabled
2008-04-29 11:20:10.432 DPMS is active.
2008-04-29 11:20:10.433 Empty LocalHostName.
2008-04-29 11:20:10.433 Using localhost value of grunt
2008-04-29 11:20:10.433 Testing network connectivity to 192.168.1.109
2008-04-29 11:20:10.499 New DB connection, total: 1
2008-04-29 11:20:10.515 Connected to database 'mythconverg' at host: 192.168.1.109
2008-04-29 11:20:10.516 Closing DB connection named 'DBManager0'
2008-04-29 11:20:10.517 Primary screen 0.
2008-04-29 11:20:10.530 Connected to database 'mythconverg' at host: 192.168.1.109
2008-04-29 11:20:10.531 Using screen 0, 1024x768 at 0,0
2008-04-29 11:20:10.538 New DB connection, total: 2
2008-04-29 11:20:10.550 Connected to database 'mythconverg' at host: 192.168.1.109
2008-04-29 11:20:10.551 Unexpected DB Schema version.  Waiting to see if DB is being upgraded.
2008-04-29 11:20:15.559 Timed out waiting.
2008-04-29 11:20:15.559 This version of MythTV requires an updated database schema. Please run mythtv-setup or mythbackend to update your database.
hansoffate@grunt:~$ 

```

I run mythtv-setup.  It asks me if I want to upgrade from 1180 to 1214, so I say Upgrade both times and exit the setup.  I then tried to run mythfrontend and this is all the output I got.  

Thanks for the help,
Hans

---

### Post by hansoffate on 2008-04-29
Update:
I just tried to drop database and recreate it from the backups, but i kept getting Unknown database.  

I then tried a complete removal of mythtv, myth-backend, myth-database.  I then installed them again and "sudo dpkg-reconfigure mythtv-database"
Afterwards, i tried to go to mythtv-setup, and I got the same upgrade from 1180 to 1214

Any other ways to try to fix this?  Should I just download the 8.04 and do a fresh install?

Thanks for the help,
Hans

---

### Post by UponFirstListen on 2008-05-01
Having a similar problem over here. I upgraded my laptop to 8.04 and am trying to connect to a backend located on a machine running 7.10. Getting the same "This version of MythTV requires an updated database schema. Please run mythtv-setup or mythbackend to update your database." error. Tried removing and reinstalling with no luck. Haven't tried messing the the backend computer, but may try later tonight.

---

### Post by superm1 on 2008-05-01
It sounds like there might be corruption in the DB, you can try to optimize your tables/repair them from either mythweb (on 0.21) or from phpmyadmin, or command line

---

### Post by hansoffate on 2008-05-01
I tried connecting to mythweb, but I couldn't since my backend wasn't up because the mysql database was broken.  I installed phpmyadmin, repaired and optimized everything with Mythconverg.  I went back into mythtv-setup and performed the upgrade.  This time, it was able to back up the mysql database and upgrade the schema. 

Everything seems to be working now.  Thanks for the help superm1.

---

### Post by UponFirstListen on 2008-05-03
I haven't had the time to investigate the issue further, but I realize I didn't give you the full breakdown of my setup.

Main: Front and Backend running Ubuntu 7.04
Secondary: Frontend only runnig Kubuntu 7.04
Tertiary: Frontend only running Kubuntu 8.04

The Main and Secondary systems are working properly, connecting to the database without issue. It's only the Tertiary system that seems to be having a problem. 

Unfortunately, I work at a baseball stadium and we are in the middle of a homestand, which means I have no free time to mess with it, but I'll be looking at it more in depth next week (because it also messed up my fstab and I can no longer mount network drives the the 8.04 install).

---

