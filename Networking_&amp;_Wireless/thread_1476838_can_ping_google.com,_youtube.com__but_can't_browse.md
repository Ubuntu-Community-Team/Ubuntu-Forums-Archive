---
title: "can ping google.com, youtube.com  but can't browse."
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by ateap0tist on 2010-05-08
Hey guys! I have this problem, I searched the forum but couldn't find a solution so i thought i'd ask in a new post.
Every now and then i can't browse the google sites. I can ping them but can't browse. It first happened in Chromium so i uninstalled thinking that it may be the browser. But i get the same problem in firefox and chrome. The problem is intermittent but when i can't browse these sites from ubuntu I can from windows (i only have ubuntu on this system but my gf has windows 7 on her netbook and she connects to the same wireless connection). So it's not that servers are busy or something. Also I can browse other sites like (ubuntuforums.org works! :) ). AFAIK it's just google sites i have problems browsing. 
I'm using a Dell Inspiron 1525 and i connect through a wireless router. My system is running Ubuntu 10.04
```
--- www.l.google.com ping statistics ---
123 packets transmitted, 123 received, 0% packet loss, time 122170ms
rtt min/avg/max/mdev = 8.810/12.625/97.470/10.647 ms

```The error from firefox is:
The connection has timed out
The server at [www.google.com]("http://www.google.com") is taking too long to respond.
    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.
    *   If you are unable to load any pages, check your computer's network
          connection.
    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.

I did disable IPv6, didn't help.
I am relatively new to gnu linux so please tell me if i should offer more information about my system.

---

### Post by Iowan on 2010-05-08
Probably not the solution, but you can check [MTU]("http://ubuntuforums.org/showthread.php?t=1376506"). (post 15 or 16).

---

