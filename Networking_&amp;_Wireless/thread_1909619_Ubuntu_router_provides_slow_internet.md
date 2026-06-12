---
title: "Ubuntu router provides slow internet"
date: 2012-01-15
forum: Networking &amp; Wireless
---

### Post by wesg on 2012-01-15
So today I moved from 5Mbps DSL to 24Mbps cable internet, and have discovered that my Ubuntu router is slowing my connection heavily. I'm using DHCP + iptables to provide internet and networking to my LAN. Using the router, I see 3Mbps with Speedtest, and when I plug the modem directly to my laptop, I get 30Mbps. 

I'm trying to upgrade my system's 9.10 to at least 10.10 so perhaps that's it? What else can I check?

---

### Post by jsra on 2012-01-15
Hello,
I would try the speedtest from ubuntu first.

---

### Post by wesg on 2012-01-15
I tried nload (server has no frontend) and received the same values I got from my Windows 7 workstation. I'm currently downloading the updates for 10.04 so I hope that does something...

---

### Post by elliotbeken on 2012-01-16
Is the Ubuntu box just doing routing?

i have a zentyal firewall that filters antivirus and firewall rules on an old athlon it can only pass about 100kb/s per second because it cant process the data fast enough

---

