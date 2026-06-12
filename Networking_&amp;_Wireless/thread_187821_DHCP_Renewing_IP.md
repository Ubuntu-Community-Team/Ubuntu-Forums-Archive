---
title: "DHCP Renewing IP?"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by dejay703 on 2006-06-03
I'm completely new to ubuntu.  I'm having trouble getting my internet working.  It seems like I am connected to my router, but I'm not getting an ip from it.  My router shows that my network device is connected, but it doesn't have any information of the ip or device name.

I'm guessing (??) that all I might have to do is like an "ipconfig /renew", but I don't even know how to do something like that on ubuntu.

Any ideas on how to fix this or how to identify the problem better?  Thanks!

---

### Post by linj on 2006-07-14
The closest I can figure is 

```
sudo ifdown eth0; sudo ifup eth0
```

Anyone have a one line command? I'd assume there'd be since I think this completely shuts down the eth0... (oh, and, replace eth0 with whatever your alias is).

---

### Post by MrHorus on 2006-07-14
> **linj said:**
> 
Anyone have a one line command? 

```
dhclient ethx
``` 

Where 'x' is the ethernet interface you wish to get a DHCP address for (usually eth0).

Running dhclient by itself will sent out DHCPREQUEST packets on all interfaes by default, just so you know.

---

### Post by mips on 2006-07-14
What lan card do you have ?
Tried disabling IPv6 ?

---

