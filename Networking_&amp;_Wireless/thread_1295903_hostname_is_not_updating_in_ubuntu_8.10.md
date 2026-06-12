---
title: "hostname is not updating in ubuntu 8.10"
date: 2009-10-20
forum: Networking &amp; Wireless
---

### Post by sai438 on 2009-10-20
Hi,

I've Ubuntu 8.10 PC. when i start networking, only IP is getting updated (DHCP) but not hostname. My DHCP server serves both IP-address and Hostname. 

I've Fedora 8 in other PC, I'm able to see the IP and the hostname being updated when i run dhclient.

Can any one please help me on how to make it work?

Thanks in advance,

Sairam

---

### Post by Iowan on 2009-10-20
Check */etc/dhcp3/dhclient.conf* - there should be a line:```
send host-name "<hostname>";
```Change the placeholder <hostname> to your hostname.  Although it might seem logical to have the machine pass it's hostname via system variable, [this]("http://ubuntuforums.org/showthread.php?t=275733") rather old thread suggests otherwise (maybe it's changed since 2006).

---

