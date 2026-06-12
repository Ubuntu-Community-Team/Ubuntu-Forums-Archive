---
title: "Linksys WAG200G and TP-Link TL-WA500G"
date: 2010-01-25
forum: Networking &amp; Wireless
---

### Post by gawynus on 2010-01-25
Hi
I have a following problem:
I have wireless router Linksys WAG200G - great signal, no problems.
Lately I have bought Access Point Tp Link TL-WA500G and I want to use it in a client mode on second computer. But first I wanted to test it on laptop where I used wifi from this router without problem to make an initial setup of AP.
The problem is:
I have no net through the ETH.
On router (IP 192.168.1.1) there is DHCP set, giving adressess and it gave dynamically IP 192.168.1.19 to the AP (before that AP had static IP but I after many trials I decided that it would be best if router gave it IP. Am I wrong? Unfortunately on computer attached to AP I have no IP from DHCP from router so I gave him static 192.168.1.100.
From this client computer I can ping both router and AP so there is connection router-AP.
I thought that it might have been problem of DNS, but when I tried to ping some other IP in the internet it didn't work and I got "no connection" info so it seems I reach the router and stop there.
Thanks in advance
Gawynus

---

### Post by chili555 on 2010-01-25
> I gave him static 192.168.1.100.Did you also give him DNS nameservers? When you set a static IP address, the computer will not be able to get DNS nameservers by DHCP. It is therefor your job to add them manually. The quick and easy way is to amend */etc/resolv.conf* and add the address of the router:```
nameserver 192.168.1.1
```

---

### Post by gawynus on 2010-01-25
Huge thanks Chili :)
So simple and I didn't figure it out before
Greetings :D

---

