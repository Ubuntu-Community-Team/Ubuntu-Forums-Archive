---
title: "Linksys E1500 Router Setup"
date: 2011-06-23
forum: Networking &amp; Wireless
---

### Post by maxw3ll on 2011-06-23
Just recently purchased a new linksys router to replace my old WRT54G and I'm having trouble connecting to the internet. Everythings connected the same way as the old box and I haven't fiddled with any settings but I now receive a DNS Lookup Failed message in my browser. What am I doing wrong?

---

### Post by chili555 on 2011-06-23
In the configuration pages of the router, did the router get credible looking DNS nameservers from your ISP? Please see attached. Did Network Manager grab them or the router's IP address, probably 192.168.1.1 for DNS servers? In a terminal, run:```
cat /etc/resolv.conf
```Lastly, one of the DNS servers might be down.

---

