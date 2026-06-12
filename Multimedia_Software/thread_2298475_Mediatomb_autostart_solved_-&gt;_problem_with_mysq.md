---
title: "Mediatomb autostart solved -&gt; problem with mysql access in owncloud"
date: 2015-10-11
forum: Multimedia Software
---

### Post by marco118 on 2015-10-11
Hi,

my first problem to solve was autostarting Mediatomp in Ubuntu Server 14.04.
I found the solution in t[his thread]("http://ubuntuforums.org/showthread.php?t=1971040") (*by editing /etc/init/mediatomp.conf)*

Now i have the problem, that owncloud gives me this fatal error:

> Exception: {"Message":"HTTP\/1.1 503 Doctrine\\DBAL\\DBALException: Failed to connect to the database: An exception occured in driver: SQLSTATE[HY000] [2002] Can't connect to local MySQL server through socket '\/var\/run\/mysqld\/mysqld.sock' (2)"

So owncloud couldn't connect to mysql database in init process. After init, owncloud has access to mysql.
But why initscript-manipulation (*"started mysql and local ....*)" in mediatomp.conf prohibits mysql access to owncloud?

---

