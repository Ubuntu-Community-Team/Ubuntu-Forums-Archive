---
title: "failed installation on 64 bit system"
date: 2009-06-07
forum: Mythbuntu
---

### Post by iopo on 2009-06-07
Hi everybody, when installing the package "mythtv" or "mythbuntu-desktop" I get the following errors:

 Stopping MySQL database server mysqld                                                                                                             [ OK ] 
 * Reloading AppArmor profiles ...                                                                                                                   [ OK ] 
 * /etc/init.d/mysql: WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.gz                                                                       
 * Starting MySQL database server mysqld                                                                                                             [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.                       

and later:

Setting up mythtv-database (0.21.0+fixes19961-0ubuntu8) ...                                                                                                 
 * /etc/init.d/mysql: WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.gz                                                                       
 * Starting MySQL database server mysqld                                                                                                             [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.                                                                                     
Failed to create or modify database (incorrect admin username/password?)            


then when I run mythtv-setup it complains that it cannot connect to the database. Any suggestions?
Thanks!

---

### Post by crez79 on 2009-06-07
I would try to install mythbuntu-control-centre and use that to install and configure your install. That is how I installed my systems. It makes sure all the dependencies are met and everything is setup with the default settings. If nothing else, it gives you a standard starting point.

---

### Post by iopo on 2009-06-08
Thanks for the reply but it didn't work. I cannot run mythtv-configure since it always says that it cannot connect to the database. I guess my mysql installation is messed up.

---

### Post by crez79 on 2009-06-08
Did you try to install once before, because apparently there is a [bug]("https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.0/+bug/306002").  Maybe [this]("http://www.jemmatzan.com/2009/02/the-default-ubuntu-mycnf-for-mysql-50x.html") will help? :-k

---

### Post by iopo on 2009-06-09
Yes!!!! That is the problem! Thanks a lot: now I can start experimenting with mythtv!

---

### Post by crez79 on 2009-06-09
Good. :D You might consider commenting on the bug page about your situation to see if the problem can be fixed.

---

