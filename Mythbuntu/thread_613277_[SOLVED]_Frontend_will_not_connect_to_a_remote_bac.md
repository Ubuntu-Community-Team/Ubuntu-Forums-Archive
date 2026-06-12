---
title: "[SOLVED] Frontend will not connect to a remote backend"
date: 2007-11-14
forum: Mythbuntu
---

### Post by kingjos on 2007-11-14
Ok so I have  a  standalone frontend machine that i'm trying to have connect to my masterbackend but am having no luck what soever with this issue.  I have already configured the backend to to allow external access to mythbackend and the mysql server so i  know thats not the problem. 

Here is the content of /var/log/mythtv/mythfrontend.log

Starting mythfrontend.real..
2007-11-13 19:08:30.509 Current Schema Version: 1160
2007-11-13 19:08:30.510 mythfrontend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2007-11-13 19:08:30.510 Enabled verbose msgs:  important general
2007-11-13 19:08:31.271 Total desktop dim: 640x480, with 1 screen[s].
2007-11-13 19:08:31.272 Using screen 0, 640x480 at 0,0
2007-11-13 19:08:31.273 Switching to square mode (Mythbuntu)
2007-11-13 19:08:31.295 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-11-13 19:08:31.483 Joystick disabled.
2007-11-13 19:08:52.678 Loading from: /usr/share/mythtv/themes/Mythbuntu/base.xml
2007-11-13 19:08:52.690 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-11-13 19:08:55.238 Registering Internal as a media playback plugin.
2007-11-13 19:08:55.365 Registering MythDVD DVD Media Handler as a media handler ext()
2007-11-13 19:08:55.366 Registering MythDVD VCD Media Handler as a media handler ext()
2007-11-13 19:08:55.446 Registering MythGallery Media Handler 1/2 as a media handler ext()
2007-11-13 19:08:55.446 Registering MythGallery Media Handler 2/2 as a media handler ext(gif,jpg,png)
Failed to run 'cdrecord --scanbus'
Failed to run 'cdrecord --scanbus'
Failed to run 'cdrecord --scanbus'
2007-11-13 19:08:55.741 Registering MythMusic Media Handler 1/2 as a media handler ext()
2007-11-13 19:08:55.742 Registering MythMusic Media Handler 2/2 as a media handler ext(ogg,mp3,aac,flac)
SIP: Creating autogen directory entry for this host
SIP listening on IP Address 192.168.1.169:5060 NAT address 192.168.1.169
SIP: Cannot register; proxy, username or password not set
2007-11-13 19:10:06.113 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-11-13 19:10:06.113 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.
Destroying SipFsm object 
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..

any imput would be welcome:

---

### Post by superm1 on 2007-11-14
> **kingjos said:**
> Ok so I have  a  standalone frontend machine that i'm trying to have connect to my masterbackend but am having no luck what soever with this issue.  I have already configured the backend to to allow external access to mythbackend and the mysql server so i  know thats not the problem. 

Here is the content of /var/log/mythtv/mythfrontend.log

Starting mythfrontend.real..
2007-11-13 19:08:30.509 Current Schema Version: 1160
2007-11-13 19:08:30.510 mythfrontend version: 0.20.20070821-1 [www.mythtv.org]("http://www.mythtv.org")
2007-11-13 19:08:30.510 Enabled verbose msgs:  important general
2007-11-13 19:08:31.271 Total desktop dim: 640x480, with 1 screen[s].
2007-11-13 19:08:31.272 Using screen 0, 640x480 at 0,0
2007-11-13 19:08:31.273 Switching to square mode (Mythbuntu)
2007-11-13 19:08:31.295 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-11-13 19:08:31.483 Joystick disabled.
2007-11-13 19:08:52.678 Loading from: /usr/share/mythtv/themes/Mythbuntu/base.xml
2007-11-13 19:08:52.690 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-11-13 19:08:55.238 Registering Internal as a media playback plugin.
2007-11-13 19:08:55.365 Registering MythDVD DVD Media Handler as a media handler ext()
2007-11-13 19:08:55.366 Registering MythDVD VCD Media Handler as a media handler ext()
2007-11-13 19:08:55.446 Registering MythGallery Media Handler 1/2 as a media handler ext()
2007-11-13 19:08:55.446 Registering MythGallery Media Handler 2/2 as a media handler ext(gif,jpg,png)
Failed to run 'cdrecord --scanbus'
Failed to run 'cdrecord --scanbus'
Failed to run 'cdrecord --scanbus'
2007-11-13 19:08:55.741 Registering MythMusic Media Handler 1/2 as a media handler ext()
2007-11-13 19:08:55.742 Registering MythMusic Media Handler 2/2 as a media handler ext(ogg,mp3,aac,flac)
SIP: Creating autogen directory entry for this host
SIP listening on IP Address 192.168.1.169:5060 NAT address 192.168.1.169
SIP: Cannot register; proxy, username or password not set
2007-11-13 19:10:06.113 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-11-13 19:10:06.113 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.
Destroying SipFsm object 
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..

any imput would be welcome:

2007-11-13 19:10:06.113 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-11-13 19:10:06.113 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.

Go into mythtv-setup on the BE and set it up properly.  You need to modify the master backend server box.

---

### Post by kingjos on 2007-11-14
When I go into  mythtv-setup on my masterbackend under the general section  it is showing the static ip address  of the backend machine.  Any other ideas?

---

### Post by kingjos on 2007-11-14
Also, can you tell me how to start the frontend application from the command prompt?

---

### Post by kingjos on 2007-11-14
I dont know if this will help at all but here is the output from /var/log/mythtv/masterbackend.log on my masterbackend  machine.

Starting up as the master server.
2007-11-14 16:52:05.176 New DB connection, total: 2
2007-11-14 16:52:05.177 Connected to database 'mythconverg' at host: localhost
2007-11-14 16:52:05.180 EITHelper: localtime offset -6:00:00 
2007-11-14 16:52:05.184 New DB connection, total: 3
2007-11-14 16:52:05.185 Connected to database 'mythconverg' at host: localhost
2007-11-14 16:52:05.341 EITHelper: localtime offset -6:00:00 
2007-11-14 16:52:05.485 New DB scheduler connection
2007-11-14 16:52:05.486 Connected to database 'mythconverg' at host: localhost
2007-11-14 16:52:06.835 Main::Registering HttpStatus Extension
2007-11-14 16:52:06.836 mythbackend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2007-11-14 16:52:06.837 Enabled verbose msgs:  important general
2007-11-14 16:52:06.837 AutoExpire: Found 2 recorders w/max rate of 144 MiB/min
2007-11-14 16:52:06.839 AutoExpire: Required Free Space: 3.1 GB w/freq: 10 min
2007-11-14 16:52:07.492 Reschedule requested for id -1.
2007-11-14 16:52:07.586 Scheduled 0 items in 0.1 = 0.08 match + 0.01 place
2007-11-14 16:52:07.590 Seem to be woken up by USER
2007-11-14 18:18:07.833 Using runtime prefix = /usr
2007-11-14 18:18:07.857 New DB connection, total: 1
2007-11-14 18:18:07.890 Connected to database 'mythconverg' at host: localhost
2007-11-14 18:18:07.894 Current Schema Version: 1160
Starting up as the master server.
2007-11-14 18:18:07.907 New DB connection, total: 2
2007-11-14 18:18:07.908 Connected to database 'mythconverg' at host: localhost
2007-11-14 18:18:07.910 EITHelper: localtime offset -6:00:00 
2007-11-14 18:18:07.914 New DB connection, total: 3
2007-11-14 18:18:07.915 Connected to database 'mythconverg' at host: localhost
2007-11-14 18:18:08.230 EITHelper: localtime offset -6:00:00 
2007-11-14 18:18:08.373 New DB scheduler connection
2007-11-14 18:18:08.374 Connected to database 'mythconverg' at host: localhost
2007-11-14 18:18:09.726 Main::Registering HttpStatus Extension
2007-11-14 18:18:09.727 mythbackend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2007-11-14 18:18:09.728 Enabled verbose msgs:  important general
2007-11-14 18:18:09.728 AutoExpire: Found 2 recorders w/max rate of 144 MiB/min
2007-11-14 18:18:09.730 AutoExpire: Required Free Space: 3.1 GB w/freq: 10 min
2007-11-14 18:18:10.385 Reschedule requested for id -1.
2007-11-14 18:18:10.846 Scheduled 0 items in 0.5 = 0.45 match + 0.01 place
2007-11-14 18:18:10.851 Seem to be woken up by USER
2007-11-14 18:20:50.316 Using runtime prefix = /usr
2007-11-14 18:20:50.561 New DB connection, total: 1
2007-11-14 18:20:50.587 Connected to database 'mythconverg' at host: localhost
2007-11-14 18:20:50.656 Current Schema Version: 1160
Starting up as the master server.
2007-11-14 18:20:50.722 New DB connection, total: 2
2007-11-14 18:20:50.729 Connected to database 'mythconverg' at host: localhost
2007-11-14 18:20:50.733 EITHelper: localtime offset -6:00:00 
2007-11-14 18:20:50.887 New DB connection, total: 3
2007-11-14 18:20:50.901 Connected to database 'mythconverg' at host: localhost
2007-11-14 18:20:51.117 EITHelper: localtime offset -6:00:00 
2007-11-14 18:20:51.330 New DB scheduler connection
2007-11-14 18:20:51.360 Connected to database 'mythconverg' at host: localhost
2007-11-14 18:20:52.951 Main::Registering HttpStatus Extension
2007-11-14 18:20:53.060 mythbackend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2007-11-14 18:20:53.096 Enabled verbose msgs:  important general
2007-11-14 18:20:53.096 AutoExpire: Found 2 recorders w/max rate of 144 MiB/min
2007-11-14 18:20:53.098 AutoExpire: Required Free Space: 3.1 GB w/freq: 10 min
2007-11-14 18:20:53.458 Reschedule requested for id -1.
2007-11-14 18:20:53.757 Scheduled 0 items in 0.3 = 0.28 match + 0.01 place
2007-11-14 18:20:53.788 Seem to be woken up by USER

---

### Post by road2elysium on 2007-11-16
> **kingjos said:**
> When I go into  mythtv-setup on my masterbackend under the general section  it is showing the static ip address  of the backend machine.  Any other ideas?

You may have to change the IP in more than one place in the mythtv-setup.  Check out this table:
[http://www.mythtv.org/wiki/index.php/User_Manual:Detailed_configuration_Backend#Backend_Configuration]("http://www.mythtv.org/wiki/index.php/User_Manual:Detailed_configuration_Backend#Backend_Configuration")

> **kingjos said:**
> Also, can you tell me how to start the frontend application from the command prompt?

It's probably in /etc/init.d/[mythfrontend or the like] or in /usr/sbin.
Try to do a locate in those directories.

---

### Post by superm1 on 2007-11-16
> **kingjos said:**
> Also, can you tell me how to start the frontend application from the command prompt?
```
mythfrontend
```

---

### Post by newlinux on 2007-11-16
It looks like your frontend is trying to connect to a local backend (127.0.0.1(. You are trying to connect to a remote backend, correct? Make sure your frontend is configured to connect to the IP of your backend. It is in the general section of your frontend's setup menu.

---

### Post by djkmyth on 2008-01-12
Hi,

I have this same problem running mythbuntu as a frontend-only.

I have set up the backend for network access, and have used other windows frontends with it.

The mythbuntu frontend is set up with the correct user, pass, ip for the backend, and passes the connection test.

The frontend _can_ see the backend, as it can successfully browse the previously recorded menu and see all the programs. 

But when trying to watch recordings I notice that the frontend log claims to be trying to access 127.0.0.1 on port 6543.  That is, the frontend is trying to access a local backend, not the one on the IP address I gave it for the master.  So the master backend config isn't involved in this problem?

I suspect this is also the problem that kingjos is having?

** Is there some hard-coded 127.0.0.1 IP address in the mythfrontend source code?

** Is there _another_ place where the backend IP must be entered?

** I'm just about to consider some tunneling program to listen on 6543 locally and tunnel the connection to my real backend!!!

djkmyth

---

### Post by superm1 on 2008-01-12
> **djkmyth said:**
> Hi,

I have this same problem running mythbuntu as a frontend-only.

I have set up the backend for network access, and have used other windows frontends with it.

The mythbuntu frontend is set up with the correct user, pass, ip for the backend, and passes the connection test.

The frontend _can_ see the backend, as it can successfully browse the previously recorded menu and see all the programs. 

But when trying to watch recordings I notice that the frontend log claims to be trying to access 127.0.0.1 on port 6543.  That is, the frontend is trying to access a local backend, not the one on the IP address I gave it for the master.  So the master backend config isn't involved in this problem?

I suspect this is also the problem that kingjos is having?

** Is there some hard-coded 127.0.0.1 IP address in the mythfrontend source code?

** Is there _another_ place where the backend IP must be entered?

** I'm just about to consider some tunneling program to listen on 6543 locally and tunnel the connection to my real backend!!!

djkmyth
The only area that this is configured is in the two dialog boxes in mythtv-setup.  Odds are one of them is wrong.

---

### Post by djkmyth on 2008-01-13
Aha,

Now I finally get it - the front end connects to the backend SQL database first, then uses the IP it gets from  the backend database to connect to the mythtv backend, which was still 127.0.0.1.  Presumably this is to allow the SQL database to reside on a different machine to the mythtv backend.

My other pseudo-frontend solutions were using the same address for both, configured at the frontend, so that's why I hadn't seen the problem to date.

Sorry for being thick...


Cheers,
DJKMyth

---

### Post by jeepGuy on 2009-07-03
Thanks for your insight. After a couple unsuccessful tries with the setup program, I went directly to the settings table and updated the data column. Worked like a charm!


[FONT="Courier New"][FONT="Courier New"][/FONT]
$ mysql -u mythtv -h localhost -p

mysql> use mythconverg;

Database changed
mysql> select * from settings where data like '127%';
+-----------------+-----------+-------------+
| value           | data      | hostname    |
+-----------------+-----------+-------------+
| BackendServerIP | 127.0.0.1 | OLDHOSTNAME | 
| MasterServerIP  | 127.0.0.1 | NULL        | 
| BackendServerIP | 127.0.0.1 | OLDHOSTNAME | 
| BackendServerIP | 127.0.0.1 | mythbuntu   | 
+-----------------+-----------+-------------+
4 rows in set (0.00 sec)

mysql> update settings set data = '192.168.1.27' where data = '127.0.0.1';
Query OK, 4 rows affected (0.00 sec)
Rows matched: 4  Changed: 4  Warnings: 0

mysql> select * from settings where data like '192%';
+-----------------+---------------+-------------+
| value           | data          | hostname    |
+-----------------+---------------+-------------+
| BackendServerIP | 192.168.1.27  | OLDHOSTNAME | 
| MasterServerIP  | 192.168.1.27  | NULL        | 
| BackendServerIP | 192.168.1.27  | OLDHOSTNAME | 
| BackendServerIP | 192.168.1.27  | mythbuntu   | 
+-----------------+---------------+-------------+
4 rows in set (0.00 sec)
[/FONT]

---

