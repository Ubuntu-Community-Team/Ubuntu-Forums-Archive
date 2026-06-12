---
title: "Connection problems to internet - IP assigned but no connection to outside"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by ales on 2006-06-08
I have the following problem:

When I start Ubuntu it shows that network adapter is being configured and successfuly. But in system after I start Firefox I can't connect to Internet. Before it worked. I checked tthe Network settings and it shows me that the card and link is online but there is no way out. In 5.10. I used the same HW like now and there wa no problem. I have 2 network cards on  borad one is disabled. It is not important which one is off or on or if both are on, effect is the same. 


What is thep problme.

Thanks for help.

Ales

---

### Post by linuchsan on 2006-06-08
You really have to give more info. Like...is there a router between, is your gateway setup right, dns..etc.

---

### Post by ales on 2006-06-08
yes router. everything in windows works in ubuntu . gateway is always reseted. networking shows and also network tools that eth0 is active, but t will not connect to internet even not to router. after fresh installation it worked , but after installing updates, maybe this is the reason" and rebooting its broken.

---

### Post by linuchsan on 2006-06-08
What does ping 82.211.81.166 say?

---

### Post by Iowan on 2006-06-09
DHCP or static IP (the title suggests DHCP)?
If DHCP. where is it coming from (router?) and is it getting one?
I presume it's Breezy (since that's what forum this is).
I've seen a few threads about gateway's being reassigned - usually ends up being a router setting (though I don't know why an Ubuntu update would change that).

---

### Post by ales on 2006-06-09
dreamwalker@dreamwalker:~$ sudo dhclient
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:13:d4:c2:34:34
Sending on   LPF/eth1/00:13:d4:c2:34:34
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPNAK from 10.0.0.138
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 10.0.0.138
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 10.0.0.138
SIOCADDRT: Network is unreachable
bound to 212.55.250.18 -- renewal in 34241 seconds.
dreamwalker@dreamwalker:~$

dreamwalker@dreamwalker:~$ ping 82.211.81.166
connect: Network is unreachable
dreamwalker@dreamwalker:~$ 


this is what I have got. I use 6.06 dapper drajke. yes DHCP from router

---

### Post by linuchsan on 2006-06-09
What is nic module you have loaded?

---

### Post by ales on 2006-06-14
What is nic module?

---

### Post by Iowan on 2006-06-14
That'd be the driver for your NIC.  Dunno if it'll help, but you might review this thread:
[http://www.ubuntuforums.org/showthread.php?p=1128313#post1128313]("http://www.ubuntuforums.org/showthread.php?p=1128313#post1128313")

It would appear that your router is on 10.0.0.138, but the address 212.55.250.18 got assigned :confused:  Check **ifconfig** to see if that happened.

---

