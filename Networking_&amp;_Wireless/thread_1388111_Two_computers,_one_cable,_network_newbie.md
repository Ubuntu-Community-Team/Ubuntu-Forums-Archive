---
title: "Two computers, one cable, network newbie"
date: 2010-01-22
forum: Networking &amp; Wireless
---

### Post by desperateone on 2010-01-22
So I got two computers, one with Ubuntu other with freeBSD, and I'd like to connect them both to the internet. All I have is one Ethernet cable that I used to plug into the computer. How would I do it? Do I have to get a hub, or can I simply use some kind of cable splitter?

---

### Post by Swab on 2010-01-22
Please explain a little more about your setup.  

Do you have a router that connects to the internet?  If so does it have multiple ports so that you could plug in both computers?  If it has only one port then you need to get yourself a switch which would plug in to the router and also the 2 computers.

---

### Post by Iowan on 2010-01-22
A router (if you don't have one) would probably be the easiest option. You can make Ubuntu (maybe BSD... I haven't used it) share it's connection, but you'd probably need another NIC, and a crossover cable or hub/switch.  Your ISP probably won't let you have two IP addresses, so a hub/switch at the incoming connection might work for only the first machine to be turned on.

---

