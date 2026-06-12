---
title: "eth0 keeps old ip information alive"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by SMADdie86 on 2009-02-17
I have xubuntu hardy running for a long time.
Now after that I used my laptop (dual core 2 ghz) to install a new xDSL router at my neighboor, the blooming linux keeps the IP info of my neighboor alive.
In other words:
my own network is on 192.168.1.xxx and sn 255.255.255.0
my neighboor has 192.168.1.xxx at 255.255.255.1

disabling networking
renewing the IP
restarting the laptop with networking disabled.
using dhclient or sudo dhclient
ifconfig eth down and up
and some 3 other ideas
they didnt work.
I also tried to give linux a static IP, but with the info entered it didnt want to go on internet.
the dhclient gave me info het got a new IP and displayed it ok.
But internet no way, restarted and he was again on the old IP.

Where could i find a kind of cache in linux where i can clear the ip info?

Im using linux more then windows but some things still unfolds he he.

---

### Post by SMADdie86 on 2009-02-18
No one here that can help me?
Friday i will be leaving abroad for my work and i want to use my laptop there without any problems.

Ciao

---

### Post by Iowan on 2009-02-18
Dunno if Xubuntu uses Network Manager... Otherwise, you might see what's saved in /etc/network/interfaces. From what I've read, Network Manager saves its settings in /etc/NetworkManager (might be spelled/capitalized differently).

Hope your machine isn't connecting to your neighbor's network and refreshing it's old address from there.

---

### Post by SMADdie86 on 2009-02-19
Ill check it out after im back from a course he he.
No its not possible that it gets his ip from my neighboor.
Cause at home i used wired network and under windows (dual boot) internet does work with the right ip.

---

