---
title: "Sniffing."
date: 2010-08-04
forum: Networking &amp; Wireless
---

### Post by knob2001 on 2010-08-04
Hi.

Before the problem, the concept about what i'm trying to do:

Connect two different machines to a PC with two different NICs (eth0 and eth1) as if the PC was a router, so i can sniff what is happening between the two machines. 

The machines are not PC's, and thus, i don't require to bridge or share any Internet between them. Just connect one to a nic, the other to the second nic, and let them begin to talk.

So, my problems are: first, very noob about networking stuff, and second, i really need some light to my concepts.

I'm using the webmin frontend.

My first thoughts:
1. First nic: eth0 configured as 192.168.1.1 / 255.255.255.0
2. Second nic: eth1 configured as 192.168.2.1 / 255.255.255.0
3. Machine 1: 192.168.1.2 / 255.255.255.0 / gw 192.168.1.1
4. Machine 2: 192.168.2.2 / 255.255.255.0 / gw 192.168.2.1
5.... no idea the routing table to let both speak each other.

I don't need any dchp server, btw. And from the PC i can see both machines... but between them there's no way to call the other one.

Could someone throw some light to my concepts? the more i read the more i'm messing the whole thing.

Regards.
knob2001

---

