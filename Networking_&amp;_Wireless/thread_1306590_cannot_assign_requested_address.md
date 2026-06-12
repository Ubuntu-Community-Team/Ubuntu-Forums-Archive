---
title: "cannot assign requested address"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by ah6511 on 2009-10-30
Hi,

I have a application that used to work on ubuntu 8.1 with one NIC that has static IP. Now after I upgrade to 9.04, I always get "cannot assign requested address" error. BTW, I have direct internet connection. The PC has 2 NICs, only eth1 is connected to internet with static IP. Any ideas? TIA

-Andy

---

### Post by i.r.id10t on 2009-10-30
/etc/network/interfaces is probably empty or otherwise set wrong.

---

### Post by Iowan on 2009-10-30
Post */etc/network/interfaces *. How does the other interface (eth0?) get address?
Results of **ifconfig -a** might also be helpful.

---

