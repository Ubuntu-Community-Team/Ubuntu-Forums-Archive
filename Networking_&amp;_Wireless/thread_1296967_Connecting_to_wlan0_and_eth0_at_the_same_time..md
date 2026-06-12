---
title: "Connecting to wlan0 and eth0 at the same time."
date: 2009-10-21
forum: Networking &amp; Wireless
---

### Post by StarChaser93 on 2009-10-21
Hi guys,


I have recently gotten a Windows machine and wish to access the internet on it, but, I have a bit of a conundrum.


I am currently across the other side of the house to the router, I am accessing it with wifi on wlan0 with my laptop.
The Windows Machine is right next to the laptop and they can communicate with one another and the wifi has been working for nearly 12 months.

My problem is, both connections don't seem to want to be on at the same time.


My current setup is:

Modem -> Wifi router -> Ubuntu Machine -> Network Switch -> Windows Machine


The network switch is because I don't have a a crossover cable long enough for them to reach each other. 
I don't think the switch is the problem but I thought I should mention it just in case.

I am also using wicd since network-manager didn't seem to think eth0 even existed.


I think I can get the internet sharing working with Firestarter but first I need both connections to connect at the same time.


Anyone have a rough idea of what the problem may be?


Thanks in advance.

~SC

---

### Post by Iowan on 2009-10-21
Network Manager will only manage one interface at a time.  This works fine if you want to use either wireless OR wired, but not both.  To use both, one will need to be set up in */etc/network/interfaces*. 
Dunno if **wicd** has the same limitations...

---

