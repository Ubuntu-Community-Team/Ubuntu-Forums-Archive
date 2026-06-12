---
title: "network help: slow speeds, homemade wifi repeater"
date: 2013-08-28
forum: Networking &amp; Wireless
---

### Post by mvmacd on 2013-08-28
Ok here is my setup:

I connected an old pc (Pentium 4) to a usb WiFi adapter, wlan5. It is connected to the internet.
Setup a script to automate connecting wlan5 and setting iptables upon boot. Here's the iptables
```

iptables --table nat --append POSTROUTING --out-interface wlan5 -j MASQUERADE
iptables --append FORWARD --in-interface eth0 -j ACCEPT
```
I got a linksys wifi router, and on the pc, set up a dhcp server on eth0. It has 172.0.0.1, I plug it into internet port of linksys (has 172.0.0.50) by ethernet.

So now I just connect to the linksys network, and (from 192.168.1.100, the wifi router being 192.168.1.1) I can load internet and also my local http file server (172.0.0.1:8080) on the same network (main reason for it is because the original wifi signal isn't strong enough and wlan5 is a long range wifi adapter).


Now here is the problem. I can stream files at 1 or 2 MB/s from my http server on 172.0.0.1, but when downloading I can only get 2-300KB/s max. If I download on the pc, I usually get 6-900KB/s, which is about the max for my internet. So what reason could there be for me not getting max speed over my linksys router when local web server goes beyond a MB/s? It can't be the signal. Any help is appreciated.

---

