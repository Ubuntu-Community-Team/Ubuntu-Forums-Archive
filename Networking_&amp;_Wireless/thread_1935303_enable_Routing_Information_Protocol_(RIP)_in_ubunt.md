---
title: "enable Routing Information Protocol (RIP) in ubuntu"
date: 2012-03-04
forum: Networking &amp; Wireless
---

### Post by spezticle on 2012-03-04
i had this set up at one point and it worked.
for the life of me, i can not remember how i did it now as i try to replicate this scenario months later.

if i could enable RIP on my ubuntu system it should receive and send out the proper routes to make this work.

here's the topology:

Router R1 is connected to ubuntu system via network 172.16.0.0/30

ubuntu system is connected to a netgear router network 192.168.0.0/28

i have cisco router and netgear router configured for RIP but because ubuntu box is in the middle and the routes aren't configured right, RIP broadcasts aren't reaching the other destinations.
(cisco router f0/0 172.16.0.2 255.255.255.252) =======( ubuntu eth1 172.16.0.1 255.255.255.252) 

(ubuntu eth0 192.168.0.1 255.255.255.240) ==== (netgear router 192.168.0.14 255.255.255.240) ====== ( WAN IP via netgear  65.30.xx.xx)


The ultimate goal is to get cisco router to ping my wan IP
Thanks in advance,

---

### Post by redmk2 on 2012-03-04
> **spezticle said:**
> i had this set up at one point and it worked.
for the life of me, i can not remember how i did it now as i try to replicate this scenario months later.

if i could enable RIP on my ubuntu system it should receive and send out the proper routes to make this work.

here's the topology:

Router R1 is connected to ubuntu system via network 172.16.0.0/30

ubuntu system is connected to a netgear router network 192.168.0.0/28

i have cisco router and netgear router configured for RIP but because ubuntu box is in the middle and the routes aren't configured right, RIP broadcasts aren't reaching the other destinations.
(cisco router f0/0 172.16.0.2 255.255.255.252) =======( ubuntu eth1 172.16.0.1 255.255.255.252) 

(ubuntu eth0 192.168.0.1 255.255.255.240) ==== (netgear router 192.168.0.14 255.255.255.240) ====== ( WAN IP via netgear  65.30.xx.xx)


The ultimate goal is to get cisco router to ping my wan IP
Thanks in advance,

The package you need to add is called *quagga*.  This used to be called *zebra*.  It contains the the daemon *ripd*.  See [**_[COLOR="Blue"]here[/COLOR]_**]("https://www.os3.nl/2008-2009/students/jarno_van_de_moosdijk/inr/week5_rip") for a quick howto.

To monitor the routing protocol you can install the package called *a.s.s* (less the dots (autonomous system scanner)).

---

### Post by spezticle on 2012-03-04
oh thanks a lot. i'll give it a go here later today. thanks for the howto link. and the a.s.s detail, too :)

---

