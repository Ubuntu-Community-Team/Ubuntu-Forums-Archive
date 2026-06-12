---
title: "Shrew VPN on Ubuntu 10.04/10.10 desktop"
date: 2011-01-19
forum: Networking &amp; Wireless
---

### Post by eini on 2011-01-19
Hello,

I have following problem. I try to establish connection between Shrew VPN 2.1.5 and 2.1.7 to Linksys RV042 router. On Windows everything is ok. On Ubuntu 9.04 also works. But on Ubuntu 10.04 and 10.10 tunnel is established but it seems that packets are not forwarded from tap0 to eth0.
I can ping remote vpn gateway, local tap0 interface. Connection is OK (i see it on RV042 logs) but I cannot ping any machine on remote lan. Generally there is no network traffic on the tap0 output.
I have all rp_filter set to 0 and ip_firwarding set to 1. Firewall is off. Because it worked on previous Ubuntu edition it looks that this is poroblem in kernel conf?
Does anybody can help me in this subject?

---

