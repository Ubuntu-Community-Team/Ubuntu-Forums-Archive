---
title: "upnp no ping"
date: 2008-05-31
forum: Mythbuntu
---

### Post by haman30 on 2008-05-31
help trying to set up mythbuntu on pc but first thing that happens is ther no upnp look int to it on forums got this far but after this i'm stuck here is where i got to i terminal at this point is total diffent to advice found so far
hamish@hamish:~$ sudo mysqldump -u mythtv -p mythconverg recorded > recorded.sql
[sudo] password for hamish: 
Enter password: 
mysqldump: Got error: 1045: Access denied for user 'mythtv'@'localhost' (using password: YES) when trying to connect
hamish@hamish:~$ sudo /etc/init.d/mysql restart
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
hamish@hamish:~$

---

### Post by tgm4883 on 2008-05-31
> **haman30 said:**
> help trying to set up mythbuntu on pc but first thing that happens is ther no upnp look int to it on forums got this far but after this i'm stuck here is where i got to i terminal at this point is total diffent to advice found so far
hamish@hamish:~$ sudo mysqldump -u mythtv -p mythconverg recorded > recorded.sql
[sudo] password for hamish: 
Enter password: 
mysqldump: Got error: 1045: Access denied for user 'mythtv'@'localhost' (using password: YES) when trying to connect
hamish@hamish:~$ sudo /etc/init.d/mysql restart
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
hamish@hamish:~$

First, you should edit your title to something that actually represents the problem.

Secondly, you are using the wrong password it would seem.  Are you using the password from ~/.mythtv/mysql.txt

---

