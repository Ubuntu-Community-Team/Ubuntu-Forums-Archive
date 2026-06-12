---
title: "Waiting for database schema upgrade lock"
date: 2014-03-10
forum: Mythbuntu
---

### Post by wayover13 on 2014-03-10
This query is part of my continuing saga to upgrade from mythbuntu 10.04 to 12.04. Again, this is a combination FE/BE machine. 12.04 has been really buggy and tenuous for me: I thought it would have been better stabilized by now.

I got some of the bugs worked out. I decided to add a ppa that would get me myth .27, thinking the system might work a bit better. That didn't make much difference.

Today, however, when I did an apt-get upgrade, I've got a new show-stopping problem. The message is what appears in the title of this thread. For some reason the database can't get a "lock" (whatever that means). This seems to be preventing the BE from starting. And the FE keeps crashing, apparently because the BE, and maybe most importantly, mysql, is not up.

I also get an on-screen pop-up message with the text "This version of mythtv requires and updated database . . . Please run mythtv-setup or mythbackend to update your database." Meantime, I can neither start mythbackend manually (gives an unending sequence of database lock errors as above), nor run mythtv-setup (I believe because the BE won't start owing to the database lock problem). Suggestions, pointers, advice?

---

### Post by blm-ubunet on 2014-03-10
Mythtv-setup must be run first after an upgrade & you need to make sure the backend has stopped.
```
sudo service mythtv-backend stop
mythtv-setup
```

The database upgrade can take several minutes.

What does this return:
```
sudo service mysql status
sudo service mythtv-backend status
```


if mysql is not running then can start with:
sudo service mysql start
But the problem could be that the BE tries to start before mysql has started or mysql is listening on the different IP address.

I believe there have been changes to syntax of the config files for mysql.

MythTV has moved from the .txt file to config.xml file..
The search path is /home/"user"/.mythtv/config.xml and then iff not found /etc/mythtv/config.xml.

---

### Post by wayover13 on 2014-03-10
> **blm-ubunet said:**
> 
What does this return:
```
sudo service mysql status
sudo service mythtv-backend status
```
Thanks for your reply, blm-ubunet. The first command returns "mysql start/running, process 973." The second command return "mythtv-backend stop/waiting." So mysql appears to be running. Not sure how to interpret the output for the backend: I guess lack of a PID means it's not running? I'll have a look at config.xml to see if that will help clear anything up for me.

---

### Post by wayover13 on 2014-03-10
I'd guess these might be the most relevant lines from /home/user/.mythtv/config.xml? ```
<Host>localhost</Host>
<UserName>mythtv</UserName>
  . . .
<Port>3306</Port>
```

---

### Post by wayover13 on 2014-03-10
This problem is getting weirder. I'm not sure now whether the upgrade lock is the source of the issues, or not.

One of my big problems is that the FE wants to start and keep respawning itself, though the only thing it really does is show me the need-to-upgrade message. That pop-up has an "ok" box in it, and if I select that, the FE exits briefly, only to respawn itself and show the same message all over again. It's kind of hard to do any troubleshooting when this keeps happening.

With some deft movement, though, I was able to open a terminal between respawnings and issue the command mythtv-setup from it. That goes through a process of killing the BE, I think (though there's nothing to kill since it's not running), then it seems to want to start the database upgrade process. The screen is taken up by a window that warns me mythtv wants to update the database from 1303 to 1317, and which has button to "exit" or "upgrade" at the bottom. So I select "upgrade." Then I get another screen with a wanring that the process cannot be undone, and giving the same two selection buttons at the bottom. Again, I select "upgrade." That results in the fleeting appearance of a terminal with some text scrolling past that quickly disappears and is replaced by a GUI pop-up asking me if I want to start the mythtv backend (I've seen this before after I've run mythtv-setup from the GUI menu). I select yes, then another GUI pop-up appears asking if I want to run mythfilldatabase. I select "no," and in the original terminal I started all this from there appears a PID number. However, when I check the status of the BE just a few seconds later using "sudo service mythtv-backend status" I get "mythtv-backend stop/waiting." So the BE process dies or is killed quickly.

The database is clearly not getting upgraded. And it appears as though the FE may not be starting because of this. I am unsure if this could be preventing the BE from running. Again, any tips or suggestions will be appreciated.

---

### Post by wayover13 on 2014-03-10
Ok. Some additional information. I decided to try running "sudo mythbackend" from a terminal session served via ssh. Here's some relevant output I got when I did that: > Warning: MythTV wants to upgrade your database,
for the TV schema, from 1303 to 1317.
MythTV was unable to backup your database.

Database Host: localhost
Database Name: mythconverg

WARNING: MythTV was unable to backup your database.


Shall I upgrade this database? [yes]  2014-03-10 17:38:01.449646 E  DBUtil: Error backing up database: 'mysqldump --defaults-extra-file='/tmp/mythtv_db_backup_conf_ZDgHBP' --host='localhost' --port='3306' --user='mythtv' --add-drop-table --add-locks --allow-keywords --complete-insert --extended-insert --lock-tables --no-create-db --quick 'mythconverg' > '/var/lib/mythtv/db_backups/mythconverg-1303-20140310223801.sql' 2>/dev/null' (2)
yes

A database backup might be a good idea
Are you sure you want to upgrade? [no]  yes
2014-03-10 17:38:16.807905 C  Upgrading to MythTV schema version 1304
2014-03-10 17:38:16.815497 E  DB Error (Performing database upgrade): 
Query was: UPDATE recordedseek SET starttime = CONVERT_TZ(starttime, 'SYSTEM', 'Etc/UTC') ORDER BY -starttime 
Error was: Driver error was [2/144]:
QMYSQL: Unable to execute query
Database error was:
Table './mythconverg/recordedseek' is marked as crashed and last (automatic?) repair failed
 
new version: 1304
2014-03-10 17:38:16.815529 E  Database schema upgrade failed.
2014-03-10 17:38:16.815779 E  Couldn't upgrade database to new schema

---

### Post by wayover13 on 2014-03-10
The previously posted error messgae output allowed me to find an old forum thread that seemed like it might be relevant (see [http://ubuntuforums.org/archive/index.php/t-1807234.html](http://ubuntuforums.org/archive/index.php/t-1807234.html)). So I tried the database repair command suggested there: ```
mysqlcheck -u mythtv -p<password> --repair mythconverg
``` That did finally repair the database and allow me to once again boot sanely into my mythbuntu system. So it looks like this hurdle has been surmounted. Now, to figure out why scheduling recordings via mythweb isn't working.

---

