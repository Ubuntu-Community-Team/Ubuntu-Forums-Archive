---
title: "Unable to connect to internet"
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by krishna_akella on 2009-01-25
Hello,
I have installed ubuntu recently. Not able to connect to internet using either wired or wireless network. 

I am having dual boot option with vista and ubuntu on my hp laptop. 
Referred to the documentation. if config gives the following details for eth0
inet addr 192.168.1.100
Bcast 192.168.1.255
Tried pinging 91.189.94.249 - 100% successful packets.
Tried pinging ubuntu.com - Message says "Ubuntu.com can not be found"
Firefox can not open any webpage (tried google.com)
In the network settings, wired connection properties show that configuration is "Automatic Configuration (DHCP)"
Network is enabled.
I have connected another laptop using xp to the same router using wire. I can use internet with out any problem and using the same coonetion to use this forum.

Please help.

---

### Post by Iowan on 2009-01-25
It'll ping by IP address, but not hostname... sounds like DNS.  What's in /etc/resolv.conf.  If It doesn't contain your DNS server (or router), you may need to modify the /etc/dhcp3/dhclient.conf file to use the "prepend" line.

---

### Post by C J on 2009-01-25
> **Iowan said:**
> It'll ping by IP address, but not hostname... sounds like DNS.  What's in /etc/resolv.conf.  If It doesn't contain your DNS server (or router), you may need to modify the /etc/dhcp3/dhclient.conf file to use the "prepend" line.


(sorry to mind with this thread but it might help me solve my problem)

so i have to add these lines?

prepend 208.67.222.222
prepend 208.67.220.220

(if 208.67.222.222 is my 1st and 208.67.220.220 is my 2nd DNS??)

---

### Post by Iowan on 2009-01-25
[This]("http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html") article explains it better, but in brief```
prepend domain-name-servers 208.67.222.222,208.67.220.220;
```

---

