---
title: "Port Forwarding"
date: 2011-02-12
forum: Networking &amp; Wireless
---

### Post by diablo69er on 2011-02-12
Here is my setup.  I originally had the Att Uverse 2wire modem/router combo.  I took that and turned it into just the modem.  I plugged my buffalo router into port 1 of the 2wire, and then connected that to my wan port on my buffalo router.  In the 2wire config page I set DMZ to my new router.

Now that that's out of the way here is the problem.  I cannot forward ports.

I forwarded my ports correctly first in the router:

torrent 51413 both 192.168.2.147 enable

And in the iptables:

 root@DarkAbyss:~# iptables --list
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:51413 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Here's where the problem kicks in:

PORT      STATE    SERVICE
53/tcp    open     domain
443/tcp   open     https
51413/tcp filtered unknown


Any ideas on how I can forward this?  I'm about at whits end with ATT

---

