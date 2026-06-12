---
title: "ubuntu boxes dont see each other on windows network"
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by jeh253 on 2010-03-10
I have two ubuntu boxes on a Windows network. One is 6.06.1 LTS and the other is 9.10. They are both configured for DHCP and networking works fine. The only issue I have is that these two boxes can not resolve each others IP from hostname. Any of the windows boxes on the network can resolve the ubuntu boxes IP from hostname and these two ubuntu boxes can resolve any of my windows clients IP from hostname; they just can't resolve each other. The DHCP/DNS Server is a Win2k3 box and there is a domain in place.  I'm guessing it's a windows configuration issue, hope someone here can help?

Thanks

---

### Post by sedawk on 2010-03-10
As you said you can correctly map IP <-> FQDN from the windows boxes, so DNS seems to work fine and should do so also when queried from a Linux box. Very strange.
Is it possible you have WINS/DNS running somehow in parallel
and what is working might be WINS but not DNS ? 
(I never used WINS, I only heard of it, this is a wild guess!).

You might try tools like dig (Ubuntu) or nslookup (Ubuntu, Windows command line) to debug this further.

---

### Post by Iowan on 2010-03-10
By default, Ubuntu boxes don't send their hostname to the DHCP server - but you can edit a line in */etc/dhcp3/dhclient.conf*  (send host-name) to fix that...

---

### Post by jeh253 on 2010-03-11
> **Iowan said:**
> By default, Ubuntu boxes don't send their hostname to the DHCP server - but you can edit a line in */etc/dhcp3/dhclient.conf*  (send host-name) to fix that...


If the ubuntu boxes weren't sending their names to the DHCP server, how would my Windows boxes be able to resolve their IP's and ping, or nslookup them?

---

### Post by jeh253 on 2010-03-11
> **Iowan said:**
> By default, Ubuntu boxes don't send their hostname to the DHCP server - but you can edit a line in */etc/dhcp3/dhclient.conf*  (send host-name) to fix that...


That didn't fix the problem anyway.

Another symptom: My windows boxes can ping the ubuntu boxes but they can't nslookup them...... ?

---

