---
title: "wired networking issue"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by Greensystemsgo on 2010-01-16
Says connection is active, however 192.168.1.1 brings me instead of my router, my switch. The computer in question is physically plugged into the 4 port router. Installed 8.10, had this problem, installed 9.10 and same issue.  Motherboard is a HP OEM part #404794-001, with a broadcom gigabit connection. Dont know how to get much more info, im not to great at linux. XD


edit: playin around with ipv4/ipv6 settings i was able to connect to my router, a wrt54gs v7 running dd-wrt, however no internet.

---

### Post by Pie to the max on 2010-01-16
he me to its says its active but nothing works. have you tried pinging a website?

---

### Post by Greensystemsgo on 2010-01-17
> **Pie to the max said:**
> he me to its says its active but nothing works. have you tried pinging a website?

I attempted 
> dig AAAA [www.kame.net](www.kame.net)
Did it time out? Then try this one:

dig A [www.kame.net](www.kame.net)
Did the latter work? Then it is indeed, an issue with ipv6 and you have a few options here from [http://www.lockergnome.com/linux/2007/10/24/ubuntu-gutsy-internet-help/](http://www.lockergnome.com/linux/2007/10/24/ubuntu-gutsy-internet-help/)

and both just time out :/ with all auto settings im taken to switch config panel, with tweaked auto dhcp address i managed to get my router admin panel, once.

---

### Post by Iowan on 2010-01-17
What kind of switch?

---

### Post by Greensystemsgo on 2010-01-17
the switch is a 4port linksys router, however it is in switch mode as the wan port is unused.

The router is a wirt54gs v7 runnin dd-wrt 12548

---

### Post by Iowan on 2010-01-17
Thanks - I was curious about a switch with IP address. Are the switch and router configured for the same (default) address? Which one of them providing is DHCP?

---

### Post by Greensystemsgo on 2010-01-18
> **Iowan said:**
> Thanks - I was curious about a switch with IP address. Are the switch and router configured for the same (default) address? Which one of them providing is DHCP?

the router.

modem>>wrt54gs wifi router which provides DHCP>>4port +1 WAN port router, in switch mode, also with DHCP OFF.

---

