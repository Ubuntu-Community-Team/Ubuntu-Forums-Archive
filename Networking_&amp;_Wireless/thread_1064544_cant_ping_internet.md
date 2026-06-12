---
title: "cant ping internet"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by kinalas on 2009-02-08
greetings!

just installed ubuntu server, (new user)

on my eth0 i used:

address 202.138.184.115
netmask 255.255.255.248
network 202.138.184.0
gateway 202.138.184.113
broadcast 202.138.255
dns-nameservers 202.138.128.54 202.138.128.50


my prob is:
i can ping my ip, gateway, dns.. .but if it try to ping internet name address ex: ping yahoo.com, ping google.com it gives me unknown host error.. help

---

### Post by punx45 on 2009-02-09
are you connected directly to your isp or do you have a router?

does your ISP usually grant dynamic IP addresses, and did you set these as static?

---

### Post by kinalas on 2009-02-09
connected directly from my modem to ethernet card

not sure on my network/broadcast address coz i dont set it up on windows pcs.

or can i just connect it to my router than have 192.168.0.x address

im planning to make my ubuntu server a proxy server

---

### Post by punx45 on 2009-02-09
yeah, most ISPs assign dynamic IPs, so unless you specifically requested a static IP, setting it yourself will probably break things.   you should either let it auto configure, or put it behind your router.

---

### Post by Iowan on 2009-02-09
> **kinalas said:**
> address 202.138.184.115
netmask 255.255.255.248
network 202.138.184.0
gateway 202.138.184.113
broadcast [COLOR="Red"]202.138.255[/COLOR]
dns-nameservers 202.138.128.54 202.138.128.50
 I presume this was just a typo?  Can you ping by address (eg. 209.85.171.100)?  Might not mean much - this machine won't ping that address, but works.

---

