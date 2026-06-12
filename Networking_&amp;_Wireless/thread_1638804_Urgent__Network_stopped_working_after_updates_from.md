---
title: "Urgent:  Network stopped working after updates from Dec. 3, 2010,  Version: 10.4 LTS"
date: 2010-12-06
forum: Networking &amp; Wireless
---

### Post by phen on 2010-12-06
Hello all,

Friday I installed all updates from the repositories for 10.4. There were several network-related packages like bind9-host, dnsutils, etc. 

When I booted the machine this morning, it wasn't able to connect to our network (its a university network with IP adresses accessible from the outside (not a 192.168.0.x network). I use DHCP from within network-manager.

My laptop didn't connect either, but it's OS is exactly the same, network card is the same ,too. Its either Ubuntu or our network, but all other collegues haven't had any problems with their OSes.

I found a thread dealing with the same behaviour, but it doesn't help:
[http://ubuntuforums.org/showthread.php?t=1552120](http://ubuntuforums.org/showthread.php?t=1552120)

Thanks for help, this is kind of urgent as it is my work pc.


Relevant dmesg output:
---------------------------------
[ 8368.185073] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[ 8368.185620] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 8378.684046] eth0: no IPv6 routers present
---------------------------------

---

### Post by dineshs on 2010-12-06
Can you post the resut of```
ifconfig -a
```

---

### Post by phen on 2010-12-06
Sorry for bothering you, suddenly admins running over the corridor caught my attention. there is a problem that affects only some network ports, thats why my collegues had no problems.

thank you anyway..

personal counter for problems caused by updates minus 1, back to 0 :-)

---

