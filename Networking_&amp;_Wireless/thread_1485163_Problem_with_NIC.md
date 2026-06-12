---
title: "Problem with NIC"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by liranv on 2010-05-16
Hey Guys
 
When running mii-tool , i get this resault
 
[FONT=Calibri]eth0: negotiated 1000baseT-FD flow-control, link ok[/FONT]
[FONT=Calibri]SIOCGMIIPHY on 'eth1' failed: Resource temporarily unavailable[/FONT]
 
 
[FONT=Calibri]Which is probably preventing me from creating a "Bonding/Teaming" .[/FONT]
 
[FONT=Calibri]1) can any one help me solve this problem[/FONT]
[FONT=Calibri]2) can any one send me a simple link which describes how to create a "teaming" with these 2 interfaces ?[/FONT]
 
 
[FONT=Calibri]Thanks a lot [/FONT]

---

### Post by Iowan on 2010-05-16
[Here]("http://www.cyberciti.biz/tips/linux-bond-or-team-multiple-network-interfaces-nic-into-single-interface.html") is one article I found (haven't read, though.
[This]("https://help.ubuntu.com/community/UbuntuBonding") one is on **bonding**.

---

### Post by liranv on 2010-05-16
Thank you . 
 
What about the second issue ?  the error i get when running wii-tool ?

---

### Post by red wagon on 2012-09-10
> **liranv said:**
> Thank you . 
 
What about the second issue ?  the error i get when running wii-tool ?

Same issue here.  I was running 10.04, upgraded to 12.04 and now bonding is failing because of this error.  Any new information related to resolving this issue?

root@host1:/etc/network# mii-tool 
eth0: 100 Mbit, full duplex, link ok
SIOCGMIIPHY on 'eth1' failed: Resource temporarily unavailable

---

### Post by Iowan on 2012-09-10
From the Code of Conduct:
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

