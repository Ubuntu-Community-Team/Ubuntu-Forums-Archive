---
title: "Mythbuntu: could not connect to master backend"
date: 2014-06-13
forum: Mythbuntu
---

### Post by linuxhippy on 2014-06-13
Hi!  I've been using mythbuntu for years with few problems.  I am running mythbuntu 12.04.4.  The other day my system suddenly froze while I was watching TV.  I went to a virtual terminal and got it to reboot with CTRL-ALT-Delete.  Now when it starts the mythfrontend, I get this error message:

Could not connect to the master backend server.  Is it running?  Is the IP address set for it in mythtv-setup correct?

***********************************************************************************

This is a single pc running both the frontend and the backend so the IP should be localhost??  How can I fix this?

---

### Post by blm-ubunet on 2014-06-13
From a terminal (not console) run:
```
mythtv-setup
```
What is the IP address shown for BE.

AFAIK from reading here:
[http://irc.mythtv.org/ircLog/channel/4/2014-06-07](http://irc.mythtv.org/ircLog/channel/4/2014-06-07)
(Maybe) the label/keyword localhost is not valid (anymore)..should be 127.0.0.1 for localhost

```
sudo service mythtv-backend status
sudo service mysql status
```

Could have corrupted config.xml file.
Could have mysql dB table problems.

Make a dB backup with mythtv script mythconverg_backup.
[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)
There are a couple of dBase check/repair scripts that ship with mythtv..could be idea to run them **after **making a backup.
[http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance](http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance)

---

### Post by linuxhippy on 2014-06-13
Got it fixed.  A while ago when I set up mythtv, I had defined the IP address as the static address my router gives.  Well, I recently had router problems and had to reset it and all the static IPs were erased.  All I had to do was setup my router to give that original IP to mythtv and then reboot the mythtv pc.  Now it gets that IP and is happy...then I finished watching 24 :)

---

### Post by blm-ubunet on 2014-06-14
That's an ugly problem when the router dies or has to reboot..

A more robust solution could be:
- set MBE to static IP.
- setup router to allocate addresses in a fixed IP range (excluding MBE IP)
- can put MBE IP into router as static assignment identified by MAC.

wifi security:
- use MAC access lists to allow connection (& IP)

---

