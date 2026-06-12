---
title: "Intel Corp. Wifi Link 5300/Karmic 64b/ThinkPad W700: OS now needs restart 2 reconnect"
date: 2010-10-07
forum: Networking &amp; Wireless
---

### Post by original_MikZ on 2010-10-07
G'day people,

I have an IBM ThinkPad W700 running 64 bit Ubuntu 9.10 Karmic Koala. At the office I normally connect it to the Ethernet since it's never connected very reliably to the wifi there (drops out 2 or 3 times per day, usually at the worst possible time, of course), but it always worked just fine with Netgear WGR614v5 at home... until a week or two ago.

I used to be able to come home, take the laptop out of suspend mode, and it would connect to the wifi. Occasionally there'd be some hitch and I'd have to restart the network manager (sudo /etc/init.d/network-manager restart) but this was only sometimes, and when I did, it'd always work. But now, when I get home from work, I need to restart the entire system to get it to connect properly again. Without restarting the whole system, it either doesn't scan for wifi networks, it doesn't find any wifi networks, it keeps stuffing up my wifi password, or it connects and gets 0% signal.

Presumably, some driver was updated recently and it doesn't work so well. What's the easiest way to find out what drivers have been updated lately, and revert to a previous version? And what else can I try restarting so I don't have to restart the entire system? I've tried /etc/init.d/network-manager restart, /etc/init.d/networking restart, /etc/init.d/network-interface restart, and restart network-manager. I've also tried turning the wireless switch at the front of the laptop off and on, many times.

```
$ lspci -nn
[...]
03:00.0 Network controller [0280]: Intel Corporation Wireless Wifi Link 5300 [8086:4236]
[...]

$ ifconfig wlan0
[...]
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets: 80530 errors:0 dropped:0 overruns:0 frame:0
TX packets:59237 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
[...]

$ uname -mr
2.6.31-22-generic x86_64
```


The info above is when I've taken my laptop out of suspend mode and it won't connect to the network. lsmod doesn't say anything about wifi nor wireless; iwlist does see my network, which my older Januty laptop is connected to without drama.

Thanks,
MikZ.

---

### Post by original_MikZ on 2010-10-14
This problem just fixed itself a day or two ago. Another update, presumably.

---

