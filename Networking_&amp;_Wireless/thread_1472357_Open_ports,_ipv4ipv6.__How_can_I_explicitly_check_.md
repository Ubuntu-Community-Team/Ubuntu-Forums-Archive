---
title: "Open ports, ipv4/ipv6.  How can I explicitly check ipv4?"
date: 2010-05-04
forum: Networking &amp; Wireless
---

### Post by Huufarted on 2010-05-04
Normally I use 'netstat -an' to determine if a daemon is listening on a specific port.  The excerpt of this command below doesn't list things like vnc (5900) on ipv4.  It DOES however show it on ipv6.  My issue is I want to know how to determine if it is indeed listening on ipv4 as would normally be seen with 0.0.0.0:5900.

It would appear that all ipv4 ports are internally being redirected to ipv6.  Of course this does simplify things, but it also leaves me unable to reliably determine the ipv4 listening status.

Any ideas on how I can tell at a glance if a specific ipv4 port is being listened on?  Is there a way to force netstat to list the ipv4 listens specifically?

```

art@eee1:/proc/sys/net/ipv6$ netstat -an
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State     
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:23              0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:49451           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     
tcp6       0      0 ::1:8080                :::*                    LISTEN     
tcp6       0      0 :::80                   :::*                    LISTEN     
tcp6       0      0 :::7443                 :::*                    LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN     
tcp6       0      0 :::445                  :::*                    LISTEN     
tcp6       0      0 :::7070                 :::*                    LISTEN     
tcp6       0      0 :::7777                 :::*                    LISTEN     
tcp6       0      0 :::9090                 :::*                    LISTEN     
tcp6       0      0 :::9091                 :::*                    LISTEN     
tcp6       0      0 :::5222                 :::*                    LISTEN     
tcp6       0      0 :::5223                 :::*                    LISTEN     
tcp6       0      0 :::139                  :::*                    LISTEN     
tcp6       0      0 :::5900                 :::*                    LISTEN     
tcp6       0      0 :::5229                 :::*                    LISTEN     
udp        0      0 0.0.0.0:67              0.0.0.0:*                         
udp        0      0 0.0.0.0:5353            0.0.0.0:*                         
udp        0      0 0.0.0.0:111             0.0.0.0:*                         
udp        0      0 0.0.0.0:58239           0.0.0.0:*                         
udp        0      0 0.0.0.0:137             0.0.0.0:*                         
udp        0      0 0.0.0.0:138             0.0.0.0:*                         
udp        0      0 0.0.0.0:913             0.0.0.0:*                         
udp        0      0 0.0.0.0:44323           0.0.0.0:*

```

---

### Post by FlameLicker on 2010-06-11
... in case you haven't got a solution yet.
Have you ever tried 

   netstat -an --inet ?

Cheers!

---

