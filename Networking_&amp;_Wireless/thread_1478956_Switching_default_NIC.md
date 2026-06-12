---
title: "Switching default NIC"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by jwab on 2010-05-10
Hi I have 2 NIC's in my mythbuntu 10.0.4 box, one is connected to a closed network eth0 and the other to an Internet gateway eth1.

For some reason Ubuntu always makes eth0 the default network card, even if I delete the connections and add them in different a order. Because of this I can't access the Internet w/o disabling the private network card.

I could just switch the cables over but this should be doable in software and I'd like to know how. Can anyone help?

Thanks

---

### Post by jwab on 2010-05-10
Managed to figure it out.

It seems the way to use network manager for default network assignment is by checking the 'Use this connection only for resources on its network' option in editing IPv4 routes on all connections you do NOT want to be the default.

---

