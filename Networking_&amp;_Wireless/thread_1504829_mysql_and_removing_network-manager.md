---
title: "mysql and removing network-manager"
date: 2010-06-08
forum: Networking &amp; Wireless
---

### Post by fx69 on 2010-06-08
Hi,
I set the static ip to my machine and removed network-manager. After this I couldn't connect to mysql:
```
fx69@fx69-desktop:~$ sudo mysql -h localhost -u root -p test
```gave an error saying that /var/run/mysqld/mysqld.sock doesn't exist
I installed network-manager back and mysqld.sock was on its place. What should I change in my.cnf file (or any other) to make mysql work without network-manager ?
I can't simply copy the mysqld.sock:
```
fx69@fx69-desktop:~$ cp /var/run/mysqld/mysqld.sock ~/
cp: cannot open `/var/run/mysqld/mysqld.sock' for reading: No such device or address
```Permissions are set only to mysql, and it seems I can't change that..
ps: sorry if I'm opening such a thread in a wrong place :)

---

