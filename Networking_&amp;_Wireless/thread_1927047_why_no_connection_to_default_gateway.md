---
title: "why no connection to default gateway"
date: 2012-02-17
forum: Networking &amp; Wireless
---

### Post by scampsd on 2012-02-17
Good afternoon,
I am working on an HP server using Ubuntu.
In the file "/etc/network/interfaces" there is the definition of eth0, similar to the following:
iface eth0 inet static
address xxx.xxx.xxx.xxx
netmask 255.255.255.0
gateway AAA.BBB.CCC.1
 
All of this information is correct.
 
When I do a "ifconfig -a", all information seems to be correct (and the interface is mentioned as "UP").
However when I do a "ping AAA.BBB.CCC.1", the result is NOK.
 
Does anybody have an idea where I need to look for solving this issue? (are there other files that need to be modified in order to ping a default gateway?)
 
Thanks
Dominique

---

### Post by SeijiSensei on 2012-02-17
> **scampsd said:**
> 
address xxx.xxx.xxx.xxx
netmask 255.255.255.0
gateway AAA.BBB.CCC.1

Is the gateway address in the same subnet as the ethernet adapter?  A machine in 10.1.1.0/24 can only reach a default gateway with an address like 10.1.1.1.

In other words "AAA.BBB.CCC" has to be the same as the first three octets in "xxx.xxx.xxx.xxx" if you have a 255.255.255.0 netmask.

If you run the command "route -n" what do you get in response?  (If you post the response please put it in [noparse]```

```[/noparse] tags.)

---

### Post by iponeverything on 2012-02-17
After a ping attempt, See if the default has an entry in the ARP table.

```
cat /proc/net/arp 
```

---

### Post by jonobr on 2012-02-17
ICMP (ping) could be blocked from the router?

---

