---
title: "ics ubuntu 8.10 &gt; mac, winxp"
date: 2009-04-05
forum: Networking &amp; Wireless
---

### Post by weedsmoker85 on 2009-04-05
Hello
I have a pIV with two network cards
one is wireless and one is wired
my router is downstairs so i connect wireless with ubuntu and i want to share the connection with the realtek 10/100 card over a switch.
the machine is a dualboot with xp and in xp everything works fine
at first my wireless connection worked fine and i could browse the web but then i wanted to enable the internet connection sharing and i found a guide but this messed everything up
i still get connected to my router but i cannot browse the web
The names of the network cards are:
wlan0
eth0

and if i go type the following rule in terminal:
cat /etc/network/interfaces

i get this:
auto lo
iface lo inet loopback

i will attache a drawing of how it looks it's the same in xp as in ubuntu only eth0 has no ip in ubuntu

i want my internet back and if it's possible also share it with the rest of my network

---

