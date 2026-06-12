---
title: "Myth FE stuck in Endless Loop"
date: 2012-05-29
forum: Mythbuntu
---

### Post by nhtrader on 2012-05-29
MythTV v0.25
Ubuntu 12.04 64bit
Fresh Clean Install

I'm now stuck on FE page: "Database Configuration 1/2"

Selecting "Finish" button on page 2 brings me back to page 1 - Endless loop.


How I got in this mess...

1. Today I transferred videos from backup HDD to Myth025:/var/lib/mythtv/videos
2. sudo chown mythtv:mythtv *.*

3. opened FE |Media Library| Video Library| scan for changes & populated with videos (all present and accounted for). This worked and FE responds normally.

4. exited FE
5. Open webbrowser to check entry via MythWEB
6. [http://localhost/mythweb](http://localhost/mythweb) login prompt appears
7. enter UN and PWD - OK
8. result - ERROR 
```

!NoTrans: Access denied for user 'mt_dad'@'localhost' (using password: YES) [#1045]

 Backtrace
 Array
 (
 [0] => Array
 (
 [file] => /usr/share/mythtv/mythweb/classes/Database/Query/mysql.php
 [line] => 63
 [function] => error
 [class] => Database
 [object] => Database_mysql Object
 (
 [dbh] => 
 [error] => Access denied for user 'mt_dad'@'localhost' (using password: YES) [#1045]
 [err] => Access denied for user 'mt_dad'@'localhost' (using password: YES)
 [errno] => 1045
 [last_sh] => Database_Query_mysql Object
 (
 [dbh] => 
 [query] => Array
 (
 [0] => SET NAMES utf8;
 )

 [last_query] => SET NAMES utf8;
 [warnings] => Array
 (
 )

 [num_args_needed] => 0
 [num_rows] => 
 [affected_rows] => 
 [insert_id] => 
 [db] => Database_mysql Object
 *RECURSION*
 )

 [fatal_errors] => 1
 [query_count] => 0
 [query_time] => 0
 [global_name] => 
 [destruct_handlers] => Array
 (
 )

 )

 [type] => ->
 [args] => Array
 (
 )

 )

 [1] => Array
 (
 [file] => /usr/share/mythtv/mythweb/classes/Database.php
 [line] => 259
 [function] => execute
 [class] => Database_Query_mysql
 [object] => Database_Query_mysql Object
 (
 [dbh] => 
 [query] => Array
 (
 [0] => SET NAMES utf8;
 )

 [last_query] => SET NAMES utf8;
 [warnings] => Array
 (
 )

 [num_args_needed] => 0
 [num_rows] => 
 [affected_rows] => 
 [insert_id] => 
 [db] => Database_mysql Object
 (
 [dbh] => 
 [error] => Access denied for user 'mt_dad'@'localhost' (using password: YES) [#1045]
 [err] => Access denied for user 'mt_dad'@'localhost' (using password: YES)
 [errno] => 1045
 [last_sh] => Database_Query_mysql Object
 *RECURSION*
 [fatal_errors] => 1
 [query_count] => 0
 [query_time] => 0
 [global_name] => 
 [destruct_handlers] => Array
 (
 )

 )

 )

 [type] => ->
 [args] => Array
 (
 [0] => Array
 (
 )

 )

 )

 [2] => Array
 (
 [file] => /usr/share/mythtv/mythweb/classes/Database.php
 [line] => 124
 [function] => query
 [class] => Database
 [object] => Database_mysql Object
 (
 [dbh] => 
 [error] => Access denied for user 'mt_dad'@'localhost' (using password: YES) [#1045]
 [err] => Access denied for user 'mt_dad'@'localhost' (using password: YES)
 [errno] => 1045
 [last_sh] => Database_Query_mysql Object
 (
 [dbh] => 
 [query] => Array
 (
 [0] => SET NAMES utf8;
 )

 [last_query] => SET NAMES utf8;
 [warnings] => Array
 (
 )

 [num_args_needed] => 0
 [num_rows] => 
 [affected_rows] => 
 [insert_id] => 
 [db] => Database_mysql Object
 *RECURSION*
 )

 [fatal_errors] => 1
 [query_count] => 0
 [query_time] => 0
 [global_name] => 
 [destruct_handlers] => Array
 (
 )

 )

 [type] => ->
 [args] => Array
 (
 [0] => SET NAMES utf8;
 )

 )

 [3] => Array
 (
 [file] => /usr/share/mythtv/mythweb/includes/database.php
 [line] => 49
 [function] => connect
 [class] => Database
 [type] => ::
 [args] => Array
 (
 [0] => mythconverg
 [1] => mt_dad
 [2] => mythtv
 [3] => localhost
 [4] => 
 [5] => mysql
 )

 )

 [4] => Array
 (
 [file] => /usr/share/mythtv/mythweb/includes/init.php
 [line] => 40
 [args] => Array
 (
 [0] => /usr/share/mythtv/mythweb/includes/database.php
 )

 [function] => require_once
 )

 [5] => Array
 (
 [file] => /usr/share/mythtv/mythweb/mythweb.php
 [line] => 20
 [args] => Array
 (
 [0] => /usr/share/mythtv/mythweb/includes/init.php
 )

 [function] => require_once
 )

 )
 !!

```

so I enter terminal mode and delete all copies of mysql.txt
sudo su
find / -name "mysql.txt -exec rm -rf '{}' \;
then 
dpkg-reconfigure mythtv-database
dpkg-reconfigure mythtv-common
reset user to mythtv with new password mbisgreat

now enter FE and stuck in endless loop.


BTW, this all started b/c I had used "mt_dad" as the database username in the previous install. Then I did what I thought was a fresh new install only to find "mt_dad" lurking about. Why wasn't "mt-dad" completely removed? I selected the option that stated all data would be destroyed.

How do I proceed? What file permissions in what DIR need to be checked/changed?

---

### Post by nhtrader on 2012-05-29
Got myself into this mess and I guess I'll have to dig my way out.

Fortunately, I don't have any recordings, movies, music, etc to backup. This was a clean install and it still got messed up.

So I'm digging the hole a bit deeper.

I used the following commands and it solved the endless loop, but at a price. I'll explain later. First the commands...


sudo su
service mysql stop
apt-get purge mysql-common
apt-get install mythtv

Again, this solved the problem. I no longer am stuck in an endless loop. And when I used FE I my settings were still intact. Plus my BE settings are still the same as well. TV channels are OK as well. 

The bad news is that "Mythbuntu Control Centre" is decimated. When I click Menus:
Applications|System|Mythbuntu Control Centre only Log Grabber exists on the Right Side. All of the other buttons (plugins, drivers, mysql, startup behaviour, etc) are missing. Plus MythWeb is gone and other plugins are non-functional b/c they are no longer installed. 

Apparently, installing rather reinstalling MythTV (apt-get install mythtv) doesn't bring back the whole essemble of gadgets and widgets that make the entirety of MythTV. Now there's a surprise. So I went into Synaptic to take a look at what might be missing, and selected to add a few packages and reinstall those that were installed. The end result is that Mythbuntu Control Centre is not fully restored.

Lesson learned. DON'T CHANGE ANY OF MYTHTV SETTINGS DURING INSTALLATION.

1. if you want to change your mind and rename your computer (change hostname) this is a problem.
2. if you want to change your mind and change your user name, this is problem.
3. if you want to change your mind and change the database name, this is problem.

This is very unforgiving. No harm; no foul. As a kid, I always enjoyed breaking stuff. The problem here is that this software is still being stress tested.

And while I'm at it. If a user elects not to install MythBrowser then the software should know not to ask the user to send a "Hardware Profile" when it can't. Since it can only send a "Hardware Profile" if MythBrowser exists. Again, stress testing and integration testing apparently are still ongoing.

---

### Post by nhtrader on 2012-05-30
PROBLEM: If you changed the username password, like I did, and get stuck; do the following to fix this problem.

SOLUTION:

Press ALT+F11 to view Menubar
select Applications|Accessories|terminal
sudo su
ps aux|grep myth
take note of process IDs which contain phrase: mythfrontend, mythtv-setup, or mythfrontend.real

then kill offending processes
kill PIDs in numerical order lowest to highest.

You should now see your desktop.

now exit root terminal
exit

now you're in user terminal mode
(notice that the prompt has changed from # to $)

now enter these commands:

mysql -u root -p

NOTE: If this command above fails (you get error msg), then stop.
Do not proceed. You're better off starting over and reinstalling MythTV from scratch. 


mysql>GRANT ALL PRIVILEGES ON mythconverg.* TO 'mythtv'@"localhost" identified by "password here" WITH GRANT OPTION;
mysql>GRANT ALL PRIVILEGES ON mythconverg.* TO 'mythtv'@"%" identified by "password here" WITH GRANT OPTION;
mysql>use mysql;
mysql>UPDATE user SET Password=PASSWORD('password here') WHERE user='mythtv';
mysql>FLUSH PRIVILEGES;
mysql>exit

Now you should be able to use MythTV Frontend and Backend.

Problem solved.

---

### Post by anonymousdog on 2012-05-31
FWIW, 'sudo su' introduces unnecessary risk by almost 100% working around the safety of a non-root account.

'sudo command' gets you that one command before dropping you to an unprivileged prompt.  It keeps you from doing something unintended or ill considered and disastrous on the next line.

'sudo su' gets you a root shell until you explicitly exit it: Much more dangerous.

I only use 'sudo su' where a whole series of commands have to execute as root in such a way that issuing a series of 'sudo command1', 'sudo command2'...'sudo commandx' would not work (and I don't want to script the whole thing).

---

### Post by nickrout on 2012-05-31
I am unsure what password nhtrader is trying to change. A user has a system password (eg for when you log in to a console). There are also users and passwords in the mythconverg mysql database. mythbuntu sets up a random password for mysql when it installs mythbuntu-common. If you want to change it you should do ```
sudo dpkg-reconfigure mythbuntu-common
``` 

just looking at the postinst script in the mythbuntu-common deb, it looks to me like it fixes mysql.txt so it has the newly generated password too, so if you actually use the provided tool you can change the password to your heart's content.

Of course the postinst script will not change the password on remote frontends, so you will need to make a note of it for your remote frontends (if any).

---

### Post by anonymousdog on 2012-05-31
At this point, he's trying to change the MySQL password in mythweb.

---

