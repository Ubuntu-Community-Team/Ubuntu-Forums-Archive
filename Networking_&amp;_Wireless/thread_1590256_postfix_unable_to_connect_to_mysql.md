---
title: "postfix unable to connect to mysql"
date: 2010-10-07
forum: Networking &amp; Wireless
---

### Post by srainsdon on 2010-10-07
found this post [http://ubuntuforums.org/showthread.php?t=251119]("http://ubuntuforums.org/showthread.php?t=251119")

did what it said and changed the 
```
host = localhost to host = 127.0.0.1
```
but postfix is still unable to connect

when i run the command:
```
postmap -q test1@thegamequest.com mysql:/home/config/mysql-users.cf
```
it returns correct and the same for and outer postmap query that is in the database

---

