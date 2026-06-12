---
title: "Change MySQL user password"
date: 2008-08-28
forum: Mythbuntu
---

### Post by uMuppet on 2008-08-28
Mythbuntu always generates a random MySQL password.  How can I choose my own password?  I've dug around alot and only found how to change the root password.

Thanks

---

### Post by ian dobson on 2008-08-29
Hi,

The mysql password is saved in the mysql.txt file. This file is usually in /etc/mythtv/mysql.txt or /home/mythtv/.mythtv/mysql.txt where mythtv is the user that runs the backend.

Just edit the line DBPassword= to the password you want to use and then change the password with mysqladmin to change the password in Mysql.

Regards
Ian Dobson

---

### Post by jimgrill on 2008-08-29
ditto on the mysql.txt...

to change the password in mysql connect as root

```
mysql -uroot -p
(enter your root password when prompted)
mysql> SET PASSWORD FOR mythtv = PASSWORD('new_password_here');

```

You'll want to double check your setup screens in mythtv to be sure the correct password shows up there as well.

---

### Post by fatlard on 2008-08-31
I used a different syntax.

```
mysql -u root mysql

```

```
mysql> UPDATE user SET Password=PASSWORD('mythtv') WHERE user='mythtv';
mysql> FLUSH PRIVILEGES;
```

---

### Post by fatlard on 2008-08-31
Oh yeah.. make sure you change your password for mythweb

---

