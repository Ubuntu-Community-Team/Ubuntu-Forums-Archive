---
title: "Can't run Mythtv setup"
date: 2007-01-26
forum: Multimedia &amp; Video
---

### Post by JezV on 2007-01-26
Hi

I'm trying to install Mythtv on edgy 6.10 to run as a combined frontend/backend/desktop machine.  I have followed the guide [https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop) which is ok, up until I run 'mythtv-setup', at which point I get the following:
> QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-01-26 22:44:13.188 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-01-26 22:44:13.244 Database not open while trying to save setting: Language
2007-01-26 22:44:13.244 Unable to connect to database!
2007-01-26 22:44:13.244 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

BUT when I look at /var/log/mythtv/mythbackend.log I get the following:

> Current Schema Version: 1160
No setting found for this machine's BackendServerIP.
Please run setup on this machine and modify the first page
of the general settings.

This implies it is connecting to the database ok, but the ip address is wrong.  But I can't run setup to change it.  

Any ideas?  Thanks.

---

### Post by lssl on 2007-01-27
Hi!
You can edit /home/YOUR_USER_NAME/.mythtv/mysql.txt and /etc/mythtv/mysql.txt to change your settings, but first try to add mythtv user to mysql datebase```
$ mysql -u root -p mythconverg
mysql> grant all on mythconverg.* to mythtv@"localhost" identified by "mythtv";
mysql> flush privileges;
``` restart mysql server ```
sudo /etc/init.d/mysql restart
``` and then run mythtv-setup.

---

### Post by JezV on 2007-01-28
Hey, thanks lssl

With your help I have got the setup program running and the frontend up.  Just need to get frontend and backend talking to each other now!  One for another day when I have a bit more time.

If anyone else reads this in the future, check the username and passwords in the two mysql.txt files that lssl mentioned above.

Thanks again

Jez

---

