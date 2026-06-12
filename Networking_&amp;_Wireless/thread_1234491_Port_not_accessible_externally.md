---
title: "Port not accessible externally"
date: 2009-08-07
forum: Networking &amp; Wireless
---

### Post by syrgak on 2009-08-07
Hi all,

here is the problem:

I have an ubuntu server running apache in my LAN and jabber server written in PHP on top of it. A php-script opens a socket and listens to 5222 port. 
Locally it works just fine:

# telnet localhost 5222 -> OK

But the port is not accessible from other machines in my local network.

I'm looking for a way make it publicly available.

Below is a result for my netstat:

netstat -an | grep LISTEN
tcp        0      0 127.0.0.1:5222          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:23              0.0.0.0:*               LISTEN     
tcp6       0      0 :::80                   :::*                    LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN  

If you have a look at it, ports 21, 22, 23 are available (I can connect from other machines to them without problems) 
and I started to think there should be a difference between: 127.0.0.1:5222 and 0.0.0.0:5222.

Say, if as an experiment if the port 23 has been opened as:

# 127.0.0.1:23 

and not as it is:

# 0.0.0.0:23

it wouldn't be accessible from other machines, correct?
If so, is there way to make my application listen as 0.0.0.0:port ... 

   

I'm not asking for an answer, I need more a push in right direction.

Thanks in advance,

---

### Post by syrgak on 2009-08-07
solved. closed.

---

