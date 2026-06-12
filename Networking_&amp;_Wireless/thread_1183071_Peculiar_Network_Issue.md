---
title: "Peculiar Network Issue"
date: 2009-06-09
forum: Networking &amp; Wireless
---

### Post by azaraelishanti on 2009-06-09
I have recently installed Ubuntu 9.04 onto an old Dell machine to use a local weberver for a small business I work with. I've set servers running Ubuntu up before, so I'm having an issue figuring out what the problem is this time around.

I have installed Apache, MySQL, PHP5, phpmyadmin (all we need for the webserver) and have reserved the computer's address in the router as 10.0.0.100

Now, I went to the Port Forwarding in the Netgear RangeMAX WNR834B v2 and forwarded all traffic on ports 80 and 21 to 10.0.0.100 (which, running ifconfig, is the local IP address). The DHCP lists the server as 10.0.0.100, etc etc. But no traffic is getting through the router at all.

In desperation, I was going to use the DMZ function, but I can't find that either. Is it something to do with the router? Or is it Bellsouth (I believe it's on Bellsouth Business 6.0 Extreme) and I have run a server on Bellsouth before with no Port 80 problems.

The webserver software is running, because I can access it via FTP and browser from other computers on the network with no issues.

Any help would be appreciated. :)

-Az

---

### Post by DGortze380 on 2009-06-09
Check any firewalls

---

### Post by superprash2003 on 2009-06-10
use this online port scanner to see if ports are open [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)

---

