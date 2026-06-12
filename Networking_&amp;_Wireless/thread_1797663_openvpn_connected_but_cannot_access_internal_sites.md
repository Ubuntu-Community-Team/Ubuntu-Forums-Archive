---
title: "openvpn: connected but cannot access internal sites"
date: 2011-07-05
forum: Networking &amp; Wireless
---

### Post by d3v1150m471c on 2011-07-05
I am connected to a vpn, using open vpn. ifconfig shows the assigned vpn address, the routing tables and arp looks normal, i can ping hosts within the vpn but when i try to open a website via firefox on the internal network it can't connect. other websites like this one work fine. i'm new to vpn so any advice would be greatly appreciated

---

### Post by poolet on 2011-07-05
check the following thread maybe helps you... I search all over the net and i get that... Hope that helps you!!!!

[http://forums.untangle.com/openvpn/8578-site-site-vpn-step-step-instructions.html](http://forums.untangle.com/openvpn/8578-site-site-vpn-step-step-instructions.html)

---

### Post by poolet on 2011-07-05
Also try to enable  ip forwarding on vpn server...

```
sysctl -w net.ipv4.ip_forward=1 
```

---

### Post by d3v1150m471c on 2011-07-05
Thanks for the support guys, i'm gonna give these a shot and let you know something. I have a sneaking suspicion that it's my modem/router specifically from my isp.

---

### Post by d3v1150m471c on 2011-07-05
Got it with the help of a friend on the vpn:
```

mv /etc/resolv.conf /etc/resolv.conf.backup && echo 'nameserver 1.0.27.38' > /etc/resolv.conf

```

DNS wasn't working

---

