---
title: "few questions about wireless router"
date: 2009-03-06
forum: Networking &amp; Wireless
---

### Post by montamer on 2009-03-06
Hi
Im planning to get a wireless router. I have a psp which i want to connect to internet.
Im not connected to internet directly, My ip is assigned by a dhcp server in my institute (my ip is like 10.94,9.10). and im behind a proxy server.(say 10.65.4.1:3128).

My questions are:
1) As the cable from my ethernet port goes to router and from router to my pc.  Do i need a extra wireless adaptor for my pc to access net? and what ip will i get? 
2) will i be able to access other pcs connected in my local network? like 10.94.0.1, 10.94.0.2 etc .......
3) netgear, dlink, belkin, linksys routers are available in my local stores. Which one is best supported in linux?
4) as im behind a proxy will that be any problem?
5) do i need any aditional drivers? and if so are these drivers can be compiled for other architecture like arm?

Sorry for asking so many questions :D ....... im a complete noob with wireless. watched few videos in youtube but can't clarify these questions

Thanx

---

### Post by jflaker on 2009-03-06
See bolded answers below

Hi
Im planning to get a wireless router. I have a psp which i want to connect to internet.
Im not connected to internet directly, My ip is assigned by a dhcp server in my institute (my ip is like 10.94,9.10). and im behind a proxy server.(say 10.65.4.1:3128).

My questions are:
1) As the cable from my ethernet port goes to router and from router to my pc.  Do i need a extra wireless adaptor for my pc to access net? and what ip will i get? 
**Your IP will be a nat'd ip, likely 192.168.1.1**

2) will i be able to access other pcs connected in my local network? like 10.94.0.1, 10.94.0.2 etc .......
**Only those locally connected to YOUR router**

3) netgear, dlink, belkin, linksys routers are available in my local stores. Which one is best supported in linux?
**Routers are transparent and I have never heard of one router not supporting Linux.  I use Linksys and have also connected to a netgear router.....**

4) as im behind a proxy will that be any problem?
If the campus DHCP server assigns the information, you should be fine.  [B]If you needed to add proxy information provided by your campus, you will need to add that to your system, not the router
[/B]
5) do i need any aditional drivers? and if so are these drivers can be compiled for other architecture like arm?
[B]Your network adapter and the router are separate entities.  Again, routers are NOT dependent on any type of OS driver software.

[/B]
Sorry for asking so many questions :D ....... im a complete noob with wireless. watched few videos in youtube but can't clarify these questions

Thanx

---

### Post by montamer on 2009-03-08
thanx for the reply ..... that helped alot

---

