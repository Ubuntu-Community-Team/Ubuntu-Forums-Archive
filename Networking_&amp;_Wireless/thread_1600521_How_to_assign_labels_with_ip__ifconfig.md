---
title: "How to assign labels with ip / ifconfig"
date: 2010-10-19
forum: Networking &amp; Wireless
---

### Post by hgerstung on 2010-10-19
Hi!

I am trying to manually set up a number of static IPv6 addresses to one of the physical network interfaces on my 8.04server box.

I tried to use the "ip" utility like that:
./ip addr add [myIPv6addr] dev eth0 label eth0:0

which was accepted by ip (no errors) and the IP address was correctly assigned to eth0. But using "ip addr show" I do not see any reference to the label I defined and "ip addr show dev eth0 label eth0:0" does not come back with anything (empty output). 

This seems to contradict the information I found on the ip manpage and I wonder if this is a bug or a misconfiguration on my side. 

Did anyone successfully used the label functionality with ip?

Regards,
  Heiko

---

### Post by SeijiSensei on 2010-10-19
I just use the standard ifconfig command for this task:

```
ifconfig eth0:0 192.168.1.33
```

after the initial assignment for eth0 has taken place.  It uses the same netmask and broadcast address by default.

Just typing "ifconfig" should list all the interfaces on your machine.

---

