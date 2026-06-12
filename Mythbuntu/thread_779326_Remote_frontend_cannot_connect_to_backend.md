---
title: "Remote frontend cannot connect to backend"
date: 2008-05-02
forum: Mythbuntu
---

### Post by bla2000 on 2008-05-02
My backend server ip is 192.168.1.4. How do I fix the following?

```

xxx@hardy2:~$ mysql -u mythtv -pXXX-h 192.168.1.4 mythconverg
ERROR 1045 (28000): Access denied for user 'mythtv'@'hardy2.local' (using password: YES)

```

I've looked at [http://www.mythtv.org/docs/mythtv-HOWTO-6.html#ss6.2]("http://www.mythtv.org/docs/mythtv-HOWTO-6.html#ss6.2") and done the following:

```

$ mysql -u root mythconverg
mysql> grant all on mythconverg.* to mythtv@"%" identified by "mythtv";
mysql> flush privileges;

```

I've also checked /etc/mysql/my.cnf and changed set "bind-address=192.168.1.4" and made sure "skip-networking" is not found. Do I have to add an entry into /etc/hosts.allow on my backend?

Thanks

---

### Post by bla2000 on 2008-05-03
On my backend 192.168.1.4 I tried:

```

xxx@hardy1:~$ mysql -u mythtv -pXXX -h localhost mythconverg

```

and it connects. But when I still get an error when I try:

```

xxx@hardy1:~$ mysql -u mythtv -pXXX -h 192.168.1.4 mythconverg
ERROR 1045 (28000): Access denied for user 'mythtv'@'hardy1.local' (using password: YES)

```

How do I fix this?

---

### Post by volkswagner on 2008-05-03
If you changed the default password for mysql mythtv user, you will need to tell mysql.  You will need to get your mysql prompt with root user and perform a change password command.

Check here if you need the commands.  

[http://www.cyberciti.biz/faq/mysql-change-root-password/]("http://www.cyberciti.biz/faq/mysql-change-root-password/")

---

### Post by bla2000 on 2008-05-03
I set the password to be the same as shown in:

```

mysql> select host, user, password from user;
+--------------+------------------+-------------------------------------------+
| host         | user             | password                                  |
+--------------+------------------+-------------------------------------------+
| localhost    | root             |                                           | 
| hardy1       | root             |                                           | 
| 127.0.0.1    | root             |                                           | 
| localhost    |                  |                                           | 
| hardy1       |                  |                                           | 
| localhost    | debian-sys-maint | *CE19B4B351A9A3318C7AB4DB72FEE5E316546D4E | 
| localhost    | mythtv           | *7E599B667CFA08BEF39E0B49F0E5E83CA2A43C41 | 
| %            | mythtv           | *7E599B667CFA08BEF39E0B49F0E5E83CA2A43C41 | 
| 192.168.1.%  | mythtv           | *7E599B667CFA08BEF39E0B49F0E5E83CA2A43C41 | 
| %.local      | mythtv           | *7E599B667CFA08BEF39E0B49F0E5E83CA2A43C41 | 
| hardy1.local | mythtv           | *7E599B667CFA08BEF39E0B49F0E5E83CA2A43C41 | 
+--------------+------------------+-------------------------------------------+
11 rows in set (0.00 sec)

```

but I still get: 

```

xxx@hardy1:~$ mysql -u mythtv -pXXX -h 192.168.1.4 mythconverg
ERROR 1045 (28000): Access denied for user 'mythtv'@'hardy1.local' (using password: YES)


```

---

### Post by bla2000 on 2008-05-03
It is fixed now.  The following code work from my remote computers but not my backend server.

```

xxx@hardy2:~$ mysql -u mythtv -pXXX -h 192.168.1.4 mythconverg

```

The problem was the mythtv user had different passwords.  Whenever I did:

```

$ mysql -u root mythconverg
mysql> grant all on mythconverg.* to mythtv@"%" identified by "mythtv";
mysql> flush privileges;

```

by default it would set up the new user with the same password as the "debian-sys-maint" password.

---

