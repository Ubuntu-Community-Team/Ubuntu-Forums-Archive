---
title: "Sharing internet over wifi from wvdial."
date: 2010-09-14
forum: Networking &amp; Wireless
---

### Post by arundracula on 2010-09-14
I have BSNL EVDO usb modem and I use wvdial to connect to internet in my Ubuntu 10.04.

I want to share my internet over wifi so I can use this on my wifi phones. I searched all over and actually ended up here. 

```

sysctl -w net.ipv4.conf.all.forwarding=1
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
iptables-save

```After this, I don't know what to do.

In windows I've done this to share the same.. but I prefer Ubuntu.

_**EVDO Connection**_
IP: xxx.xxx.xxx.xxx(auto)
SubnetMask:255.255.255.255(auto)
DNS1:aaa.aaa.aaa.aaa(auto)
DNS2:bbb.bbb.bbb.bbb(auto)

_**Wireless Connection**_
IP:192.168.1.1
SubnetMask:255.255.255.255
DNS1:aaa.aaa.aaa.aaa
DNS2:bbb.bbb.bbb.bbb
Default gateway: xxx.xxx.xxx.xxx(My internet IP address)

_**My phone**_
IP:192.168.1.2
SubnetMask:255.255.255.255
DNS1:aaa.aaa.aaa.aaa
DNS2:bbb.bbb.bbb.bbb
Default gateway:192.168.1.1

And this is my ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:26:18:8b:9a:70  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:820 (820.0 B)  TX bytes:820 (820.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:117.254.165.134  P-t-P:192.168.52.12  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:1608 errors:3 dropped:0 overruns:0 frame:0
          TX packets:1682 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1368524 (1.3 MB)  TX bytes:220344 (220.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:17:3f:d4:d6:da  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

---

### Post by sindhu_sundar on 2011-03-02
Bump!

Did you figure anything out?

---

### Post by arundracula on 2011-03-03
After some tests (before finding a way) my wifi card became faulty.

Later I bought another external wifi dongle. At that time BSNL EVDO modem is correctly detected by Ubuntu(Since Ubuntu 10.10 BSNL EVDO is working perfectly with Network Manager). So I plugged this dongle into the USB port and I was surprised.

WITHOUT ANY SETTINGS (Other than the password), it got connected and shared my Mobile Broadband throught wifi..

Thanks. Hope you will also go through this way and find yourself working.

---

