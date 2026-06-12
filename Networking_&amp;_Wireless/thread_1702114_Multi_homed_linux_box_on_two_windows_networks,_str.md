---
title: "Multi homed linux box on two windows networks, strange netbios issues"
date: 2011-03-07
forum: Networking &amp; Wireless
---

### Post by lance UNI on 2011-03-07
I have two networks, one that is our domain work network sitting on 192.168.20.x.  The other one is our guest network, where we hook up customer machines, and it is running on 192.168.2.x

I wanted to setup a linux box (ubuntu 10.04LTS latest updates) running a common file share between the two networks as i wouldn't have to worry about viruses and such infecting the linux machine, and windows has always had strange issues with multi homing.

everything works fine, i can see the linux share from both networks with no issues whatsoever.

the strange problem is that on my domain computers, under the network list, I can sometimes see netbios computer listings from the OTHER guest network.  I can't access them, or ping them (as i should not be able to, since i want no access between the networks) but they still show up as listings.

can someone point me in the right direction for making those listing go away and properly separating the two networks?

---

