---
title: "SERVER- ICS DNS Problem"
date: 2012-05-27
forum: Networking &amp; Wireless
---

### Post by Hwest on 2012-05-27
Hey forums,

I made an earlier thread about this that didnt help much, But that was more the ICS config not the client.
Im trying to connect my PS3 to my Ubuntu server to increase streaming speeds using the IPTables method in this guide:
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

I get the following on my server for ```
sudo iptables -L
```:
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  192.168.0.0/24       anywhere             ctstate NEW
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

I configure the ICS using the settings:
wlan0: Internet, Static ip 192.168.1.52, Subnet 255.255.255.0, Gateway, 192.168.1.254.
eth0: PS3 connection with Crossover LAN, Static IP(As per guide) 192.168.0.1/24 (What is the /24?) Subnet, 255.255.255.0

Ifconfig displays:
```
eth0      Link encap:Ethernet  HWaddr 90:2b:34:22:df:c5
          inet addr:192.168.0.1  Bcast:0.0.0.0  Mask:255.255.255.0
          inet6 addr: fe80::922b:34ff:fe22:dfc5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:111 errors:0 dropped:0 overruns:0 carrier:17
          collisions:0 txqueuelen:1000
          RX bytes:60 (60.0 B)  TX bytes:20449 (20.4 KB)
          Interrupt:42

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1308 (1.3 KB)  TX bytes:1308 (1.3 KB)

wlan0     Link encap:Ethernet  HWaddr 90:f6:52:62:96:b9
          inet addr:192.168.1.52  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::92f6:52ff:fe62:96b9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:626 errors:0 dropped:0 overruns:0 frame:0
          TX packets:576 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:223484 (223.4 KB)  TX bytes:286463 (286.4 KB)

```

Then the settings on the PS3 Client:
IP(Static): 192.168.0.100 (Per guide)
subnet: 255.255.255.0
Default router: 192.168.0.1 (Per guide)
DNS: As per routers Default with the ISP

When I test connect to the internet on the PS3 I get:
Obtain IP Address: Succeeded
Internet Connection: Failed

Error is:
```
An error occurred during communication with the server. This is a DNS error.(80710102)
```
Sonys statement about that code:
[http://faq.en.playstation.com/app/answers/detail/a_id/856/~/ps3-error-80710102](http://faq.en.playstation.com/app/answers/detail/a_id/856/~/ps3-error-80710102)

I havent checked everything there and confirm it all is working.

Any help would be awesome,

Cheers.

---

### Post by Hwest on 2012-05-28
Bump

---

### Post by Hwest on 2012-05-29
Bump. Anyone help?

---

### Post by Hwest on 2012-05-30
Does anyone have an idea to fix this?

---

