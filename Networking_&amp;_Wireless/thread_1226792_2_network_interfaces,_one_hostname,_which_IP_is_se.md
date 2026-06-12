---
title: "2 network interfaces, one hostname, which IP is selected?"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by UranUtan on 2009-07-29
Hi,

Using Ubuntu 9.04. I have two network interfaces:
- wired, eth0, static IP: 192.168.1.11
- wireless, wlan0, dynamic IP: 192.168.1.119

Within the same machine, if I ping itself by its hostname:
> ping MyMachineName.local
PING MyMachineName.local (192.168.1.119) 56(84) bytes of data.
64 bytes from MyMachineName.local (192.168.1.119): icmp_seq=1 ttl=64 time=0.022 ms
etc...


NOTE: .local is a suffix set in the router

[COLOR="Red"]Question 1[/COLOR]: what is the rule which determine which IP to use when a machine is referenced by name?

[COLOR="Red"]Question 2[/COLOR]: How do I force the IP of eth0 to be used?

Thanks in advance for any help.

---

### Post by superprash2003 on 2009-07-30
i think this would help [http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/](http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/)

---

