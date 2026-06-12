---
title: "ZoneMinder Upgrade"
date: 2013-01-21
forum: Multimedia Software
---

### Post by lflindsey on 2013-01-21
Hi Y'all,

I was having some trouble with ZoneMinder across a distribution upgrade. apt-get would give me:

```
Initiating database upgrade to version 1.25.0 from version 1.24.4

Upgrading database to version 1.25.0
Loading config from DB
Saving config to DB
ERROR 1142 (42000) at line 10: CREATE command denied to user 'zmuser'@'localhost' for table 'Logs'
Output: 
Command 'mysql -hlocalhost -uzmuser -pzmpass zm < /usr/share/zoneminder/db/zm_update-1.24.4.sql' exited with status: 1
dpkg: error processing zoneminder (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 zoneminder
```

The solution that I found is this:

```
sudo mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 95
Server version: 5.5.28-0ubuntu0.12.04.3 (Ubuntu)

Copyright (c) 2000, 2012, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> grant CREATE on *.* to zmuser@localhost;
Query OK, 0 rows affected (0.00 sec)
```


After which, running

```
sudo apt-get install
```

completed successfully

---

