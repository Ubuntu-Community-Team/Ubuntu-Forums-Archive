---
title: "Connection issues"
date: 2011-04-16
forum: Mythbuntu
---

### Post by flobbalobalob on 2011-04-16
Please help!
I have installed a mythbuntu backend/frontend combo upstairs and that all works fine. However when i try to connect a remote front end it wont connect.
Here's as far as it gets.

```
lee@lee-901:~$ mythfrontend
2011-04-16 10:38:03.850 mythfrontend version: branches/release-0-23-fixes [26437] www.mythtv.org
2011-04-16 10:38:03.851 Using runtime prefix = /usr
2011-04-16 10:38:03.852 Using configuration directory = /home/lee/.mythtv
2011-04-16 10:38:03.855 MediaRenderer::HttpServer Create Error
2011-04-16 10:38:03.858 Empty LocalHostName.
2011-04-16 10:38:03.858 Using localhost value of lee-901
2011-04-16 10:38:03.859 Testing network connectivity to '192.168.0.7'
2011-04-16 10:38:03.891 New DB connection, total: 1
```

I would assume from this that there's a problem connecting remotely to the database, but I can connect to it manually. I've tried two front ends and they both hang in the same place so I guess it must be a backend issue.

Any ideas would be greatly appreciated

Cheers

---

### Post by ian dobson on 2011-04-16
Hi,

Have you changed the mysql configuration so that it binds to all IP addresses (comment out the line bind= in the my.cnf)

Regards
Ian Dobson

---

### Post by flobbalobalob on 2011-04-16
Yes, I have also tried setting it to the backend ip. neither made a difference.

---

### Post by ian dobson on 2011-04-16
Hi,

Are you sure that mysql is listening  on your external interface.

What do you see when you do:-

netstat -l | grep mysql

On my backend I see:-
```
tcp        0      0 *:mysql                 *:*                     LISTEN
unix  2      [ ACC ]     STREAM     LISTENING     48108    /var/run/mysqld/mysqld.sock
```
The first line is the tcp connection.

Regards
Ian Dobson

---

### Post by flobbalobalob on 2011-04-16
The database seems to be fine. I can connect to it from the front ends with the command line and search through the tables. I think I've tracked the problem down to the backend and something's already using port 6543. can't figure out what though.

thanks for the suggestion

---

