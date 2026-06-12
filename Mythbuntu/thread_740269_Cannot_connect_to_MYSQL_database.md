---
title: "Cannot connect to MYSQL database"
date: 2008-03-30
forum: Mythbuntu
---

### Post by Depressed Man on 2008-03-30
When I try to setup the backend it can't access the database. So I tried seeing if it was up by command line.

vforviktor@vendetta:~$ mysql -u mythtv -p mythconverg
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

After enering the password it says it just can't connect. Then again when I installed MythTV through synaptic on Hardy Heron I don't think it installed the MYSQL server itself (it installed the MYSQL client and it said it setup a database) but when I look at there again the MYSQL server package isn't installed.

---

### Post by tgm4883 on 2008-03-30
What MythTV packages did you install in synaptic?

---

### Post by mvan83 on 2008-03-31
Is the mysql daemon running? Run this:
```
ps aux|grep mysqld
```
and paste the results here.

---

### Post by laga on 2008-03-31
> **Depressed Man said:**
> Then again when I installed MythTV through synaptic on Hardy Heron I don't think it installed the MYSQL server itself (it installed the MYSQL client and it said it setup a database) but when I look at there again the MYSQL server package isn't installed.

I think you, uhm, need to install the mysql server package.

---

### Post by Depressed Man on 2008-03-31
> **mvan83 said:**
> Is the mysql daemon running? Run this:
```
ps aux|grep mysqld
```
and paste the results here.

vforviktor@vendetta:~$ ps aux|grep mysqld
1000     10690  0.0  0.0   3004   764 pts/0    R+   12:39   0:00 grep mysqld

I installed the 0.25-0ubuntu1 (hardy) with the mythtv-backend, common and frontend as 0.21.0+fixes16838

When I tried installing the MYSQL server packages they had me setup another database..

---

