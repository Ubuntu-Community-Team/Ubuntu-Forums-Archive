---
title: "speed up mysql server connection/query time"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by sa125 on 2009-05-10
I'm not sure if this question fits this forum, but I'll try.

I maintain a mysql database on one of our office servers (running ubuntu 8.10 server). The server's address is found on the network using its IP or DNS address. 

The problem is that it takes between 5-10 seconds to connect to the server from another machine on the network (from the room next door), and about the same time to retrieve query results - even from tiny tables (6 rows..). I suspect this to be a network problem and not a query optimization issue, but I'm not sure how to work around it. We have another server in the office that's running dapper with the same mysql version, and its lightning fast.

This is probably something trivial, but I'd still appreciate any help on possible causes and how I might solve this problem. Thanks!

---

### Post by sa125 on 2009-05-11
if anyone happens to have the same problem, try editing your my.cnf file (typically under /etc/mysql/my.cnf, or try running "locate my.cnf" in bash).

Add **skip-name-resolve** in the [mysqld] section of the file and restart the service with /etc/init.d/mysql restart

hope this helps someone.

---

### Post by qhoore on 2011-11-28
Thanks, it work even in 2011... great tip... :D

---

