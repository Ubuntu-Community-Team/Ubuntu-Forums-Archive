---
title: "DNS problem with openvpn"
date: 2012-02-01
forum: Networking &amp; Wireless
---

### Post by SiggSauer on 2012-02-01
[SIZE=2]I'm having a little problem with openvpn, when I start the openvpn service from my network manager I get the remote DNS and Domain name in my resolv.conf. But when I run it with a conf file in /etc/openvpn these options are not passed through to the resolv.conf.

My local network is 192.168.41.0/24 and the remote location is  192.168.0.0/16.[/SIZE] [SIZE=2]

Now I know it is probably caused by the "potential network conflict  error". My question is if there is a way to ignore this and push it  through anyway, changing either networks is just not an option unfortunately.[/SIZE]

---

