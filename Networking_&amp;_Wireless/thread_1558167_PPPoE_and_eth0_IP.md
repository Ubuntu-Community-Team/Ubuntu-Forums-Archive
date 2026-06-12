---
title: "PPPoE and eth0 IP"
date: 2010-08-21
forum: Networking &amp; Wireless
---

### Post by niallm90 on 2010-08-21
Hi,
I just started using PPPoE on my ubuntu desktop and I also want to have network access. The problem is when I click on the PPPoE connection it remove IP addresses from my eth0 adapter. I want both as I still use the network. I did find that if I run "sudo dhclient" that it will get an ip on eth0 for me but this is not ideal to do every time I launch the PPPoE connection.

Thanks,
Niall

Edit:
I have found that by putting "ifconfig eth0 192.168.1.201 netmask 255.255.255.0" in /etc/ppp/ip-up fixed the problem. I'm however not sure if this is a hackish way of doing it.

Thanks again,
Niall

---

