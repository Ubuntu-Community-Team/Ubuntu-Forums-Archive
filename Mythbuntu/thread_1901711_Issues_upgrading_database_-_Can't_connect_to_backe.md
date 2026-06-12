---
title: "Issues upgrading database - Can't connect to backend"
date: 2011-12-29
forum: Mythbuntu
---

### Post by BigPacks on 2011-12-29
I have Mythbuntu 10.04 running and I'm trying to setup Mythbuntu 11.10.

After getting the notorious HVR-2250 working for 11.10 (it was also working for 10.04), I was able to watch live tv from the frontend.  I.e. it would connect to the backend.

Now I'm trying to transfer my Mythbuntu 10.04 database into 11.10, but I can't connect to the backend.

I've copied all my */var/lib/mythtv* directories (like recordings, fanart, etc), backed up my old 10.04 database using [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore).  In 11.10, both the backend and frontend updated the schema but I think it worked?  When I test the remote connectivity of the MySQL database (via Mythbuntu Control Centre -> MySQL config) it says it's connected.  Also via MythWeb I can see my recording schedule.

I have my IP settings the same as it was for Mythbuntu10.04 (where I also had a remote frontend which could connect to the backend - but  I'm not using this machine).

In the backend I have the following:
Local backend IP address: 127.0.0.1
Remote backend IP address: 192.168.0.100 (static IP address of the backend)

Frontend
Backend IP address: localhost

I've tried various other combinations, such as having them all as 127.0.0.1, but without any luck.

I've attached a cut down version of both the backend and frontend log files after I replaced the database tonight (for the 3rd time).

I've noticed there's a problem.  In the frontend log, it has the following output
```
2011-12-29 19:40:31.766 mythfrontend version: fixes/0.24 [v0.24.1-80-g1de0431] www.mythtv.org
2011-12-29 19:40:31.766 Using runtime prefix = /usr
2011-12-29 19:40:31.766 Using configuration directory = /home/mythbuntu1110/.mythtv
2011-12-29 19:40:31.767 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-12-29 19:40:32.555 Empty LocalHostName.
2011-12-29 19:40:32.555 Using localhost value of mythbuntu1110-desktop
2011-12-29 19:40:32.567 New DB connection, total: 1
2011-12-29 19:40:32.576 Connected to database 'mythconverg' at host: localhost
2011-12-29 19:40:32.578 Closing DB connection named 'DBManager0'
2011-12-29 19:40:32.578 Connected to database 'mythconverg' at host: localhost
2011-12-29 19:40:32.697 Current locale en_AU
2011-12-29 19:40:32.836 No locale defaults file for en_AU, skipping
2011-12-29 19:40:33.038 ScreenSaverX11Private: XScreenSaver support enabled

```while the backend log file says this
```
2011-12-29 19:40:35.350 mythbackend version: fixes/0.24 [v0.24.1-80-g1de0431] www.mythtv.org
2011-12-29 19:40:35.450 Using runtime prefix = /usr
2011-12-29 19:40:35.546 Using configuration directory = /home/mythtv/.mythtv
2011-12-29 19:40:35.630 Unable to read configuration file mysql.txt
2011-12-29 19:40:35.751 Empty LocalHostName.
2011-12-29 19:40:35.871 Using localhost value of mythbuntu1110-desktop
2011-12-29 19:40:35.973 New DB connection, total: 1
2011-12-29 19:40:36.077 Unable to connect to database!
2011-12-29 19:40:36.171 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)
```My username is *mythbuntu1110*, so the frontend looks ok (*Using configuration directory = /home/mythbuntu1110/.mythtv*).  But the backend is trying to connect to the wrong location (*Using configuration directory = /home/mythtv/.mythtv*) and is unable to read mysql.txt.

I'm not sure why it's trying to go to */home/mythtv/*?In 10.04, my username is *mythbacked1.*

Is this because I've done something wrong trying to use the mythconverg_backup/mythconverg_restore scripts?

Is there a system file I can manually edit to fix this?

Anybody got any ideas?

PS.  I'm also not sure about the *Access denied for user 'mythtv'@'localhost' (using password: YES)* bit.

---

### Post by nickrout on 2011-12-30
> **BigPacks said:**
> I have Mythbuntu 10.04 running and I'm trying to setup Mythbuntu 11.10.

After getting the notorious HVR-2250 working for 11.10 (it was also working for 10.04), I was able to watch live tv from the frontend.  I.e. it would connect to the backend.

Now I'm trying to transfer my Mythbuntu 10.04 database into 11.10, but I can't connect to the backend.

I've copied all my */var/lib/mythtv* directories (like recordings, fanart, etc), backed up my old 10.04 database using [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore).  In 11.10, both the backend and frontend updated the schema but I think it worked?  When I test the remote connectivity of the MySQL database (via Mythbuntu Control Centre -> MySQL config) it says it's connected.  Also via MythWeb I can see my recording schedule.

I have my IP settings the same as it was for Mythbuntu10.04 (where I also had a remote frontend which could connect to the backend - but  I'm not using this machine).

In the backend I have the following:
Local backend IP address: 127.0.0.1
Remote backend IP address: 192.168.0.100 (static IP address of the backend)

Frontend
Backend IP address: localhost

I've tried various other combinations, such as having them all as 127.0.0.1, but without any luck.

I've attached a cut down version of both the backend and frontend log files after I replaced the database tonight (for the 3rd time).

I've noticed there's a problem.  In the frontend log, it has the following output
```
2011-12-29 19:40:31.766 mythfrontend version: fixes/0.24 [v0.24.1-80-g1de0431] www.mythtv.org
2011-12-29 19:40:31.766 Using runtime prefix = /usr
2011-12-29 19:40:31.766 Using configuration directory = /home/mythbuntu1110/.mythtv
2011-12-29 19:40:31.767 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-12-29 19:40:32.555 Empty LocalHostName.
2011-12-29 19:40:32.555 Using localhost value of mythbuntu1110-desktop
2011-12-29 19:40:32.567 New DB connection, total: 1
2011-12-29 19:40:32.576 Connected to database 'mythconverg' at host: localhost
2011-12-29 19:40:32.578 Closing DB connection named 'DBManager0'
2011-12-29 19:40:32.578 Connected to database 'mythconverg' at host: localhost
2011-12-29 19:40:32.697 Current locale en_AU
2011-12-29 19:40:32.836 No locale defaults file for en_AU, skipping
2011-12-29 19:40:33.038 ScreenSaverX11Private: XScreenSaver support enabled

```while the backend log file says this
```
2011-12-29 19:40:35.350 mythbackend version: fixes/0.24 [v0.24.1-80-g1de0431] www.mythtv.org
2011-12-29 19:40:35.450 Using runtime prefix = /usr
2011-12-29 19:40:35.546 Using configuration directory = /home/mythtv/.mythtv
2011-12-29 19:40:35.630 Unable to read configuration file mysql.txt
2011-12-29 19:40:35.751 Empty LocalHostName.
2011-12-29 19:40:35.871 Using localhost value of mythbuntu1110-desktop
2011-12-29 19:40:35.973 New DB connection, total: 1
2011-12-29 19:40:36.077 Unable to connect to database!
2011-12-29 19:40:36.171 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)
```My username is *mythbuntu1110*, so the frontend looks ok (*Using configuration directory = /home/mythbuntu1110/.mythtv*).  But the backend is trying to connect to the wrong location (*Using configuration directory = /home/mythtv/.mythtv*) and is unable to read mysql.txt.because mythbackend in ubuntu runs as user mythtv.

I assume if you are using localhost values you have a combined bck/front end and never want a remote frontend.

try ```
sudo dpkg-reconfigure mythtv-common
```> 

I'm not sure why it's trying to go to */home/mythtv/*?In 10.04, my username is *mythbacked1.*

Is this because I've done something wrong trying to use the mythconverg_backup/mythconverg_restore scripts?

Is there a system file I can manually edit to fix this?

Anybody got any ideas?

PS.  I'm also not sure about the *Access denied for user 'mythtv'@'localhost' (using password: YES)* bit.

---

### Post by BigPacks on 2011-12-30
nickrout,

I got impatient (needed to get it working by today) and decided that there was only a couple of things I really wanted to keep in my recordings so I decided not to bother upgrading the database.

Thanks for your help anyway.

---

