---
title: "Mythweb: Fatal Error Access Denied"
date: 2016-03-05
forum: Mythbuntu
---

### Post by ahood on 2016-03-05
Hello,

Love MythTV and Mythbuntu. I started using MythTV in 2005.

I can use some advise about a Mythweb Fatal Error Access Denied message.

**Mythweb Error**
> Fatal Error

!!NoTrans: Access denied for user 'mythtv'@'mythtv-backend' (using password: YES) [#1045]

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
[error] => Access denied for user 'mythtv'@'mythtv-backend' (using password: YES) [#1045]
[err] => Access denied for user 'mythtv'@'mythtv-backend' (using password: YES)
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

**Root Cause**
I have verified that the mythtv db password is correct in
[LIST=1]
[*]/etc/mythtv/config.xml for the backend
[*]~.mythtv/config.xml
[*]~/.mythtv/mythconverg.xml
[*]
[/LIST]

I believe the cause to be with permissions in mysql for mysql user mythtv. I am able to SSH into the Mythbuntu machine and log into mysql as root. The following hosts are designated for mythtv.

> mysql> select user,host,password from mysql.user where user = 'mythtv';
+--------+------------------------------+-------------------------------------------+
| user   | host                         | password                                  |
+--------+------------------------------+-------------------------------------------+
| mythtv | localhost                    | *9A2DFB28925AEAA50AB7B456B46C1F616EBCF707 |
| mythtv | %                            | *9A2DFB28925AEAA50AB7B456B46C1F616EBCF707 |
| mythtv | 192.168.0.%                  | *CC8F35F587CA5A556B4132C2407E556D92172FFC |
+--------+------------------------------+-------------------------------------------+


The next mysql command has the following:

> mysql> show grants for mythtv;
+-------------------------------------------------------------------------------------------------------+
| Grants for mythtv@%                                                                                   |
+-------------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'mythtv'@'%' IDENTIFIED BY PASSWORD '*9A2DFB28925AEAA50AB7B456B46C1F616EBCF707' |
| GRANT ALL PRIVILEGES ON `mythconverg`.* TO 'mythtv'@'%'                                               |
+-------------------------------------------------------------------------------------------------------+


**How to fix?**
This is where I am stumped. I am not familiar enough with mysql to know what to do. I have googled but have not come up with a page that give me confidence of the correct command to enter.

Any advise on how to modify the mysql permissions for mysql user mythtv?

---

### Post by bilkay on 2016-05-08
I'm having the same problem. Any luck with yours?

Trying to use logic (which doesn't always seem to apply), it would seem that a wrong password is being sent to mysql. Now if I could just figure out where mythweb stores the mysql login information... (Or if I could find some decent documentation)

p.s. The mythtv backend is running on Mythbuntu 14.04.4

---

### Post by bilkay on 2016-05-08
Aha! [FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][COLOR=#660066]/etc/apache2/sites-available/mythweb.conf had a strange password in it. After putting in the correct password, mythweb works.[/COLOR][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

---

