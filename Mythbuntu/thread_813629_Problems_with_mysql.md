---
title: "Problems with mysql"
date: 2008-05-31
forum: Mythbuntu
---

### Post by karlec on 2008-05-31
I am getting the following error message in the logs:
```
mysqld_safe[26382]: PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
mysqld_safe[26382]: To do so, start the server, then issue the following commands:
mysqld_safe[26382]: /usr/bin/mysqladmin -u root password 'new-password'
mysqld_safe[26382]: /usr/bin/mysqladmin -u root -h Jmyth password 'new-password'
mysqld_safe[26382]:
mysqld_safe[26382]: Alternatively you can run:
mysqld_safe[26382]: /usr/bin/mysql_secure_installation
mysqld_safe[26382]:
mysqld_safe[26382]: which will also give you the option of removing the test
mysqld_safe[26382]: databases and anonymous user created by default.  This is strongly recommended for production servers.

```

```
Checking for insecure root accounts.
/etc/mysql/debian-start[26662]: WARNING: mysql.user contains 3 root accounts without password!
```

I have two questions:
[LIST=1]
[*]how can I fix this issue?
[*]is this the reason while my scheduled recordings failed to record
[/LIST]

---

### Post by nasha on 2008-05-31
1. The information in the error log that you pasted tells you how to fix your problem...
2. Yes

---

