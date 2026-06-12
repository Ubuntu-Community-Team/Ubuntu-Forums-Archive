---
title: "mythtv-setup does not connect to mysql database"
date: 2008-08-25
forum: Mythbuntu
---

### Post by mm44mm44 on 2008-08-25
Hello,

I did a fresh install of Mythbuntu 8.04.01-desktop-i386 on an VIA Epia ME 6000 system.

The system boots fine but I am not able to configure Mythtv using
```
$sudo mythtv-setup
```
In a popup window I see:
> Acess denied for user 'mythtv'@'localhost' using password (YES)
and some other error messages.

I had already checked google and searched this forum.

I had already done

```
sudo dpkg-reconfigure mythtv-database
sudo dpkg-reconfigure mythtv-common

```
(And never entered any passwords)

I also checked
```
raimoed@myth-tv:~$ grep mythtv: /etc/group
mythtv:x:110:ubuntu,raimoed,root,mythtv

```

I also did 
```

mysql -u root -p
Pasword:[ENTER]

mysql> CREATE DATABASE mythconverg;
ERROR 1007 (HY000): Can't create database 'mythconverg'; database exists
mysql> GRANT ALL ON mythconverg.* TO 'mythtv'@'localhost' IDENTIFIED BY 'mythtv';
Query OK, 0 rows affected (0.04 sec)

mysql>
mysql> use mysql;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> UPDATE user SET Password=PASSWORD('mythtv') WHERE user='mythtv';
Query OK, 0 rows affected (0.01 sec)
Rows matched: 2  Changed: 0  Warnings: 0

mysql> FLUSH PRIVILEGES;
Query OK, 0 rows affected (0.00 sec)

```

but mythtv-setup does not work.
What do I do wrong here?

Thanks for help

Raimund

---

### Post by stevanbt on 2008-08-26
Hi,
Are you sure you need to run mythtv-setup as sudo?  Please try without being sudo.

Thanks, Steve.

---

### Post by volkswagner on 2008-08-26
Can you log into mysql with mythtv user and it's password.  If you can't, you need to set the correct password.  As indicated above no changes were made to the database.

---

### Post by mm44mm44 on 2008-08-27
@stevanbt
if I run mythtv-setup as normal user *raimoed* I will be asked for my password and the same happens again.

@volkswagner
> Can you log into mysql with mythtv user and it's password.
I will be asked for a password, but I have none....
```
raimoed@myth-tv:~$ mysql -u mythtv -p
Enter password: 
```

How do I change the password of mythtv?
How do I make sure, that this password is used, when I run mythtv-setup?

Thanks for another help

Raimund

---

### Post by stevanbt on 2008-08-27
Hi,
I think this is right (not at my MythBox now) MythTv stores it's MySQL password in /etc/mysql/my.cnf.  You could check this out and try to connect using that password (userid will be in there too).  

But to be honest I don't know if this will work as you have tried to change MythTv's MySQL password.

Thanks, Steve.

---

### Post by mm44mm44 on 2008-08-27
> MythTv stores it's MySQL password in /etc/mysql/my.cnf.
Unfortunately this did not work either.
I could not find passwords and no mythtv entrys in this file.

But don't mind. I will end this thread here and I may try it with another distribution later.

Thanks for your kind help so far.

Raimund

---

### Post by ReddogOne on 2008-08-27
Not at all experienced in this (apart from a couple of installs)...

... but maybe just follow [http://parker1.co.uk/mythtv_ubuntu.php]("http://parker1.co.uk/mythtv_ubuntu.php") (or the appropriate page for what you want to do).

As always in Linux there is an extremely easy way to do something and a really hard way. Unfortunately you tend to find the hard way ;)

---

