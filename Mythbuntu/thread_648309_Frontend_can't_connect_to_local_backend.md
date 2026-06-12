---
title: "Frontend can't connect to local backend"
date: 2007-12-23
forum: Mythbuntu
---

### Post by erland on 2007-12-23
I just installed Mythbuntu with a backend+frontend on the same machine. I now have problem that the frontend can't connect to the local backend. 

Is there some way I can debug what is happening ?

The backend log just says:
```

2007-12-23 18:39:18.748 Using runtime prefix = /usr
2007-12-23 18:39:18.773 New DB connection, total: 1
2007-12-23 18:39:18.778 Connected to database 'mythconverg' at host: 172.16.0.114
2007-12-23 18:39:18.781 Current Schema Version: 1160
Starting up as the master server.
2007-12-23 18:39:18.791 New DB connection, total: 2
2007-12-23 18:39:18.792 Connected to database 'mythconverg' at host: 172.16.0.114
2007-12-23 18:39:18.794 New DB connection, total: 3
2007-12-23 18:39:18.795 Connected to database 'mythconverg' at host: 172.16.0.114
2007-12-23 18:39:18.802 EITHelper: localtime offset 1:00:00 
2007-12-23 18:39:19.041 DVBTuning Warning: Invalid inversion, aborting, falling back to 'auto'
2007-12-23 18:39:19.560 EITHelper: localtime offset 1:00:00 
CAM: Viaccess, 01, 0500, 0500

```

And the frontend log:
```

Starting mythfrontend.real..
2007-12-23 18:35:50.467 Current Schema Version: 1160
2007-12-23 18:35:50.468 mythfrontend version: 0.20.20070821-1 www.mythtv.org
2007-12-23 18:35:50.468 Enabled verbose msgs:  important general
2007-12-23 18:35:50.988 Connecting to lcd server: localhost:6545 (try 1 of 10)
2007-12-23 18:35:51.230 Total desktop dim: 800x600, with 2 screen[s].
2007-12-23 18:35:51.231 Using screen 0, 800x600 at 0,0
2007-12-23 18:35:51.232 Switching to square mode (Mythbuntu)
2007-12-23 18:35:51.242 Using the Qt painter
2007-12-23 18:35:51.350 Joystick disabled.
2007-12-23 18:35:51.393 Loading from: /usr/share/mythtv/themes/Mythbuntu/base.xml
2007-12-23 18:35:51.405 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-12-23 18:35:51.435 Registering Internal as a media playback plugin.
2007-12-23 18:35:51.462 Registering MythDVD DVD Media Handler as a media handler ext()
2007-12-23 18:35:51.462 Registering MythDVD VCD Media Handler as a media handler ext()
2007-12-23 18:35:51.480 Registering MythGallery Media Handler 1/2 as a media handler ext()
2007-12-23 18:35:51.480 Registering MythGallery Media Handler 2/2 as a media handler ext(gif,jpg,png)
Failed to run 'cdrecord --scanbus'
Failed to run 'cdrecord --scanbus'
Failed to run 'cdrecord --scanbus'
2007-12-23 18:35:51.542 Registering MythMusic Media Handler 1/2 as a media handler ext()
2007-12-23 18:35:51.543 Registering MythMusic Media Handler 2/2 as a media handler ext(ogg,mp3,aac,flac)
2007-12-23 18:35:51.581 New DB connection, total: 2
2007-12-23 18:35:51.582 Connected to database 'mythconverg' at host: localhost
SIP listening on IP Address 172.16.0.114:5060 NAT address 172.16.0.114
SIP: Cannot register; proxy, username or password not set
2007-12-23 18:35:54.174 Connecting to backend server: 172.16.0.114:6543 (try 1 of 5)
2007-12-23 18:35:54.177 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.

```

I tried to connect with telne but that didn't work, it just says:
```

telnet localhost 6543
Trying 127.0.0.1
telnet: Unable to connect to remote host: Connection refused

```

I also tried connect to mysql and that seems to work.
Both IP addresses in the mythtv-setup is configued to 172.16.0.114 (which is the same address as eth0 returns in ifconfig.

Does anyone have any clue what's going on and how to debug the problem ?

---

### Post by erland on 2007-12-23
Running nmap shows:
```

Starting Nmap 4.20 ( http://insecure.org ) at 2007-12-23 18:53 CET
Interesting ports on 172.16.0.114:
Not shown: 1692 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
3306/tcp open  mysql

Nmap finished: 1 IP address (1 host up) scanned in 0.456 seconds

```

And ps gives:
```

ps `cat /var/run/mythtv/mythbackend.pid`
  PID TTY      STAT   TIME COMMAND
 7342 ?        Ssl    0:00 /usr/bin/mythbackend --daemon --logfile /var/log/mythtv/mythbackend.log --pidfile /var/run/mythtv/mythbackend.pid

```

---

### Post by volkswagner on 2007-12-24
I am having difficulty fully understanding these directions.

[http://www.mythtv.org/wiki/index.php/User_Manual:Detailed_configuration_Backend#Backend_Configuration]("http://www.mythtv.org/wiki/index.php/User_Manual:Detailed_configuration_Backend#Backend_Configuration")

I am fairly certain you should use 127.0.0.1 for the ip address of the master server and location of mysql database when running mythtv-setup.  If you make these changes a restart may be in order.

You should also verify mythtv user can access mysql database with its password.

```
mysql -u mythtv -p
```

enter your password and you should get a mysql prompt if not your password may be incorrect.

---

### Post by erland on 2007-12-24
> **volkswagner said:**
> 
I am fairly certain you should use 127.0.0.1 for the ip address of the master server and location of mysql database when running mythtv-setup.  If you make these changes a restart may be in order.

I need to have the real IP address, because there is also a remote frontend that is later going to connect to the same backend.

It works sometimes, so I think something happens that causes the server to start incorrectly, however I can't see anything strange in the mythbackend.log file.  When the backend starts correctly it works to connect both local and remote frontend.

Is there something that could cause the backend to hang at startup ?

> **volkswagner said:**
> 
You should also verify mythtv user can access mysql database with its password.

```
mysql -u mythtv -p
```

enter your password and you should get a mysql prompt if not your password may be incorrect.
I've check this and it always seems to work.

---

