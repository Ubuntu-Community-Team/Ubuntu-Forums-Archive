---
title: "Network topology question"
date: 2013-08-26
forum: Networking &amp; Wireless
---

### Post by Keith_Beef on 2013-08-26
I have a small home network, that is likely to grow, and I'm looking for a way to mix wired and wireless together.

I have an ADSL modem and wireless router supplied by my ISP, which has only four ethernet ports. My ReadyNAS is taking up one of those ports, and the TV is taking up another one (so as to play video and music files off the NAS without taking Wifi bandwidth).

Connected by Wifi for now are a Patriot PBO Core media player, two Ubuntu computers, an Apple MacBook and a few small devices (elelctronic book, tablets, telephones).

I'm thinking that all the devices that are in the same room as the ADSL modem/router could be connected by ethernet cables, and that I could either connect the NAS that way or I could move it out of that room to somewhere cooler and where the noise would be less of an inconvenience.

So I was thinking of an 8-port gigabit ethernet switch and a couple of powerline ethernet (CPL) adapters, to make the topology shown in the figure below.

I already have the 500 Mbps CPL adapters, but not the switch. I'm wondering what kind of throughput I'd get with my idea… it's got to be better than the 36 - 48 Mbps that I'm getting with Wifi.

---

### Post by Kevin_Arnold on 2013-08-26
I can't view the attachment on my mobile browser for some reason but I would definitely get everything in the same room on a gigabit switch.  I'd leave the NAS on that too.

It's up to you about the power line stuff, I never had good luck with them but you might.

---

### Post by Rsxhawk on 2013-08-29
I own some netgear powerline kits, and they work great as long as both endpoints are in the same room even though that sort of defeats the purpose of having them.  My home is relatively new, only 4 years old with good wiring but the units do not work reliably enough if I'm traversing from the office to my tv room (which is only about 20-30 feet from room to room, but as for the path the wiring takes it could be much longer.  I took some packet captures of the traffic through the powerline kit and it was retransmission-city, took forever to load webpages.  It will just depend on your home really and how its wired, I have heard of many people having success with those units, just not me.  

As far as your idea goes, I would put everything on the gigabit switch if possible, if you only have one VLAN, then connecting your current router to the switch shouldn't be a problem.  As far as what amount of throughput you'll get, keep in mind that you're only as fast as your slowest link in the path between two endpoints.  If you're getting a gigabit switch anyway, I would also opt for getting a gigabit wireless router as well, one that does wireless N or AC.  Your throughput will skyrocket on those wireless standards.  If you're still using Wireless G, don't expect your wireless speeds to get any faster just because you install a switch.

---

