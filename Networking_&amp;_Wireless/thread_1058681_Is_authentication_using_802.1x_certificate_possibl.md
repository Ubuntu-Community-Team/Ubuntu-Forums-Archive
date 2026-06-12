---
title: "Is authentication using 802.1x certificate possible?"
date: 2009-02-03
forum: Networking &amp; Wireless
---

### Post by anders.ostling on 2009-02-03
Hi all!
I have bought an Acer AAO, and everything is working beautifully with the optimized kernel. Wireless works fine on WEP networks at home and on our corporate visitor network (open). 

The remaining sorrow point now is to have the box on our corporate wireless network.

Facts:
Ubuntu 8.10 netbook edition, all updates as of 2009-02-02
Optimized kernel 2.6.28 by SickBoy ([http://www.ug.it.usyd.edu.au/~scole/](http://www.ug.it.usyd.edu.au/~scole/))
Wireless adapter atheros ARA242X, driver ath5k

"iwlist scan" sees the hidden network, but Network Manager can not connect. I have done the following preliminary attempts

1. Export CA and personal certificate from my Windows computer
2. Use NM to 'connect to other networks', browsed to certificate files and filled in every field. 

However, the CONNECT button stays grayed, so there is no way that I can test if it works. Hmm, maybe this is a NM problem?

---

