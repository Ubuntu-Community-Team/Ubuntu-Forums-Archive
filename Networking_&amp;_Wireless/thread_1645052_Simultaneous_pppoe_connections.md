---
title: "Simultaneous pppoe connections?"
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by sagarthegreat1 on 2010-12-14
hello Linux users.
my isp provides different services via same line.Just that the have different access concentrators.
now i can connect to them using the rp-pppoe package.

**pppoe -A** give the output:
> 
sudo pppoe -A
Access-Concentrator: Rajeshnet3
       Service-Name: Rajeshnet3
Got a cookie: 88 1a 22 cf a5 c1 cf 39 d8 bb ca c6 d8 cd 84 29 a3 0c 00 00
AC-Ethernet-Address: 00:07:e9:0c:67:fd
--------------------------------------------------
Access-Concentrator: FiveNet
       Service-Name: 5netpantnagar
AC-Ethernet-Address: 00:07:e9:2a:ad:b4
--------------------------------------------------
Access-Concentrator: RajeshDC3
       Service-Name: RajeshDC3
Got a cookie: 1f 40 5c a3 fe 82 6e f7 13 bb 9a 14 22 b5 9b e0 9d 0c 00 00
AC-Ethernet-Address: 00:07:e9:0e:43:5c
--------------------------------------------------
Access-Concentrator: worldnet002
       Service-Name: worldnet002
Got a cookie: 6e 71 9d 73 ef 4a cf f6 91 3d 18 72 d1 33 f1 ed cb 4e 00 00
AC-Ethernet-Address: 00:15:17:c9:f0:5a
--------------------------------------------------
Access-Concentrator: Zone.Net
       Service-Name: Zone.Net
AC-Ethernet-Address: 00:1b:21:2d:96:61
--------------------------------------------------



now i can connect to worldnet002 **OR** Zone.Net, depending on the acname field in my pppoe.conf.
i wanted to know a way to connect to both of them at the same time.
i can do it in windows.

---

