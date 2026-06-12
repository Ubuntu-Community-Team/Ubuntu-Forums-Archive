---
title: "Server NIC CONFIG~ help ! I'm GOIGN BALD!"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by pur@evilcom on 2009-03-20
I'm tired of trying to get help from websites that are vauge, or not exactly what I am trying to accomplish.  

Im my opinion this should be an extremely simple /interfaces config, but I was up for about 14 hours last night into today attempting to get this to run.

Here's a base line, I've got three NICs, eth2 is the onboard nic which I want to use for the incoming internet line. Then I have two additional NICs... I want eth1 feeding my PC. And I want eth0 feeding my router.  

I have tried EVERY possible scenario in teh course of the last 14-15 hours, in attempting to make this run.  My last configuration I actually got my PC to recognize it was attached to a network, but I couldn't get it connected to web ( this was about 4 of the 14 hours)...

I would think this would be something extremely simple to foward net to both eth0 & eth1... I was wrong.  My server is online and able to brw fine either DHCP, or static. but I'm having issues everywhere else as getting the other nic's setup properly..

Here's what I'm working with this is off the top of my head mind you.

can someone give me an idea and or a sample interfaces config of this? 

PAAA LEEEEAAAAASSSSSSSEEEEEEEEEEE:popcorn:for the one who solves it ;)

As shown this should work right... umm ..not in my case for soemreason... 

auto eth0
     iface eth0 inet dhcp
     
     auto eth1
     iface eth1 inet static
     address 192.168.1.1
     network 192.168.1.0
     netmask 255.255.255.0
     broadcast 192.168.1.255

---

