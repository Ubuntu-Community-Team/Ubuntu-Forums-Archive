---
title: "Upgrade ffrom 0.23.0 to 0.23.1 on Ubuntu (not MYTHbuntu) install?"
date: 2010-10-01
forum: Mythbuntu
---

### Post by yonkiman on 2010-10-01
My main Mythbox runs MythBuntu 9.10 / 0.23.1.  On a different PC in the house I'm running Ubuntu (not Mythbuntu) 10.04, and have installed MythTV frontend 0.23.0 (or maybe even 0.22) from the standard 10.04 PPA.

The last time I tried it (many months ago) the 10.04 frontend happily connected to the mythbuntu backend and played video.  Today when I launch the frontend it tells me "the server uses protocol version 23056, but this client only understands version 56...", so I gather I need to upgrade my mythTV frontend.

But I can't find a way to do that.  On my server, I've enabled 0.23.1 autobuilds.  But I don't know how to get the 0.23.1 frontend installed at all (let alone the fastest way, which is my goal since I've got a kid that needs to see his baseball game).

Any advice?

---

### Post by tgm4883 on 2010-10-01
Install the mythbuntu auto-builds package on your frontend and select 0.23.1.

---

### Post by yonkiman on 2010-10-02
> **tgm4883 said:**
> Install the mythbuntu auto-builds package on your frontend and select 0.23.1.

Thanks - I didn't know you could use mythbuntu auto-builds on a non-mythbuntu system.

Took me a while to find a working repo, but finally did here: [http://www.ubuntuupdates.org/ppa/mythtv_0.23.1?dist=lucid](http://www.ubuntuupdates.org/ppa/mythtv_0.23.1?dist=lucid)

Worked great!

---

### Post by tgm4883 on 2010-10-02
> **yonkiman said:**
> Thanks - I didn't know you could use mythbuntu auto-builds on a non-mythbuntu system.

Took me a while to find a working repo, but finally did here: [http://www.ubuntuupdates.org/ppa/mythtv_0.23.1?dist=lucid](http://www.ubuntuupdates.org/ppa/mythtv_0.23.1?dist=lucid)

Worked great!

Not sure I understand. Why did it take you a while to find a working repo? What was the issue?

---

### Post by SnoopFogg on 2010-12-22
I'm trying to set up a front end but receiving error message "The server uses network protocol version 23056, but this client only understands version 56".  Both use ubuntu 10.10.  The back end I'm connecting to is v23.1 and the frontend v23.0.  I think I've enabled autobuilds, but they are not at the same build.  

How do I upgrade the FE to 23.1?  Tried the instruction above [http://www.ubuntuupdates.org/ppa/mythtv_0.23.1?dist=maverick#](http://www.ubuntuupdates.org/ppa/mythtv_0.23.1?dist=maverick#)

Which say to:
sudo add-apt-repository ppa:mythbuntu/0.23.1 
sudo apt-get update
sudo apt-get install <package name>

(where <package name> is one of the packages below). But getting an error message "Couldn't find package 0.23.1+fixes26863-0ubuntu0+mythbuntu3"  Is this the right package name?  Do I need to enable something else?

Any help much appreciated.

---

### Post by SnoopFogg on 2010-12-22
Found how to upgrade to 23.1 - sudo dpkg-reconfigure mythbuntu-repos 

No longer get an error message about the network protocol version but unable to watch live TV.  Also I can see recordings in the menu from the BE but unable to watch those either.  It looks as though it is about to start then goes back to the menu.

---

### Post by newlinux on 2010-12-22
> **SnoopFogg said:**
> Found how to upgrade to 23.1 - sudo dpkg-reconfigure mythbuntu-repos 

No longer get an error message about the network protocol version but unable to watch live TV.  Also I can see recordings in the menu from the BE but unable to watch those either.  It looks as though it is about to start then goes back to the menu.

what do your frontend logs say when you try to view a recording?

---

### Post by tgm4883 on 2010-12-22
> **newlinux said:**
> what do your frontend logs say when you try to view a recording?

Backend logs.

---

### Post by t4thfavor on 2010-12-22
Same problem that I had when I did the install, I had to make sure that the backend. and frontend were running the same version of ubuntu even with the mythbuntu-repos installed, and configured the same.

Other than that, I had to read the logs a lot. Post them, and I am sure someone will be able to point you in the correct direction.

---

### Post by SnoopFogg on 2010-12-23
Hi, not sure if I needed to start a new tread.  This is the results of the backend logs when I tried to first watch TV and then watch previously recorded programmes on the front end on another machine.  Any ideas why it looks as though it's going to start playing, then stops?

russ@russ-desktop:~$ more /var/log/mythtv/mythbackend.log

> 2010-12-23 18:58:44.127 mythbackend version: branches/release-0-23-fixes [26863]
 [www.mythtv.org](www.mythtv.org)
2010-12-23 18:58:44.127 Using runtime prefix = /usr
2010-12-23 18:58:44.127 Using configuration directory = /home/mythtv/.mythtv
2010-12-23 18:58:44.257 Empty LocalHostName.
2010-12-23 18:58:44.258 Using localhost value of russ-desktop
2010-12-23 18:58:44.273 New DB connection, total: 1
2010-12-23 18:58:44.274 Unable to connect to database!
2010-12-23 18:58:44.274 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock'
 (2)

2010-12-23 18:58:44.276 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-12-23 18:58:44.276 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
SSDP::PerformSearch - did not write entire buffer.
SSDP::PerformSearch - did not write entire buffer.2010-12-23 18:58:44.381 QMulti
castSocket: setsockopt - IP_ADD_MEMBERSHIP Error

................................................................................
2010-12-23 18:58:46.595 UPnPautoconf() - No UPnP backends found
2010-12-23 18:58:46.595 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-12-23 18:58:46.600 Deleting UPnP client...
2010-12-23 18:58:46.600 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-12-23 18:58:47.355 Failed to init MythContext, exiting.
2010-12-23 18:58:47.515 mythbackend version: branches/release-0-23-fixes [26863]
 [www.mythtv.org](www.mythtv.org)
2010-12-23 18:58:47.515 Using runtime prefix = /usr
2010-12-23 18:58:47.523 Using configuration directory = /home/mythtv/.mythtv
2010-12-23 18:58:47.527 Empty LocalHostName.
2010-12-23 18:58:47.531 Using localhost value of russ-desktop
2010-12-23 18:58:47.561 New DB connection, total: 1
2010-12-23 18:58:47.577 Connected to database 'mythconverg' at host: localhost
2010-12-23 18:58:47.578 Closing DB connection named 'DBManager0'
2010-12-23 18:58:47.581 Connected to database 'mythconverg' at host: localhost
2010-12-23 18:58:47.594 Using protocol version 23056
2010-12-23 18:58:47.706 Backend is running in Europe/London time zone.
2010-12-23 18:58:47.709 Current MythTV Schema Version (DBSchemaVer): 1254
2010-12-23 18:58:47.711 MythBackend: Running as a slave backend.
2010-12-23 18:58:47.723 MythBackend, Error: No valid capture cards are defined i
n the database.
			Perhaps you should re-read the installation instructions
?
2010-12-23 18:58:47.728 New DB connection, total: 2
2010-12-23 18:58:47.729 New DB connection, total: 3
2010-12-23 18:58:47.730 Connected to database 'mythconverg' at host: localhost
2010-12-23 18:58:47.730 Connected to database 'mythconverg' at host: localhost
2010-12-23 18:58:47.748 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-12-23 18:58:47.749 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-12-23 18:58:49.173 Main::Registering HttpStatus Extension
2010-12-23 18:58:49.173 Enabled verbose msgs:  important general
2010-12-23 18:58:50.177 Connecting to master server: 192.168.0.12:6543
2010-12-23 18:58:50.177 Connected successfully


By the way, is there a quick way to get to the end of this report?  (It took five minutes of holding down the space bar)

---

### Post by t4thfavor on 2010-12-23
Cannot connect to the MySQL server would be a good place to start. Make sure that your .mythtv config files point to the correct server.

---

### Post by SnoopFogg on 2010-12-23
Thanks for that, but I'm a bit out of my depth.  Is that part of the front end configuration settings?

---

### Post by t4thfavor on 2010-12-23
```
2010-12-23 18:58:47.723 MythBackend, Error: No valid capture cards are defined i
n the database.
Perhaps you should re-read the installation instructions
?
```

That is also another hint, you need to run mythtv-setup on your backend, and define somekind of tv capture card so that the backend has something to stream to the frontends.

If you don't have a capture card, I have heard good things about the HDHomeRun from SiliconDust.

I may not check this very often, but since I subscribed to the thread, I will post back if you have anymore questions.

---

### Post by tgm4883 on 2010-12-26
In 0.24 you can put in a dummy tuner.

For getting the end of the logs, use tail

---

