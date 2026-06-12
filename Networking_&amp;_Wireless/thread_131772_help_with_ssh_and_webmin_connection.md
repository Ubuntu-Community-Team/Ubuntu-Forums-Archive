---
title: "help with ssh and webmin connection"
date: 2006-02-17
forum: Networking &amp; Wireless
---

### Post by Hotchilli on 2006-02-17
I can connect to ssh on port 22 from my box and also to webmin web interface on port 10000/ but not from outside 

here is what netstat says

Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 localhost:10000         localhost:32822         TIME_WAIT
tcp        0      0 localhost:10000         localhost:32827         ESTABLISHED
tcp        0      0 localhost:10000         localhost:32826         ESTABLISHED
tcp        0      0 localhost:ssh           localhost:32821         ESTABLISHED
tcp        0      0 localhost:32827         localhost:10000         ESTABLISHED
tcp        0      0 localhost:32826         localhost:10000         ESTABLISHED
tcp        0      0 localhost:32821         localhost:ssh           ESTABLISHED
Active UNIX domain sockets (w/o servers)

when I type

netstat -at | grep 22

i am just returned to the comand prompt

when I tpye netstat -at | grep 10000 i get

tcp        0      0 *:10000                 *:*                     LISTEN


any ideas how to establish a connection from outside my box

here is what netstat -tln  looks like
root@4096:~# netstat -tln
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 0.0.0.0:20000           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:8002            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:70              0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:11372           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN
tcp        0      0 192.168.1.64:53         0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:119             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN




hc;) ;)

---

