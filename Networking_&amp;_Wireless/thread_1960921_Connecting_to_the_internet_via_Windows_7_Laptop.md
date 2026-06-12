---
title: "Connecting to the internet via Windows 7 Laptop"
date: 2012-04-18
forum: Networking &amp; Wireless
---

### Post by Satki on 2012-04-18
I'm trying to connect to the internet via a windows 7 laptop, the laptop connects to the wireless hub via wifi and my Ubuntu PC connects to the laptop via crossover cable. The PC detects the network, but no internet. I've tried connection bridging and Internet Connection Sharing on the laptop without any luck. Any help?

---

### Post by newbie-user on 2012-04-19
I think Windows Internet Connection Sharing merely allows packet forwarding through the Windows box. You would probably have to set up static ip addresses for the Ubuntu box and the lan port of the laptop, then create a static route on the Ubuntu box so that it knows to route traffic through the laptop.

---

