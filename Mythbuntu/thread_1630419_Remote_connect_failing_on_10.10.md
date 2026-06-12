---
title: "Remote connect failing on 10.10"
date: 2010-11-25
forum: Mythbuntu
---

### Post by nunrgguy on 2010-11-25
Just reinstalled from scratch to 10.10. Unable to connect any remote f/e to backend. Backend is on fixed IP. Local front end to backend is up and working. Backend is setup to allow remote front ends, pin is 0000. BUT if I run the test for remote connectivity on the local machine in mythcontrol centre it fails. IP addresses etc on the backend are all set for the actual IP rather than loopback. Is this something to do with one of the bugs I've heard about when switching from DHCP, which the system defaults to, to static or something else? Where else should I look in the system to resolve this?

MTIA

---

### Post by nunrgguy on 2010-11-25
Something strange here. Local front end on first boot also says cannot connect but when I re-run it it connects and we have TV.
System is setup for master backend roll, all IP addresses on both f/e/ and b/e are set as per the fixed IP, the IP is in mysql.txt, pin is set as 0000 and yet when I run test in myth control centre even on the master backend machine it fails.

---

### Post by nunrgguy on 2010-11-26
Settings:
fixed IP address of machine 192.168.1.110
Netmask 266.255.255.0
Gateway 192.168.1.254
DNS 192.168.1.254


F/E
Hostname: 192.168.1.110 (actual hostname has also been tried...still doesn't work)

B/E
Local Backend IP address: 192.168.1.110 port 6543 status port 6544
Security pin 0000

Master backend IP 192.168.1.110 port 6543

Mythbuntu control centre set for Enable Master backend role

Hosts file contains IPs for all eventualities i.e 127.0.0.1 and 192.168.1.110 are mapped to hostname mythtv

mysql...myconf have tried hashing out binding, makes no difference


MCC - 'test connection' still fails 

If you try to change anything here and change back you get the message: 
The MYsql plugin is not fully filled in, Please complete it before proceeding. The same message is encountered if you try to backup the database.

ALSO, on first boot local F/E says it cannot find the DB, click on OK and then it will merrily play TV anyway. F/E logs shows the following
2010-11-26 11:33:23.889 Using localhost value of mythtv
2010-11-26 11:33:23.889 Testing network connectivity to '192.168.1.110'
2010-11-26 11:33:24.002 New DB connection, total: 1
2010-11-26 11:33:24.007 Connected to database 'mythconverg' at host: 192.168.1.110
2010-11-26 11:33:24.058 Closing DB connection named 'DBManager0'
2010-11-26 11:33:24.070 Connected to database 'mythconverg' at host: 192.168.1.110

followed by
2010-11-26 11:33:32.167 MythCoreContext: Connecting to backend server: 192.168.1.110:6543 (try 1 of 1)
2010-11-26 11:33:32.167 Connection to master server timed out.
			Either the server is down or the master server settings
			in mythtv-settings does not contain the proper IP address

2010-11-26 11:33:32.168 Unable to determine master backend time zone settings.  If those settings differ from local settings, some functionality will fail.
2010-11-26 11:36:08.500 MythCoreContext: Connecting to backend server: 192.168.1.110:6543 (try 1 of 1)

The only corresponding error in the backend log at that time seems to be unrelated: 
2010-11-26 11:33:31.542 DVBChan(2:/dev/dvb/adapter0/frontend0) Warning: Your frequency setting (10891250) is out of range. (min/max:950000/2150000)
2010-11-26 11:33:31.662 New DB scheduler connection
2010-11-26 11:33:31.769 Connected to database 'mythconverg' at host: 192.168.1.110



??????
Stumped

---

### Post by nunrgguy on 2010-11-27
Couldn't find any way of fixing it, have had to re-install. Now tell me this...when installing from trial which you have to do to set static IP before install,which I did, after choosing primary backend with front end, WHY ON EARTH does the install revert to DHCP??? It's a nonesense yes?
At the moment the machine is, again setup with DHCP when I want static and all f/e and b/e settings are set to loopback. Why? Why would a master backend server be set for loopback?
Lets see if it messes it all up again going to static IP.

---

### Post by thatguruguy on 2010-11-27
Make sure that the frontend systems are running the same version of mythtv as the backend, or you won't be able to connect.

---

### Post by nunrgguy on 2010-11-28
Cheers m8 :) Yes they were all the same version. Even the f/e and b/e on the same system wouldn't pass the test. Ended up flattening it and doing it from scratch again. On four boxes it's taken almost the whole weekend but worth it. Now up and working and I haven't done anything different this time to last time so I don't know. May have been a bad install. Remote front end wouldn't connect again this time via pin so I skipped that and entered details manually and it worked. So now just have to sort out an xmltv issue and we're back up and running

---

### Post by screwbunt2 on 2011-01-06
BUMP...

I have the same bloody problem after upgrading from 9.1 to 10.04 and then 10.10. Everytime I try to make any changes in MCC (Mythbuntu Control Center), I get this message:

[B]"the mysql plugin is not fully filled out." Please complete it before proceding.
[/B] 
Where are you supposed to fill out whatever it is looking for and where is the plugin located?

Please help as I'm about ready to dig out my eyes or god forbid go back to tivo (NOT)!

I have a combined frontend/backend system, running myth .24 / ubuntu 10.10.
Other database functions seem to be fine as I can record etc. and even access it with mythweb.

Which logfile should I be looking in?


THANKS!

---

### Post by screwbunt2 on 2011-01-06
Additional info from /var/log/mysql/error.log

110106 16:16:55 [Note] Plugin 'FEDERATED' is disabled.
110106 16:16:57  InnoDB: Started; log sequence number 0 1885745
110106 16:16:58 [Note] Event Scheduler: Loaded 0 events
110106 16:16:58 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.1.49-1ubuntu8.1'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
110106 16:17:00 [ERROR] Invalid (old?) table or database name 'mythconverg.BAK'


There are a BUNCH of the last line about **mythconverg.BAK**

Why would it be using a backup version of my database and how do I reset it to **mythconverg** ?

What is the FEDERATED pluging that has been disabled?

Is the mysql.sock port correct, if not, where do I change it?

THANKS!

---

### Post by screwbunt2 on 2011-01-07
Ok, I figured out part of the problem, but still need help with the original error.

The part I figured out was the **mythconverg.BAK error**. At some point in the past I 'backed up' my database by copying the directory /var/lib/mysql/mythconverg  to  /var/lib/mysql/mythconverg.BAK....  So deleting or moving that directory out of /var/lib/mysql cleared up that error in the logfile, but I'm still stuck with the original problem.

I've found several other threads of people with the same problem I need help with, but none of them have any real solution because everyone seems to have given up and reinstalled from scratch, which I'm not willing to do because I have way too much time into customizing this system!

---

### Post by theDaveTheRave on 2011-01-07
for information...

the 'federated' engine is a DB engine, I believe that it has been dropped from the more recent list DB engine options by MySQL

(quick history/info, from what I have read / understand)... MySQL uses the 'myisam' DB engine by default. with options for a whole bunch of others (I use InnoDB for my dbases - they are apparently better for 'large' table - and I mean large, 50 - 60 million lines per table, 20 - 30 tables etc etc). When MySQL was taken over by Sun, a bunch of the original developers jumped ship, when Sun was acquired by Oracle, a whole bunch more departed.

This group started a new DBMS called 'mariaSQL' (the name of the second daughter is 'maria', the first being My). Maria closely tracked the changes in the MySQL system, and developed it's own truly open source / freedom included DB engine (called mariaDB). This is now included in the options of the soon to be released versions of MySQL - it may even be available in the current version as an option. I believe that in time mariaDB is expected to become the standard DB engine for MySQL
(end of history lesson... sorry to be so much of a 'geek' about it, and feel free to correct any errors).

so if 'FEDERATED' plugin is dasabled I wouldn't worry about it.

There have been a number of issues with MySQL with the updates (which I have suffered from) and ended up performing an install from source - this was related to a problem with the current condition of upstart for the mysql server.

I also noted that when I installed from source a number of things that used mysql where looking for a 'mysql.sock' file that didn't exist. This simply required the creation of a symbolic link to the correct location for the various systems (my problem one was for a test install of sugarCRM - nice package by the way).

so to answer some of the other questions...

the mysql.sock port of 3306 is the 'default' port for mysql to listen to connections on.
When I ran a test system I had it listen on port 3309, and to be honest I could access all the tables on both systems via either port - which I found strange - but I think may have been related to the mysql.sock file being in the same place. So I would assume that so long as the sock file is where it is expected to be you should be able to 'see' all the various tables you need to. You could test this with phpmyadmin (or similar) or directly with from the command line mysqlmonitor (or the mysql gui tools).

Remeber if you are trying to do change details in your my.cnf file you will need to start firefox as 'sudo' and then go to the relevant phpmyadmin page (same goes for the mysql monitor / gui tools) or you can't write to the my.cnf file.

alternatively you can edit it by hand using gedit, vi or whatever you fance (again you need sudo remember). Remember to make a copy /backup first - and comment your changes.

so that said, if you are trying to make changed in Myth control center are you starting it with sudo? or it may not be able to access the file to 'fill out' the plugin?

That is the best I can do for help, for now, report back on success or otherwise.

David

---

### Post by screwbunt2 on 2011-01-07
David,

Thanks for the background/history. I was a little curious how things were going to change with mysql/Myth after the sun/oracle deal.

I have verified the mysql.sock/link/port stuff you mentioned, and read elsewhere that the FEDERATED stuff isn't an issue. I've been going through log files tackling all the strange little things I can find and noticing little improvements, but still no luck with my original problem. I also wanted to confirm that I tried running MCC/Mythbuntu Control Center as root and still no luck. Orignally I was getting the error when trying to do a backup from control center, but last attempt that worked, but simply trying to toggle themes on/off gives the error.

Anyway, I'm about to get some sleep, so I'll check back tomorrow.

Thanks!

---

### Post by screwbunt2 on 2011-01-16
Update: Still haven't solved this. 

Mythbuntu .24 / Ubuntu 10.10

Mythbuntu Control Center (MCC) Plug-In Incomplete Error when applying/saving changes

Thanks

---

### Post by markackerman8@gmail.com on 2011-09-14
Completely removed Mythtv and re installed, and no synaptic or purge commands don't work... 

you need to also remove all contents in:

/var/lib/mythtv & mysql
/usr/share/mythtv & mysql
/home/myhtv

reinstall
Done Solved

---

### Post by Randall311 on 2011-12-20
```
sudo dpkg-reconfigure mythweb_password mythweb_auth mythweb_user
```

boom... done!

---

