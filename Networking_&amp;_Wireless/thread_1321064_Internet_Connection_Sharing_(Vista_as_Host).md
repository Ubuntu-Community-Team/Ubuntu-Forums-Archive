---
title: "Internet Connection Sharing (Vista as Host)"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by jeffrey296 on 2009-11-09
Hey all, I know ICS issues have been posted before, but I already spent a great deal of time searching and have not found anything that helps me. So here's the deal:

I'm basically trying to set up a triple monitor display between my Vista laptop (already dual display) and my Ubuntu desktop. I want to run 9.10 on the desktop. I have no wireless card for the desktop and am too far from the router to run a cable, so I've got an ethernet cable connected from my laptop to the desktop.

Currently, the desktop is running 8.04, and when I try to install 9.10 via Live CD, it doesn't work for whatever reason (there are no disk defects, it just freezes after installing and then upon reboot 9.10 doesn't exist on the HD). So I figured I'd just set up ICS first, and then use the update manager to update it.

Here's what I've done so far:
[LIST]
[*]Set up Vista to share the internet connection.
[*]Changed the Local Area Connection in Vista to have a static IP (IPv4) address of 192.168.0.1 and same gateway. I did NOT give the DNS servers any addresses, since I don't know how those work.
[*]I supposedly set up Ubuntu as a client by setting the default gateway (I think).
[/LIST]

Right now the Vista laptop says the Local Area Connection has a cable unplugged and Ubuntu cannot ping the laptop.

Can someone just give me step-by-step instructions as to how I set this up?

Thanks,
Jeff

P.S. I don't know if the ethernet cable is a crossover cable or not because I do not know the difference. Does this matter?

---

### Post by Iowan on 2009-11-09
> **jeffrey296 said:**
> P.S. I don't know if the ethernet cable is a crossover cable or not because I do not know the difference. Does this matter? It matters... Easiest way to tell is to hold both ends up - cords down, clip away from you (contacts toward you). A straight cable will have the same color pattern on both ends. On a crossover cable, othey will be different. [Here]("http://en.wikipedia.org/wiki/Ethernet_crossover_cable") is more information.
To go directly between computers usually requires a crossover cable. The other alternative is to use straight cables - but put a switch or hub between the two.

---

### Post by jeffrey296 on 2009-11-09
Yeah I just converted one of my straight cables to a crossover cable (I actually cut parts of the middle of the wire and moved them around). The computers now recognize that they are connected to SOMETHING, but when I ping 192.168.0.1 (the LAC's static IP on the Vista host computer) from Ubuntu, it says "From 169.254.8.133 icmp_seq=n Destination Host Unreachable" where "n" starts at 1 and increases with each time it states that.

Since I now have the right cable, can anyone describe how to do this?

---

### Post by Iowan on 2009-11-09
For whatever reason, it looks like an **avahi** address sneaked in...
Dunno if it'll be easier to get the right static address entered - or convince Vista to use an avahi (ZeroConf) address, too.

---

### Post by jeffrey296 on 2009-11-09
Ok I fixed that slightly. Basically the Ubuntu machine didn't have a static IP address. It does now, and that address is what is returned in the error message. I'm still not being able to ping my Windows machine though.

---

### Post by jeffrey296 on 2009-11-09
Got it working (all of it, including Synergy). The main problem was that my in Vista, the LAN connection had not reset, and thus had not accepted my change to static IP address yet. Then when I tried to access it through the Ubuntu computer, it did not find it. After that was fixed (and a little tinkering around) I was able to route the Ubuntu computer and get the internet working through the LAN connection. From there on setting up Synergy was a snap. I wholeheartedly recommend it to anybody who uses/wants to use two computers on one desk.

Thanks for your help,
Jeff

---

