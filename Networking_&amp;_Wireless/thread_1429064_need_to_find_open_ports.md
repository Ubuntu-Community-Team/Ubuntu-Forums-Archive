---
title: "need to find open ports"
date: 2010-03-13
forum: Networking &amp; Wireless
---

### Post by hippietilley on 2010-03-13
Alright, so i'm connected to an windows network. It's a school network and it blocks everything. I need help finding a port to run pidgin through so that I can connect to my im services. Any suggestions?

---

### Post by hippietilley on 2010-03-13
bump

---

### Post by MarkC502 on 2010-03-13
you could run nmap with the portscan option etc to find an open one but I doubt that will do the trick for you. If they allow web traffic then you can probably VPN out to your home network and the do whatever you want from there, so I would look at VPN's as a solution, you can even defend such VPN traffic much easier as they would have no way of proving you were IM'ing vs just bouncing web traffic through a VPN for security.

Mark

---

### Post by hippietilley on 2010-03-13
I've never fiddled with a VPN before. I also don't have a home network. But i will try the nmap thing.

---

### Post by hippietilley on 2010-03-13
Got it working. All I had to do was switch my accounts to run through port 80. Thanks for your help.

---

