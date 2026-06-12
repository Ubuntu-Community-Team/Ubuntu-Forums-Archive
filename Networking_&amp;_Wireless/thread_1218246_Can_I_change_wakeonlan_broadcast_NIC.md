---
title: "Can I change wakeonlan broadcast NIC?"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by _UsUrPeR_ on 2009-07-20
Hey all. I am running an ltsp setup with Ubuntu 9.04, and would like to use WakeOnLan to start my clients.

My system is hosting the LTSP clients on ETH0, while ETH1 is serving DHCP and is connected to all the thinclients on a separate wired network.

I can't seem to get wakeonlan to broadcast from eth1. It only broadcasts from eth0. Can someone point me towards getting this working right?

---

### Post by martinbaselier on 2009-07-20
Have you tried using the broadcast address of your subnet? 

**man wakeonlan** shows this:
wakeonlan -i ip_address

Destination IP address. Unless you have static ARP tables you should use some kind of broadcast address (the broadcast address of the network where the computer resides or the limited broadcast address). Default: 255.255.255.255 (the limited broadcast address).

What happens when you turn off eth0?
**sudo ifconfig eth0 down**

---

### Post by _UsUrPeR_ on 2009-07-20
Woop! Got it!

```
wakeonlan -i 192.168.0.255 <mac address>
```

I just had to specify the subnet on the NIC, and it put the magic packets out on the proper card.

---

