---
title: "Server keeps losing its ip"
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by grungerokker13 on 2009-03-13
We just installed 8.10 server on a few boxes and they were working fine for a while; however, today one of our boxes started dropping its static ip. We set them all up for static ip's using the /etc/network/interfaces file. The file had them as: 
"auto lo
iface lo inet loopback"

We changed them to:
"auto eth0
iface eth0 inet static
address (ip address)
netmask (subnet mask)
network (network addy)"

It worked fine for a few days then all of a sudden it just started losing its ip. ifconfig shows that eth0 has no ip, so I restart networking and the correct IP is back but then in a few minutes it will drop it again. Is it because we removed the loopback interface?  We did this on 6 boxes and only one is having this problem.

Has anyone encountered this before?

---

### Post by Iowan on 2009-03-13
I've heard of similar things - machines that get DHCP address despite being set up with static address. Although loopback adapter probably shouldn't be removed, it didn't enter into the formula.  Wish I could remember something about the thread to find it... seems like solution involved removing dhclient.

---

