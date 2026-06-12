---
title: "Mythtv mysql won't connect from remote computer"
date: 2009-02-19
forum: Mythbuntu
---

### Post by sickgemini on 2009-02-19
Hi all,

Hope someone can help out with this as it's beginning to drive me nuts!

I'm totally new to ubuntu and mythtv.

I've installed mythbuntu on a PC and everything seems to be working ok. The frontend runs ok and I can record and watch programs no worries.

Now I want to run the front end on a MacBook Pro. I've installed one of the mythtv frontend packages available for MAC. However when I run the app, I can input the backend parameters and click finish but it just says it cannot log into the database. I get the following error in the MAC console:

```


19/02/09 9:11:41 PM [0x0-0x2ce2ce].org.osx-bundler.MythFrontend[4431] 2009-02-19 21:11:41.368 Testing network connectivity to 10.1.1.2 
19/02/09 9:11:41 PM [0x0-0x2ce2ce].org.osx-bundler.MythFrontend[4431] 2009-02-19 21:11:41.430 Unable to connect to database! 
19/02/09 9:11:41 PM [0x0-0x2ce2ce].org.osx-bundler.MythFrontend[4431] 2009-02-19 21:11:41.430 Driver error was [1/1045]: 
19/02/09 9:11:41 PM [0x0-0x2ce2ce].org.osx-bundler.MythFrontend[4431] QMYSQL3: Unable to connect 
19/02/09 9:11:41 PM [0x0-0x2ce2ce].org.osx-bundler.MythFrontend[4431] Database error was: 
19/02/09 9:11:41 PM [0x0-0x2ce2ce].org.osx-bundler.MythFrontend[4431] Access denied for user 'mythtv'@'10.1.1.4' (using password: YES) 
19/02/09 9:11:41 PM [0x0-0x2ce2ce].org.osx-bundler.MythFrontend[4431] QSqlQuery::exec: database not open 
19/02/09 9:11:41 PM [0x0-0x2ce2ce].org.osx-bundler.MythFrontend[4431] QSqlQuery::exec: database not open 
19/02/09 9:11:41 PM [0x0-0x2ce2ce].org.osx-bundler.MythFrontend[4431] 2009-02-19 21:11:41.533 DB Error (KickDatabase): 
19/02/09 9:11:41 PM [0x0-0x2ce2ce].org.osx-bundler.MythFrontend[4431] Query was: 
19/02/09 9:11:41 PM [0x0-0x2ce2ce].org.osx-bundler.MythFrontend[4431] SELECT NULL; 
19/02/09 9:11:41 PM [0x0-0x2ce2ce].org.osx-bundler.MythFrontend[4431] No error type from QSqlError?  Strange... 
19/02/09 9:11:41 PM [0x0-0x2ce2ce].org.osx-bundler.MythFrontend[4431] 2009-02-19 21:11:41.583 Cannot login to database? 
19/02/09 9:11:41 PM [0x0-0x2ce2ce].org.osx-bundler.MythFrontend[4431] 2009-02-19 21:11:41.583 Cannot login to database? 
19/02/09 9:11:41 PM [0x0-0x2ce2ce].org.osx-bundler.MythFrontend[4431] 2009-02-19 21:11:41.584 Primary screen 0. 
19/02/09 9:11:41 PM [0x0-0x2ce2ce].org.osx-bundler.MythFrontend[4431] 2009-02-19 21:11:41.584 Using screen 0, 1440x900 at 0,0 

```


I did a bit of reading and there are some suggestions to try:

```

$ mysql -u root -p mythconverg
mysql> grant all on mythconverg.* to mythtv@"10.1.1.%" identified by "mythtv";
mysql> flush privileges;

```

But to no avail. After doing this the remote frontend server still gives the same error. 

So I have no idea what to try next. If anyone could help that would be great.

Thanks,

---

### Post by azmyth on 2009-02-19
Did you change the MB user password on the Mac side? When installing the default pass is mythtv, MB generated a random password. I just connected a frontend remotely and I had to change the pass.

---

### Post by PelleGris on 2009-02-19
I had the same problem and it was the database not allowing any hosts to connect to it.
You can install a database-tool and check it by typing (in a terminal): sudo apt-get install mysql-admin 
Also check that your /etc/mysql/my.cnf doesn't have a line: bind-address = 127.0.0.1. That will stop your database from listening on your network adapter. Just put a # in front of the line....

PelleGris

---

### Post by sickgemini on 2009-02-21
Thanks guys. 

I checked the my.cnf file and all was ok. I installed the database tool and checked the passwords. The password for the remote mythtv user was different than expected. I fixed it up an it is working now. 

Thanks again. Much appreciated.

---

