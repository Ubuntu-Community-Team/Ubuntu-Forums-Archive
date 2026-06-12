---
title: "Wireless router periodic loss of Internet - how to debug?"
date: 2010-12-21
forum: Networking &amp; Wireless
---

### Post by rstoya05-lx on 2010-12-21
I have a wireless router from my provider Internet access many times a day unless I'm using a physical cable. There is nothing unusual in /var/log/syslog that I could see. 

When I'm connected successfully I see this:

```
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.208.0   *               255.255.255.0   U     0      0        0 vmnet1
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
192.168.98.0    *               255.255.255.0   U     0      0        0 vmnet8
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         api.home        0.0.0.0         UG    0      0        0 wlan0

```

When I lose connectivity I see the same except it takes longer for 'route' to show the last line, the "api.home" gateway is replaced by the router's actual IP address (192.168.1.254), and I cannot ping the router. The router's web interface however lists my laptop as being connected. 

There are two laptops on my home network both running Ubuntu 10.4. Both lose connectivity. There is also a Squeezebox device and an Android phone. Not sure if this is related or not but sometimes the router's web interface shows (what is probably) the Android phone listed as connected multiple times under a slightly different mac address to different ip addresses. For example:

Unknown-00-23-76-2b-69-c9
Unknown-00-23-76-2b-69-c9-2
Unknown-00-23-76-2b-69-c9-3
Unknown-00-23-76-2b-69-c9-4
Unknown-00-23-76-2b-69-c9-5

I've also seen the same laptop listed under two IP addresses as well. Any suggestions on how to debug this further?

---

