---
title: "[SOLVED] Amarok database connection error."
date: 2008-06-15
forum: Multimedia Software
---

### Post by momo07 on 2008-06-15
Hello,

I have a problem with Amarok connecting to MySQL. I setting up the app with the following db connection: 
Hostname: localhost
Database: amarok
port: 3306
I left the password feilds blank and this is the message I keep getting: 

[B][I]MySQL reported the following error:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock'(2)[/I][/B] 

Any suggestions, thanks in advance

---

### Post by momo07 on 2008-06-17
Never mind.  I had to install MySQL server on my machine from the synaptic package manager and this solved the problem.

Thanks

---

