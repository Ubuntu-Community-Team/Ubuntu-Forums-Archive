---
title: "Proxy setting did not allow to connect to server"
date: 2011-02-12
forum: Networking &amp; Wireless
---

### Post by stanwang on 2011-02-12
Here is the help that I need with out-most urgency:
I used windows OS  and installed Ubuntu 10.04 (amd64) in separate partition and works well  but had a problem in internet connectivity.
Likely reason may be the  proxy setting that we used in college (currently). I used this commands  to set up the IP address and gateway.
ifconfig -a | grep eth

"eth0"

sudo ifconfig eth0 192.168.5.209 netmask 255.255.255.0

ifconfig eth0

sudo route add default gw 192.168.5.1 eth0

sudo ifup eth0

Then  I manually set the proxy setting of HTTP which is given as proxy server  192.168.5.2 and port as 8000, further more there is a wins setting  which is 192.168.1.178, really don't know where to put this number. 
Please HELP

---

### Post by klxy on 2011-02-12
192.168.5.1 ?  192.168.5.2 ?

---

### Post by stanwang on 2011-02-12
> **klxy said:**
> 192.168.5.1 ?  192.168.5.2 ?
that was an awesome finding, sorry I had missed out 1, that is 192.168.15.2 that's the proxy address

---

