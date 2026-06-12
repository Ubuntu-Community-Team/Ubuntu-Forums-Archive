---
title: "mythbackend port problems 6543 vs 3306 edgy"
date: 2007-03-21
forum: Multimedia &amp; Video
---

### Post by Panhead Bill on 2007-03-21
Since I foolishly upgraded some packages a few weeks back my myth box has been Uber hosed.

I'm trying to troubleshoot the system as I don't want to lose the recordings (Yes, I'm stubborn so far).

Among the problems is a disconnect with the backend.  If I set the ports (in mythtv-setup, general) to 6543, 6544, and 6543 (the default). I get an empty database - no recordings.  I tried to check out the database using MySQL Administrator, logging into server hostname "localhost", port 6543, user "mythtv", and the password I set.

 The startup parameters for mysqld_safe has a networking box with 3306 listed as the tcp port.  The settings are greyed out so I can't change them.

I checked /etc/mysql/my.cnf and it lists port 6543.  

Just to add to my grey hair I tried to change the backend port to 3306, then the master backend port to 3306, and finally both of them to 3306.  Protocol errors ensue when starting mythfrontend.

I tried to add phpmyadmin so that I could try to check the database, but after setting the password, it won't allow me to logon.


Any clues to what's going on?

---

