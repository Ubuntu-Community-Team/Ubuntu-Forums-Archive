---
title: "ports used"
date: 2009-03-31
forum: Networking &amp; Wireless
---

### Post by majikhotline on 2009-03-31
what command can i use to see all the ports that my NIC card is using right now?

thx

---

### Post by _Purple_ on 2009-03-31
Type netstat in terminal

---

### Post by capscrew on 2009-03-31
> **majikhotline said:**
> what command can i use to see all the ports that my NIC card is using right now?

thx

Try this:```
netstat -nptul
```

The results should look like this:```

netstat -nptul
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:901             0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      -               
udp        0      0 0.0.0.0:52742           0.0.0.0:*                           -               
udp        0      0 192.168.1.12:137        0.0.0.0:*                           -               
udp        0      0 0.0.0.0:137             0.0.0.0:*                           -               
udp        0      0 192.168.1.12:138        0.0.0.0:*                           -               
udp        0      0 0.0.0.0:138             0.0.0.0:*                           -               
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           -               
udp6       0      0 :::177                  :::*        
```

---

### Post by BkkBonanza on 2009-03-31
More specifically,

sudo netstat -ln

Which shows you all ports open listening in numeric notation. It will also dump a bunch of unix sockets. Ignore those and back up to the tcp/udp ones at the top of list.

Edit - oops someone beat me to it...

---

