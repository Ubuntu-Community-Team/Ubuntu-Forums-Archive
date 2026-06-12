---
title: "Mythbuntu 9.10 MySQL won't autostart"
date: 2010-01-07
forum: Mythbuntu
---

### Post by daviding on 2010-01-07
After a power hit, I was having problems with Mythbuntu 8.10 booting up (a NTP problem). As a final alternative, I updated all of software, upgraded to 9.04 and then to 9.10 .  

I've figured out that I've been getting the uPnP error from mythfrontend ... because mythbackend hasn't started ... because mysql hasn't started.  

I found that mysqld and mythbackend were missing (although mythfrontend was there) in Applications ... Settings ... Session and Startup ... Application Autostart ... so I added them.  After some reboots, these seem to appear in the right order (i.e. mysql first, then mythbackend and then mythfrontend).  

The autostart of mysql and mythbackend don't work, though.  Manually trying to start mythbackend results in the "Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock'" message.  In addition, manually starting mysqld doesn't work.  

On an [April 2007 message]("http://ubuntuforums.org/showthread.php?t=276470&page=2"), I found that I can start mysqld with the following commands:

```
sudo mkdir /var/run/mysqld/  
sudo touch /var/run/mysqld/mysqld.sock  
sudo chown mysql /var/run/mysqld/  
sudo chown mysql /var/run/mysqld/mysqld.sock  
sudo mysqld
```

In another terminal window, I can then start mythbackend, and everything works fine.  

However, as soon as I reboot, the mysqld.sock disappears. I then have to recreate the mysqld.sock . 

Can someone please make a suggestion as to how to resolve this?

---

### Post by azmyth on 2010-01-08
I'd look in your syslog file to see if it gives you any hints. I just went through the same thing last night as I messed up my system with autoremove and I found out it blew away mysql-server-5.1.

---

### Post by daviding on 2010-01-09
> **azmyth said:**
> I'd look in your syslog file to see if it gives you any hints.
Thanks for the suggestion.  I rebooted Mythbuntu, copied /var/log/syslog, edited the file down to after the reboot, and have saved the syslog to a temporary location on my web site at [http://daviding.com/txt/20100109_syslog.txt]("http://daviding.com/txt/20100109_syslog.txt") .

I've never looked at syslog before.  These look mostly like bootup recognition of hardware.  Everything looks fine, except for at the end with a NetworkManager "Unmanaged Device found", but since I'm typing this response from the machine via Firefox, I have access to the Internet.

> **azmyth said:**
> I just went through the same thing last night as I messed up my system with autoremove and I found out it blew away mysql-server-5.1.

I'm not have a problem with MySQL in the respect that I can start it manually.  After I execute ...
```
sudo mkdir /var/run/mysqld/  
sudo touch /var/run/mysqld/mysqld.sock  
sudo chown mysql /var/run/mysqld/  
sudo chown mysql /var/run/mysqld/mysqld.sock  
sudo mysqld
```... I get the response
```
100109 11:21:39 [Note] Plugin 'FEDERATED' is disabled.
100109 11:21:39  InnoDB: Started; log sequence number 0 91410
100109 11:21:39 [Note] Event Scheduler: Loaded 0 events
100109 11:21:39 [Note] mysqld: ready for connections.
Version: '5.1.37-1ubuntu5'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
```

In another terminal window, I then execute ...
```
mythbackend
``` ... to get the response ...
```
2010-01-09 11:24:08.560 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2010-01-09 11:24:08.560 Using runtime prefix = /usr
2010-01-09 11:24:08.560 Using configuration directory = /home/daviding/.mythtv
2010-01-09 11:24:08.560 Empty LocalHostName.
2010-01-09 11:24:08.561 Using localhost value of mythbuntu
2010-01-09 11:24:08.565 New DB connection, total: 1
2010-01-09 11:24:08.669 Connected to database 'mythconverg' at host: localhost
2010-01-09 11:24:08.669 Closing DB connection named 'DBManager0'
2010-01-09 11:24:08.670 Connected to database 'mythconverg' at host: localhost
2010-01-09 11:24:08.764 Current MythTV Schema Version (DBSchemaVer): 1244
2010-01-09 11:24:08.765 MythBackend: Starting up as the master server.
2010-01-09 11:24:08.880 New DB connection, total: 2
2010-01-09 11:24:08.881 Connected to database 'mythconverg' at host: localhost
2010-01-09 11:24:08.962 New DB connection, total: 3
2010-01-09 11:24:08.962 Connected to database 'mythconverg' at host: localhost
2010-01-09 11:24:09.125 New DB scheduler connection
2010-01-09 11:24:09.126 Connected to database 'mythconverg' at host: localhost
2010-01-09 11:24:09.262 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2010-01-09 11:24:09.262 Main::Registering HttpStatus Extension
2010-01-09 11:24:09.262 Enabled verbose msgs:  important general
2010-01-09 11:24:09.265 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
```
I can then surf to Applications ... Multimedia ... MythTv Front End, and everything works fine.  

I really shouldn't have to do all of this manually, though.  If I get another power hit when I'm not home -- I'm on the road with business travel quite often -- these procedures are more than wife could execute.  

Thus, I'm missing some configuration that happens in a native installation (since I upgraded from 8.10 to 9.04 to 9.10) that autostarts MySQL and mythbackend.  I have mysqld and mythbackend listed in Applications  ... Settings ... Application Autostart ... but that doesn't seem to be working for me.  

The note on Application Autostart says "applications that will be started automatically when you login to your Xfce desktop".  I think that mysqld and mythbackend should be started with the bootup even before logging in, and I don't know how to do that.  Can someone point me in the right direction?

---

### Post by daviding on 2010-01-09
I can't get mythweb to start, either.  In Firefox, surfing to [http://127.0.0.1](http://127.0.0.1) gives an "Unable to Connect".  I assume that apache2 isn't running.

---

### Post by Illydth on 2010-01-10
This seems to be a not so uncommon problem. 

I upgraded to 9.10 about a week and a half ago and ran into the exact same problem, I assumed it was because my mythexport package wouldn't upgrade correctly...seems maybe not.

I did some research and found that, basically, the answer is uninstall and re-install mysql...and yea, this'll include reinstalling mythtv as well.

I haven't run into the "this is why" post yet, but the "this is how to fix it" seems to be:

* BACK UP YOUR DATABASE!  I recommend making a tar.gz of /var/lib/mysql in it's entirety as well as exporting your myth database.
* Uninstall mysql-server - This will remove everything associated with MySQL as well which includes, at least, MythTV.  I actually removed ALL of mysql, not just the server portion (client, common, etc.)
* Reinstall MySQL-Server (or all of it if you uninstalled everything).  
* Reinstall all of the packages that got removed with MySQL including MythTV.  Note that just re-installing MythTV didn't seem to re-install all of the "extras" (like mythweb, mythvideo, etc.) so I had to install those manually also.

However, the good news, is that once you've re-installed MySQL and gone through the process of "putting back" the database (I think I just copied the backup /var/lib/mysql back but don't quote me on that...it's been almost 2 weeks now and it was REALLY late when I did this the first time) it all works perfectly.

--Illydth

---

### Post by daviding on 2010-01-16
> **Illydth said:**
> I did some research and found that, basically, the answer is uninstall and re-install mysql...and yea, this'll include reinstalling mythtv as well.

I was encouraged by your experience, and thus tried it myself.  I have to say that my results weren't as favourable as yours. 

I uninstalled MySQL, and as much of MythTv as I could.  (Actually, my first attempt didn't seem to have an impact, so it took a second pass to try to remove more).  

The result was that when I rebooted the system, I didn't get the usual XFCE UI and menu.  I got a small terminal window.  Searching the forums, I managed to find the manual apt-get commands to reinstall MySQL and MythTv.  I still wasn't successful in getting an XFCE UI working, so I found another text command ... which leapt me into an upgrade from 9.10 into the 10.4 alpha.  (Have you ever had one of those cases when you've thought about whether pulling the plug would put you into a better or worse situation?)  This OS upgrade did give an XFCE UI, but other things still didn't work (e.g. no Mythweb).  I was trying to fix a boot-up error on "Plymouth", and managed to get into a situation where the system halts ... long before any GUI or terminal window appears.  

The logical direction was then to try a reinstallation from a Mythbuntu CD ... or a USB drive.  This did not work.  I previously had this IDE drive in a Netvista (which finally died), and transferred it into a new computer built around an Asus M3N78 Pro motherboard.  This worked fine 10 months ago, so I've never had to install Mythbuntu on this computer from a CDROM.  Now, when I've inserted a CDROM and/or USB onto the computer, both light up, but the boot always returns to the hard disk as if the CDROM and USB drive didn't exist. 

I've now taken the hardware into the dealer who assembled the whole computer.  I had reconfigured the boot devices in the BIOS, and even flashed the BIOS to the most current level.  I've played around with jumpers on the hard disk and CDROM drive without success, so it's either something in the BIOS or we're down to the level of hardware configurations.  This isn't where I expect to be, when I was started fixing Mythbuntu bootup problem.

---

