---
title: "Looking for router software"
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by newbuntuxx on 2008-12-23
Greetings..

Just got a Pentium 3, 800 Mhz , 348 ram, 20 Gigs PC (from the trash!). the motherboard has 4 PCI slots with two old old slots (the long black ones, i dont know the name). Anyways, I have a stack of old and new NIC cards which I installed on the motherboard.

After hours of searching for a router software, I downloaded smoothwall express 3.0. The installation and the configuration were really easy. I was on the net in no time, however, I discovered that it is really a firewall, and not a router software (that is, it connects your network to the internet, it does NOT network your computers :( ).

That's why I am here: Do you guys know of any free router software that I can use to turn that old pc into a 7 port router?

Or better yet, can I use ubuntu-server, modify to route the connections?

any help is appreciated 

(you may ask why i am doing this: its because my link sys has only four ports, and I need more)

---

### Post by albinootje on 2008-12-23
> **newbuntuxx said:**
> 
That's why I am here: Do you guys know of any free router software that I can use to turn that old pc into a 7 port router?

Smoothwall should be able to supply your computers in the LAN with internet.
But you can also take a look at [http://m0n0.ch/wall/](http://m0n0.ch/wall/)
That can run from hard disk or cdrom.
> 
Or better yet, can I use ubuntu-server, modify to route the connections?

Yes, you can (with iptables).
> 
(you may ask why i am doing this: its because my link sys has only four ports, and I need more)
You can also buy a 8 or 16 port switch and use 1 linksys port for adding that switch.

---

### Post by jimmy the saint on 2008-12-23
[http://en.wikipedia.org/wiki/List_of_Linux_router_or_firewall_distributions](http://en.wikipedia.org/wiki/List_of_Linux_router_or_firewall_distributions)
Here is a good starting place for router distros.  Alternatively, the addition of a switch would easily solve your problems.  You can get them off ebay pretty cheap or try newegg or geeks.com.  Honestly, unless it is for learning/hobby purposes, I think that letting the linksys handle all of that is the way to go.  Less time setting up and maintaining your network = more time to enjoy your network.

---

### Post by newbuntuxx on 2008-12-23
> Yes, you can (with iptables).

Could you please direct me to a useful how-to, if there is any. 

> You can also buy a 8 or 16 port switch and use 1 linksys port for adding that switch. 

i am doing it for learning purposes, and to use what I have. If I miserably fail, I will eventually buy a switch. :) 


Thanks

---

### Post by albinootje on 2008-12-23
> **newbuntuxx said:**
> Could you please direct me to a useful how-to, if there is any. 
i am doing it for learning purposes, and to use what I have. If I miserably fail, I will eventually buy a switch. :) 

[http://tldp.org/HOWTO/html_single/Masquerading-Simple-HOWTO/](http://tldp.org/HOWTO/html_single/Masquerading-Simple-HOWTO/)
Have fun :)

---

