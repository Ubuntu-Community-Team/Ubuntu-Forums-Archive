---
title: "can't connect to master backend server? I've set IP's???"
date: 2008-04-28
forum: Mythbuntu
---

### Post by callagga on 2008-04-28
Hi,

I've been getting the "Could not connect to the master backend server -- is it running?  Is the IP address set for it in setup program correct?".

I've installed Mythbuntu, and I've also done the important system updates.  

I have tried setting the client and server to both my internal IP address that my router dishes out (DHCP) as well as 127.0.0.1.  I still seem to get this message.  I did actually have things working yesterday (watching TV via the front end) however obviously after I restarted it's not working again.  I do note also that my wireless settings seem to get stuffed up after each reboot and I have to set them up again.  I'm running front and backend on the same PC, however would like it so I can run a front end from another PC too.  

Q1 - How can I fault find this issue?
Q2 - How do I verify that the backend is running?  How do I start/restart the backend. 

Thanks heaps.  I'm getting nowwhere myself for the moment.  Let me know if I need to post anymore details.

Regards

---

### Post by justanotherhack on 2008-04-28
I had a similar problem, which occured to be a problem with the database. Evidently the database couldn't be created, since I changed the the root password for MySQL during the (alternate) install. Also there was a problem with writing the MySQL password set in the Mythbuntu configuration tool to the /etc/mythtv/mysql.txt (or so... my HTPC is about 10 miles away, so I can't confirm the name).

Try logging into the MySQL DB and check if the mythconverg database is there. Proceed like this:
```
mysql -u root -p
show databases
```

You can check, if it is running, with
```
ps aux | grep myth
```

In case that ain't the reason, check the MythTV backend log in /var/log/mythtv (or so ;) ).

---

### Post by callagga on 2008-04-28
I get the following:

[1] Re database.  I noted my password was <blank> for the database.  Should this match the one I configured to get out of mythtv front end to the admin area?   

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema | 
| mysql              | 
| mythconverg        | 
+--------------------+

[2] Is the following OK? 
greg@mythtv:~$ ps aux | grep myth
greg      5251  0.0  0.0   4436   388 ?        Ss   19:18   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/share/mythbuntu/session.sh
greg      5254  0.0  0.1   2700   620 ?        S    19:18   0:00 /usr/bin/dbus-launch --exit-with-session /usr/share/mythbuntu/session.sh
greg      5299  0.6 12.2 170608 60904 ?        Ssl  19:18   0:56 /usr/bin/mythfrontend.real --logfile /var/log/mythtv/mythfrontend.log 
greg      6263  0.0  0.1   2976   756 pts/0    R+   21:41   0:00 grep myth

BTW - How does one shutdown and start up the backend?

Thanks

---

### Post by justanotherhack on 2008-04-28
Looks like the backend is really not running. You can start it with (something like):
```
sudo /etc/init.d/mythtv-backend start
```
(instead of start you can use stop and restart for the matching job)

If the backend still doesn't run, check the log.

Regarding the database, you must have the same password in the /etc/mythtv/mysql.txt, as you have set within the MySQL database. If you're not sure, if you have set the correct password there, you can change it with:
```
SET PASSWORD FOR 'mythtv'@'localhost' = PASSWORD('newpassword');
```
or if you're not sure the priviliges for the user are correct, you can reset them as well with
```
GRANT ALL ON mythconverg.* TO 'mythtv'@'localhost' IDENTIFIED BY PASSWORD newpassword;
```
(newpassword being the new password of course)

---

### Post by callagga on 2008-04-28
after starting got this:

```
greg@mythtv:/etc/init.d$ sudo /etc/init.d/mythtv-backend start
[sudo] password for greg:
 * Removing stale PID file /var/run/mythtv/mythbackend
 * Starting MythTV server: mythbackend                                                                                               [ OK ] 
greg@mythtv:/etc/init.d$ 
greg@mythtv:/etc/init.d$ 
greg@mythtv:/etc/init.d$ ps aux | grep myth
greg      5251  0.0  0.0   4436   388 ?        Ss   19:18   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/share/mythbuntu/session.sh
greg      5254  0.0  0.1   2700   620 ?        S    19:18   0:00 /usr/bin/dbus-launch --exit-with-session /usr/share/mythbuntu/session.sh
greg      5299  0.6 13.4 174648 67280 ?        Ssl  19:18   1:08 /usr/bin/mythfrontend.real --logfile /var/log/mythtv/mythfrontend.log 
greg      6317  0.0  0.1   2976   756 pts/0    R+   22:03   0:00 grep myth
greg@mythtv:/etc/init.d$ 
```

If I check the logs I see in:
```

pr 28 22:08:13 mythtv ntpd[4946]: unable to create socket on wlan0 (35) for fe80::21c:f0ff:fe9d:xxxx#xxx
Apr 28 22:08:13 mythtv ntpd[4946]: failed to initialize interface for address fe80::21c:f0ff:xxxx:xxxx
```

I see a mythbackend.log file.  It had:

```
2008-04-28 22:13:56.350 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-28 22:13:56.358 Empty LocalHostName.
2008-04-28 22:13:56.358 Using localhost value of mythtv
2008-04-28 22:13:56.376 New DB connection, total: 1
2008-04-28 22:13:56.396 Connected to database 'mythconverg' at host: localhost
2008-04-28 22:13:56.399 Closing DB connection named 'DBManager0'
2008-04-28 22:13:56.400 Connected to database 'mythconverg' at host: localhost
2008-04-28 22:13:56.403 New DB connection, total: 2
2008-04-28 22:13:56.404 Connected to database 'mythconverg' at host: localhost
2008-04-28 22:13:56.406 Current Schema Version: 1214
Starting up as the master server.
2008-04-28 22:13:56.416 New DB connection, total: 3
2008-04-28 22:13:56.418 Connected to database 'mythconverg' at host: localhost
2008-04-28 22:13:56.428 DVBChan(1:0) Warning: Unsupported constellation parameter.
2008-04-28 22:13:56.740 New DB scheduler connection
2008-04-28 22:13:56.741 Connected to database 'mythconverg' at host: localhost
 is defined, but isn't attached to a cardinput.
2008-04-28 22:13:56.756 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-04-28 22:13:56.757 Main::Registering HttpStatus Extension
2008-04-28 22:13:56.757 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-04-28 22:13:56.758 Enabled verbose msgs:  important general
2008-04-28 22:13:56.760 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
QServerSocket: failed to bind or listen to the socket
2008-04-28 22:13:56.764 Failed to bind port 43. Exiting.
```

Does this help?

---

### Post by justanotherhack on 2008-04-28
Okay, so it won't start.

The part in the normal log is another problem, you can ignore it for now. (But maybe look into it later, it's about time synchronisation, which is always a good thing.)

The backend log gives a few hints. But I can't confirm them without checking on my own box (not before tomorrow night). Let's see.
Well, first I made the wrong suggestion. Don't start mythtv-backend as root. Just came to me, that your regular user has to be able to do so, as a member of the mythtv group. (Mythbuntu should have done this for you, when you started the configuration tool, if not, add your user to the mythtv group.)

Now, what looks strange, is that the backend is trying to bind to port 43 (that's usually for the whois protocol, mythtv uses... erm... 6543 I think). The configurations seems a bit messed up here. The Mythbuntu backend configuration tool let's you configure the ports. Check what they are set to.

Maybe you could post your backend configuration file from /etc/mythtv.

---

### Post by callagga on 2008-04-28
this is all in this directory - no mentioned of backend config?  The files in this directory look to be more scripts no?  Doesn't seem to be settings so much?
```

greg@mythtv:/etc/mythtv$ ls -l
total 32
-rw-r--r-- 1 root   root       78 2008-04-28 18:05 mysql.txt
-rw-r--r-- 1 root   root     1980 2008-03-12 01:11 mythweb-canned_searches.conf.php
-rw-r--r-- 1 root   root     4721 2008-03-12 01:11 mythweb-config.php
-rw-r----- 1 mythtv www-data   49 2008-04-28 18:07 mythweb-digest
-rw-r--r-- 1 root   root     6296 2008-04-28 03:24 mythweb-htaccess
-rw-r--r-- 1 root   root     1190 2008-03-11 08:15 session-settings
greg@mythtv:/etc/mythtv$ 
```

I did see this:
```
greg@mythtv:/etc/mythtv$ sudo find / -name *backend*config
/var/lib/dpkg/info/mythtv-backend.config
greg@mythtv:/etc/mythtv$ cat /var/lib/dpkg/info/mythtv-backend.config
#!/bin/sh -e

. /usr/share/debconf/confmodule

db_input low mythtv/create_v4l_devs || true
db_input high mythtv/run_setup || true
db_go

exit 0
greg@mythtv:/etc/mythtv$ 
```

Thanks for helping so far.  I'm real keen to get myth working.  Any ideas re where to next?  Can I post any other files?

---

### Post by justanotherhack on 2008-04-28
I'm terribly sorry, I've been mixing things up in my reply and am causing confusion. (But strangely I had it correct in another topic. I should restrain from posting in forums as a diversion from doing account management skrips in Perl. Anyway, back to your problem.)

The configuration resides in the MySQL database. In the "settings" table to be precise. Now, do the following
```
mysql -u mythtv -p mythconverg
SELECT * FROM settings WHERE value LIKE '%Server%';
```

You should get something like
```
+-------------------+--------------------+----------+
| value             | data               | hostname |
+-------------------+--------------------+----------+
| BackendServerIP   | 127.0.0.1          | apollon  |
| BackendServerPort | 6543               | apollon  |
| MasterServerIP    | 127.0.0.1          | NULL     |
| MasterServerPort  | 6543               | NULL     |
| ServerHaltCommand | sudo /sbin/halt -p | NULL     |
+-------------------+--------------------+----------+
5 rows in set (0.00 sec)
```

If your results differ, try setting them to the values I posted (aside the hostname of course ;) ). Here an example with the BackendServerPort
```
UPDATE settings SET data='6543' WHERE value='BackendServerPort';
```

---

### Post by callagga on 2008-04-28
this is what I see:

```
mysql> SELECT * FROM settings WHERE value LIKE '%Server%';
+----------------------------------------------------+--------------------------------------+-------------+
| value                                              | data                                 | hostname    |
+----------------------------------------------------+--------------------------------------+-------------+
| BackendServerIP                                    | 127.0.0.1                            | OLDHOSTNAME |
| BackendServerPort                                  | 6543                                 | OLDHOSTNAME |
| MasterServerIP                                     | 127.0.0.1                            | NULL        |
| MasterServerPort                                   | 6543                                 | NULL        |
| ServerHaltCommand                                  | sudo /sbin/halt -p                   | NULL        |
| upnp:UDN:urn:schemas-upnp-org:device:MediaServer:1 | 256a89b4-1266-49ca-9ac7-f0b4b4641e7f | OLDHOSTNAME |
| BackendServerIP                                    | 127.0.0.1                            | mythtv      |
| BackendServerPort                                  | 43                                   | mythtv      |
| UPnP/UDN/MediaServer                               | d349e384-9538-4167-889c-1fda22de1382 | mythtv      |
| UPnP/UDN/MasterMediaServer                         | 22fdaaa9-f78d-4990-b836-47f98202dcf5 | mythtv      |
+----------------------------------------------------+--------------------------------------+-------------+

```

I seem to have two (2) Backendserver port entries?  I assume I should remove the non-"mythtv" hostname entries?

---

### Post by callagga on 2008-04-29
> **justanotherhack said:**
> If your results differ, try setting them to the values I posted (aside the hostname of course ;) ). Here an example with the BackendServerPort
```
UPDATE settings SET data='6543' WHERE value='BackendServerPort';
```Tried this and get a better start-up log.  Does this look normal now?  (will test tonight when I'm home)

```
greg@mythtv:/usr/bin$
greg@mythtv:/usr/bin$ mythbackend
2008-04-29 16:13:11.151 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-29 16:13:11.152 Empty LocalHostName.
2008-04-29 16:13:11.152 Using localhost value of mythtv
2008-04-29 16:13:11.166 New DB connection, total: 1
2008-04-29 16:13:11.171 Connected to database 'mythconverg' at host: 127.0.0.1
2008-04-29 16:13:11.173 Closing DB connection named 'DBManager0'
2008-04-29 16:13:11.173 Connected to database 'mythconverg' at host: 127.0.0.1
2008-04-29 16:13:11.175 New DB connection, total: 2
2008-04-29 16:13:11.176 Connected to database 'mythconverg' at host: 127.0.0.1
2008-04-29 16:13:11.178 Current Schema Version: 1214
Starting up as the master server.
2008-04-29 16:13:11.186 New DB connection, total: 3
2008-04-29 16:13:11.187 Connected to database 'mythconverg' at host: 127.0.0.1
2008-04-29 16:13:11.197 DVBChan(1:0) Warning: Unsupported constellation parameter.
2008-04-29 16:13:11.508 New DB scheduler connection
2008-04-29 16:13:11.509 Connected to database 'mythconverg' at host: 127.0.0.1
 is defined, but isn't attached to a cardinput.
2008-04-29 16:13:11.521 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-04-29 16:13:11.521 Main::Registering HttpStatus Extension
2008-04-29 16:13:11.521 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-04-29 16:13:11.521 Enabled verbose msgs:  important general
2008-04-29 16:13:11.522 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-04-29 16:13:14.520 Reschedule requested for id -1.
2008-04-29 16:13:14.542 Scheduled 0 items in 0.0 = 0.00 match + 0.02 place
2008-04-29 16:13:14.545 Seem to be woken up by USER
2008-04-29 16:14:31.513 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

```

---

### Post by justanotherhack on 2008-04-29
Looks way better now. One can almost assume it'll work now ;) .

The entries with the other hostname don't need to concern you. MythTV selects the correct entries through the hostname, so it will only use those which have your current hostname.
But this might interest you, if you ever decide to change the hostname of your MythTV box. As soon as you restart, most of your settings will be gone. Gone, but not lost, since they are stored under a different hostname. Problem is, that many tables in the database are using a hostname to identify the entries. So you would have to shutdown all of MythTV and
```
DELETE FROM tablename WHERE hostname='newhostname';
UPDATE tablename SET hostname='newhostname' WHERE hostname='oldhostname';
```
on many tables.
After restart all settings should be like before. You prolly don't need that now, but I thought I should point it out, in case you miss some settings from your old configuration.

Of course you can just delete them old settings, if you want your DB to stay slim.
```
DELETE FROM settings WHERE hostname='oldhostname';
```
That should do the trick, but beware, that there might be entries in other tables as well, you might want to check out. But to repeat it: Those should be no concern to you and won't disturb your machine. And the database is strong and fast enough to handle that.

---

### Post by callagga on 2008-04-29
thanks - seems to have solved the problem

Unfortunately I'm seeing another, which I've posted separately at [http://ubuntuforums.org/showthread.php?t=774591]("http://ubuntuforums.org/showthread.php?t=774591")

---

### Post by ozybushwalker on 2008-05-07
I installed Mythbuntu 8.04 doing an advanced configuration, primary back end only.

The back end log file read (in part):

```
2008-05-07 19:36:15.272 Using runtime prefix = /usr, libdir = /usr/lib
2008-05-07 19:36:15.328 Empty LocalHostName.
2008-05-07 19:36:15.329 Using localhost value of kubuntu
QSettings::sync: filename is null/empty
2008-05-07 19:36:15.406 New DB connection, total: 1
2008-05-07 19:36:15.460 Connected to database 'mythconverg' at host: localhost
2008-05-07 19:36:15.465 Closing DB connection named 'DBManager0'
2008-05-07 19:36:15.468 Connected to database 'mythconverg' at host: localhost
QSettings::sync: filename is null/empty
2008-05-07 19:36:15.505 New DB connection, total: 2
2008-05-07 19:36:15.508 Connected to database 'mythconverg' at host: localhost
2008-05-07 19:36:15.516 Current Schema Version: 1214
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.

```

I found this thread which seems to match the problem. I queried the database:

```
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 51
Server version: 5.0.51a-3ubuntu5 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> select * from settings where value like '%server%';
+----------------------------------------------------+--------------------------------------+-------------+
| value                                              | data                                 | hostname    |
+----------------------------------------------------+--------------------------------------+-------------+
| BackendServerIP                                    | 127.0.0.1                            | OLDHOSTNAME |
| BackendServerPort                                  | 6543                                 | OLDHOSTNAME |
| MasterServerIP                                     | 127.0.0.1                            | NULL        |
| MasterServerPort                                   | 6543                                 | NULL        |
| ServerHaltCommand                                  | sudo /sbin/halt -p                   | NULL        |
| upnp:UDN:urn:schemas-upnp-org:device:MediaServer:1 | 256a89b4-1266-49ca-9ac7-f0b4b4641e7f | OLDHOSTNAME |
| BackendServerIP                                    | 127.0.0.1                            | OLDHOSTNAME |
| BackendServerPort                                  | 6543                                 | OLDHOSTNAME |
+----------------------------------------------------+--------------------------------------+-------------+
8 rows in set (0.00 sec)

mysql>

```

I didn't set the system hostname to OLDHOSTNAME - this is apparently a fabrication of the Mythbuntu install which seemed to ignore the hostname I specified in the install dialogue. What commands do I need to give to fix this? (Do I need to change BOTH BackendServerIP entries? Only one? Which one?)

---

