---
title: "Mythbuntu Fails to Connect to MySQL"
date: 2009-02-08
forum: Mythbuntu
---

### Post by lightsout565 on 2009-02-08
I just installed mythbuntu using Wubi and it automatically jumps you to step 11 of 15 when you start it for the first time. It attempts to connect to the backend but fails. All the information is pre-entered and I double checked it all at /etc/mythtv/mysql.txt. I cant proceed until it connects. Any advice is appreciated.

---

### Post by scary_jeff on 2009-02-09
Is mysqld running? If not, what happens if you sudo mysqld? If yes, is it set up for the correct IP address (see bind address in /etc/mysql/my.cnf)? I had a bit of a nightmare with network manager and mysqld, where the network wasn't up in time for mysql to bind to its address.

---

### Post by lightsout565 on 2009-02-09
I was looking at the mythbuntu control center and when I exited, it asked me if I wanted to run the mythfilldatabase.I sellected ok. everything is automatically entered and I get some more errors. Access denied for user 'mythtv'@'localhost' (using password: YES) then it says the database isn't open.

I also ran sudo mysqld and I got a bunch of these.

InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.

---

### Post by scary_jeff on 2009-02-09
OK, so it looks like mysql is running already. Can you look in /etc/mysql/my.cnf, and see what the bind address is? Myth is trying to connect to localhost, so the bind address should be 127.0.0.1.
If it is, then a password must be wrong somewhere. I can't remember how to change the mysql password, but there's bound to be an explanation somewhere else on the forums.

---

