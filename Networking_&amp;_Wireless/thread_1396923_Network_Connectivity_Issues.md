---
title: "Network Connectivity Issues"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by The Sorrow on 2010-02-02
I have Ubuntu 9.10 connected to an Intel Express 210T Stackable Hub and it wont connect eth0. The ethernet cables are connected and have correct cable standards with working ethernet cards, any ideas?

---

### Post by Iowan on 2010-02-02
I found some information about your [hub]("http://74.125.95.132/search?q=cache:k3wIZ1fx4ZoJ:ftp://download.intel.com/support/express/hubs/200/200GD.PDF+intel+Express+210T+Stackable+Hub&cd=1&hl=en&ct=clnk&gl=us&client=firefox-a"). Does the hub show activity lights? Besides the Ubuntu machine, what is connected to the hub? I presume the hub should be transparent to the machine - and there is a router/modem/etc also connected to provide addressing, gateway to internet, etc.

---

### Post by The Sorrow on 2010-02-05
Ok you were right *slaps forehead* Shoulda known that a hub didnt address devices. I found a switch that my teacher claims does network addressing. it doesnt work but my D-Link wireless router does work. just out of curiosity can you look up the switch? "Intel Express 10 Switch+"

---

### Post by Iowan on 2010-02-05
Found this [.pdf]("www.netsky.org/server/AdaptiveT.pdf") - but I didn't download it or check it.

---

### Post by The Sorrow on 2010-02-26
Allrighty i got it figured out, the hubs did need addressing so i brought in a wireless D-Link router and everything works like a charm

---

