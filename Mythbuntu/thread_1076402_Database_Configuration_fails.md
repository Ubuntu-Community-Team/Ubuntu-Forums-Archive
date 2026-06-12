---
title: "Database Configuration fails"
date: 2009-02-21
forum: Mythbuntu
---

### Post by Konzales on 2009-02-21
Hi, I am new to Mythbuntu and just installed it from the alternate CD. When I start the MythTV-Setup from Control Centre it always says `No UPnP backends found` and after clicking through the two pages it says `Cannot connect to port 6543 on database host localhost`. Afterwards it starts again with the same questions

etc/mysql/my.cnf states:
bind-address		= 127.0.0.1

and etc/mythtv/mysql.txt says:
DBPort=6543
DBUserName=mythtv
DBPassword=****
DBName=mythconverg
DBType=QMYSQL3

Please help

---

### Post by Konzales on 2009-02-21
I just found that I have to change the port :D

---

