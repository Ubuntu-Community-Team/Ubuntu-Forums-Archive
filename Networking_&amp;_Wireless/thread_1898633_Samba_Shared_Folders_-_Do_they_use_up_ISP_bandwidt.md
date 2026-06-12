---
title: "Samba Shared Folders - Do they use up ISP bandwidth?"
date: 2011-12-21
forum: Networking &amp; Wireless
---

### Post by jackbusch on 2011-12-21
This might be a stupid question, but if my Windows computer is transferring 12 GB over the wireless network to my Ubuntu shared folder (via samba), does this rack up ISP bandwidth? Also, why would this be so slow--it's about the same speed as it would be if I were transferring this over the Internet. Which is why I'm sort of wondering if this is a true LAN transfer or not.

---

### Post by inobe on 2011-12-21
no, it will not use isp bandwidth, only network bandwidth.

if you unplug the ethernet cable from modem, you'll notice that it's still transferring over your lan!

> transferring 12 GB over the wireless network 

do you mean 12 mbits?

---

### Post by jackbusch on 2011-12-21
Sorry for the confusion, I was talking about the size of the files I was trying to transfer. I have no idea what the actual transfer speed is, other than slower than I expected.

Edit: But thanks for answering my question about the ISP bandwidth!

---

### Post by inobe on 2011-12-21
if it's a 12 gig file, i will assume a couple minutes to complete.

look at your system monitor, that'll show whats going on for network during a transfer.

if you get something similar between 9.0 mb/s up to 54 mb/s that's okay, i guess.

it really depends on your hardware!

---

