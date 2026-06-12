---
title: "Problem with routing"
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by unavenged on 2010-01-14
Hi, We have a Front end server(Ubuntu 9.04) that we use to connect to a kiosk over a VSAT link... We have routing in place an for some reason the server drops the routes after a few min and for some reasond when we run "arp" it lists all the other connections with the same MAC address, but they aren't even the same device...

```
$ arp
Address                  HWtype  HWaddress           Flags Mask            Iface
xxx-xxx-xxx-xxx.router.1  ether   00:1b:54:23:3e:f0   C                     eth0
xxx-xxx-xxx-xxx.server.1  ether   00:0d:88:ee:40:ac   C                     eth0
xxx-xxx-xxx-xxx.router.2  ether   00:0d:88:ee:40:ac   C                     eth0
xxx-xxx-xxx-xxx.server.2  ether   00:0d:88:ee:40:ac   C                     eth0

```

Why is this happening?

Thanks in advance

---

### Post by changingstate on 2010-01-14
Proxy ARP?

---

### Post by iponeverything on 2010-01-14
It looks like something on the network is doing proxyarp.

---

### Post by unavenged on 2010-01-15
But its only with this one server... How would i be able to fix it?

---

### Post by unavenged on 2010-01-15
I just found out that there are no devices running proxy arp

---

### Post by efflandt on 2010-01-15
**arp** will only show devices that have had recent network traffic from the computer you arp from, unless manually set with arp and not temporary.  Entries that are discovered will disappear if not used for a period of time, and arp will be used to find local IPs or gateways again when they are used again.  Just because you do not see something in arp does not mean it no longer exists, just that it has not been used lately.

If you want to see numerical active routing without DNS delays, use **route -n**.

---

