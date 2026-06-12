---
title: "Connected but cannot browse"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by kharat on 2009-08-31
I am able to connect to internet, but not able to browse at my camp residence. The following information is displayed by the network manager after connection.

Connection name     Enjoy
IP Address          192.168.254.109
Broadcast Address   192.168.254.255
Subnet Mask         255.255.255.0
Default route       192.168.254.100
Primary DNS         192.168.254.100
Secondary DNS       192.168.254.100
Hardware Address    01:1C:F0:A3:D5:65

I could ping to default router, but average round trip time was high > 2 sec. 
FF is unable to connect. Where & which setting in FF should I specify.

But in other wireless networks I am able to connect and browse also. 

TIA,
Vikas

---

### Post by mechdave on 2009-08-31
Make sure your router is configured properly to pass on the external DNS to your machine. One way to test is to change the primary and secondary DNS to the ip addresses that your ISP has. This will bypass your router and possibly make your connection faster

---

