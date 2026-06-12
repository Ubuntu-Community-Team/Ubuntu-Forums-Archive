---
title: "Large PING delay to router"
date: 2005-12-08
forum: Networking &amp; Wireless
---

### Post by PhilOSparta on 2005-12-08
I have two PCs using Ubuntu.  Love it, but I just loaded the second, an AMD64 with the i386 kernel.   I made changes for a double clock problem per another thread:
[http://ubuntuforums.org/showthread.php?t=53094&highlight=double+clock](http://ubuntuforums.org/showthread.php?t=53094&highlight=double+clock)
That's when internet access degraded and long ping times to my router started.
Internet access is very slow.  Ping to router output is:

--- 10.10.10.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3999ms
rtt min/avg/max/mdev = 237.490/695.471/1335.531/502.884 ms, pipe 2

My other PC connected to the same router is .9 ms average.

Does anyone have any ideas on this?  It seems that since the clock was changed, the network timing has been changed.

FIXED:  Everything works perfectly in Dapper.  5-6-2006

---

