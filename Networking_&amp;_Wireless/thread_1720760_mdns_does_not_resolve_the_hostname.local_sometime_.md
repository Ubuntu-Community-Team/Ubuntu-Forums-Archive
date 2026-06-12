---
title: "mdns does not resolve the hostname.local sometime after reboot"
date: 2011-04-03
forum: Networking &amp; Wireless
---

### Post by crazy.nattu on 2011-04-03
Hi I am having 3 systems on my lan
1. hostname : phoenix
 $ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

2. hostname : matrix

 $ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"

3. hostname : jinx
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

when I restart phoenix
then ping phoenix.local and ping jinx.local works from matrix
and also ping matrix.local and ping jinx.local works from phoenix

but **after sometime** ping phoenix.local stops working from matrix and also from jinx also
Error:
ping: unknown host phoenix.local

and ping matrix.local or ping jinx.local also stops working from phoenix

but I can still ping jinx.local from matrix.

this means something is wrong with phoenix.

the contents of all the three system for /etc/nsswitch.conf has

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

---

### Post by I-love-maverick on 2011-11-04
Same here! My Win XP is not able to resolve hostname.local now! It was working until yesterday!

---

