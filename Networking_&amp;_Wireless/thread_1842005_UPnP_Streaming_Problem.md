---
title: "UPnP Streaming Problem"
date: 2011-09-10
forum: Networking &amp; Wireless
---

### Post by sdegan on 2011-09-10
My Ubuntu 10.04 box is setup as a DHCP/NAT router using bind9 for DNS support and linux-igd for UPnP support. It works GREAT! Except that something is going awry with the UPnP support. I installed linux-igd which seemed to work well -- for example, my Playstation talks nicely with my network attached storage device which is running DLNA. I was really excited when I saw it listed on my Playstation's list of attached UPnP devices and even more excited when it was able to show a list of files on the device. The problem is that when I try and stream a movie, I get a mysterious "Media Server Error: A network error has occurred. (00000000)" message from my Playstation. Does anyone have any ideas as to how I can diagnose this? Or any suggestions as to how to fix this issue?

---

### Post by poolet on 2011-09-14
Login as admin on your modem/router 192.168.*.*  and try to enable **UPnP **to see what happens**.... **If you don't know default of your router just open up a new terminal and type 

```
ifconfig "**interface**"
```

---

### Post by sdegan on 2012-02-18
The problem is that I do not have a router or modem. My Linux box is my router for my network. I have eth0 setup on the internal network, and eth1 setup as a WAN connection. I have upnpd running as a daemon but I still get the same error.

---

