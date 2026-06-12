---
title: "Connection...no connection"
date: 2010-12-05
forum: Networking &amp; Wireless
---

### Post by lamar328 on 2010-12-05
I am connecting to a non-secured wireless network, and the connection is fine, yet when I open my internet browser the pages will not load. It is as if there is no internet connection.

The internet connection was working perfectly fine a week ago.

thanks

---

### Post by dineshs on 2010-12-06
Please post the results of```
ping 4.2.2.1 -c5
```and```
route -n
```

---

### Post by lamar328 on 2010-12-06
> **dineshs said:**
> Please post the results of```
ping 4.2.2.1 -c5
```and```
route -n
```

results of code: 
ping 4.2.2.1 -c5

Ping 4.2.2.1 (4.2.2.1) 56(84) bytes of data.

--- 4.2.2.1 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4031ms




results of code: 
route -n

Kernel IP routing table

Destination
172.20.0.0
169.254.0.0
0.0.0.0

Gateway
0.0.0.0
0.0.0.0
172.20.1.3

Genmask
255.255.254.0
255.255.0.0
0.0.0.0

Flags
U
U
UG

Metric
2
1000
0

Ref
0
0
0

Use
0
0
0

Iface
eth2
eth2
eth2



oh man that was a decent amount of manual copying. Okay, well I really really really hope that I gave some valuable information here to help fix my issue! Please note that the stats posted above are when I was "connected" to the server.


Just to quickly recap... I am connecting to the local library's server at 100% connectivity, but when I open my internet browser none of the pages will load. As if I have no internet connection. This was not an issue as of just a week ago.

---

