---
title: "Failing to acquire proper network address"
date: 2009-03-08
forum: Networking &amp; Wireless
---

### Post by NexusV2 on 2009-03-08
Hey guys,
I have just installed Kubuntu and I'm just trying to get it to connect to the internet, but for some reason it wont.

It starts up and find the ethernet adapter and gives it the following:
**IP:** 192.168.2.111
**Subnet mask:** 255.255.255.0 (obv)
**Broadcast:** 192.168.2.255

When I go to the "Statistics" tab it shows that I have sent and received packets, yet I cannot browse the internet...any help?

Thanks

---

### Post by Iowan on 2009-03-08
I presume you're getting DHCP address?  Does */etc/resolv.conf* have valid DNS nameserver address?  (My system has the address of the modem here.)

---

