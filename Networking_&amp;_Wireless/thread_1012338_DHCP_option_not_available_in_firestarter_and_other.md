---
title: "DHCP option not available in firestarter? and other ICS questions..."
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by tamman2000 on 2008-12-15
Hello all

I am trying to set up an internet connection sharing system on my Ubuntu 8.10 laptop so that when my wife and I are in locations that only have a single cat5 connection we can both use the internet at the same time.

(my plan is eth0 on my machine to the outside world, and eth1 (wireless) to her machine locally, and hopefully securely)

From what I have read, it seems that firestarter is the way to go, so I got that and I am going through the setup...  there are two issues arising.

1.  The use DHCP option in the internet connection sharing panel of the wizard is grayed out.  I installed dhcp3-server from the repo's and still no love.  What am I missing?

2.  I have not seen anywhere in the documentation how to connect my wife's mac to my eth1(wireless) in order to share the connection once I have firestarter set up...  everything seems to assume that the internal network port is wired, or I am missing something very basic maybe...  Anyway, help would be appreciated on that front as well.

Thanks,
tamman2000

---

### Post by Iowan on 2008-12-16
Have you seen this [ICS]("https://help.ubuntu.com/community/Internet/ConnectionSharing") help page?

---

