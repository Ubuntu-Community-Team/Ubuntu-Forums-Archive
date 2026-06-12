---
title: "MythTV Setup"
date: 2006-11-22
forum: Multimedia &amp; Video
---

### Post by mwacky on 2006-11-22
Hello,

I'm fairly new to Linux, I gotta say I tried a couple different distros and ubuntu has been great.

With an old gateway performance pc, I've verified that my tv card works with tvtime; but the ultimate goal is to turn it into a dvr with mythtv.

I installed MythTV 0.18 and MySQL with Synaptic, following this [article]("http://www.mythtv.org/wiki/index.php/Ubuntu_Dapper_Installation#MythTV_0.18_Packages").

When I start mythtv it takes me through the initial setup where you specify language, etc., but afterwards stops giving with the following code in the terminal:
```

2006-11-22 21:03:26.677 Using WOL to wakeup database server (Try 1 of 5)
WOLsqlServerCommand not set
2006-11-22 21:03:26.741 Using WOL to wakeup database server (Try 2 of 5)
WOLsqlServerCommand not set
2006-11-22 21:03:26.810 Using WOL to wakeup database server (Try 3 of 5)
WOLsqlServerCommand not set
2006-11-22 21:03:26.873 Using WOL to wakeup database server (Try 4 of 5)
WOLsqlServerCommand not set
2006-11-22 21:03:26.942 Using WOL to wakeup database server (Try 5 of 5)
WOLsqlServerCommand not set
2006-11-22 21:03:26.978 WOL failed, unable to connect to database!
2006-11-22 21:03:26.979 Unable to connect to database!
2006-11-22 21:03:26.979 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

2006-11-22 21:03:26.980 Failed to init MythContext, exiting.
```

Any Suggestions?  It seems like maybe I have failed to start the mysql database?

---

### Post by awbassett on 2006-11-22
Looks like your password is incorrect and you probably forgot this step...

You may have to update the database access permissions to match the password defined in ~mythtv/.mythtv/mysql.txt. The example shows setting the password to "mythtv":

mysql -u root mythconverg
set password for 'mythtv'@'%' = password('mythtv');
set password for 'mythtv'@'localhost' = password('mythtv');
flush privileges;


Your password doesn't have to be mythtv obviously, but make sure the password matches in the database and in the mysql.txt file. HTH

---

