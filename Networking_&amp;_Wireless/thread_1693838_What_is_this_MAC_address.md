---
title: "What is this MAC address?"
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by zozza on 2011-02-23
Arp -a shows:

resident1421.domainname.lon.ac.uk (123.83.151.149) at 00:0b:42:65:1f:8f [ether] on wlan0

The MAC address is not my network card nor is it my access point as revealed through iwconfig.

So what might it be?  Thanks!

---

### Post by thesavager on 2011-02-23
Since you are using wireless network .... it could be a hacker ... what kind of security you are using on your wireless lan ? WEP or WPA/WPA2 ?

Ip-adress and hardware adress could be a faked one !

---

### Post by TuxIsAwesome on 2011-02-23
I'm no security expert (yet...)

But if I were you, I'd find a way quickly to blacklist/Block that MAC address based on that website on your router. 

50/50 percent chance it's a hacker.

---

### Post by An Sanct on 2011-02-23
Well, the IP lookup states, it is from a chinese IP range, but everything is possible...

---

### Post by thesavager on 2011-02-23
> **An Sanct said:**
> Well, the IP lookup states, it is from a chinese IP range, but everything is possible...

Since zozza is talking about a wireless network ... I don't think a chinese guy can enter that router wireless from China ... better impossible :) ,  so this must be a faked MAC-adress and faked ip-adress.

An IP lookup doesn't mean anything in this case!

---

### Post by zozza on 2011-02-24
OK, my mistake. 

route -n shows the IP is my gateway.  Therefore presumably the MAC is the gateway MAC.

Thanks!

---

### Post by An Sanct on 2011-02-24
Thats a strange IP ... According to [RFC 3330]("http://tools.ietf.org/html/rfc3330") (special use IP [V4] addresses), that also includes local IPs, 123 is nowhere to be found, nor in the private IP address space.

[edit]Still a strange IP :)[edit]

PS. Got warned for my post here ... that's a bummer, just trying to help and I get whacked on my fingers (for being a bad boy, they tell me ...)

---

