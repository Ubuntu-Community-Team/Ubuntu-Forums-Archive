---
title: "Transmission bind  ports - iptables"
date: 2011-10-11
forum: Networking &amp; Wireless
---

### Post by [pl]ice on 2011-10-11
Hi,

I'm looking at a way to range bind outgoing ports with transmission. 
(I've read all the transmission posts in here. Took a while)

I have found that transmission did a patch in 2010 and it was binding nicely. 

At the moment i haven't seen any solid answers. The only reasonable is to allow outgoing ports restricting to username.

Is there a way to use established/related or similar functions in iptables for that?
Edit:

how bout set the iptables to check the layer 7 for bittorent, if so then allow through, everything else, drop. (except the main ports etc...)

or ipp2p, but i haven't used it before.
thanks.

---

