---
title: "No ip adress DHCP"
date: 2011-03-25
forum: Networking &amp; Wireless
---

### Post by Flerpje on 2011-03-25
Hi everyone!

Over the last few days, my XMBC Live based Ubuntu has been driving me crazy! My problem is, i can't get a working network connection via DHCP.

If i run the live cd, everything works flawlessly (excluding hardware issues). When i install the distro, the dhcp autoconfiguration fails. Afterwards i edit my /etc/network/interfaces and /etc/resolv.conf files so dhcp is actually used. But in order to get things working, i have to manually restart the networking service. If i don't i can see in my log files there is DHCP DISCOVER but somehow i don't get an ip.

If I restart the system there is no ip asigned on eth0, I have to manually run /etc/init.d/networking restart, in order for the internet to work on the server and on the LAN.

I've googled and searched forums and tried pretty much everything but i can't get it to work, no matter what! I hope someone can help me with this issue.

Thanks in advance!

```
Motherboard: ASUS AT3IONT-I
NIC: Realtek RTL8111/8186B (wired)
Distro: XBMC Live (Ubuntu Maverick)
```

---

