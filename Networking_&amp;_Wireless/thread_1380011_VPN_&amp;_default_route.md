---
title: "VPN &amp; default route"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by butterflyT on 2010-01-13
Hi,
I wanna connect to a remote LAN via VPN so after some search i've installed pptp-linux package and configure everything that i read from [https://wiki.ubuntu.com/VPN](https://wiki.ubuntu.com/VPN)
When i prompt in commandline
```
pon myvpn nodetach
``` it displays something like that:
```
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
CHAP authentication succeeded
MPPE 128-bit stateless compression enabled
Cannot determine ethernet address for proxy ARP
local  IP address x.y.z.t
remote IP address x'.y'.z'.t'
primary   DNS address a.b.c.d
secondary DNS address a.b.c.e
```Anyway everything seems like ok, but when i open [www.whatismyip.com]("http://www.whatismyip.com") i see my own IP not remote IP address. By the way i installed network-manager-pptp package and configure it via gui and try to connect remote LAN, everything is ok even my IP was changed. I realized that when i use network manager for VPN it changes my default route like that:
```
default         *               0.0.0.0         U     0      0        0 ppp0
``` so i also try to change my default route 
```
route add default gw <vpn_host> netmask 0.0.0.0 ppp0
```but i didn't work and my network connection had become down. How can i solve this problem... By the way what does * mean here?

Thank you ....

---

