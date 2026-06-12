---
title: "ICS:  Client can ping Internet using IPs, DNS not working"
date: 2009-08-21
forum: Networking &amp; Wireless
---

### Post by Michael&amp;Dana on 2009-08-21
This is my first post here.

I have two computers connected with a LAN cable, one connected to a wireless adapter.

I'm running Intrepid on the gateway machine that is connected via wireless to a Linksys router.  The client machine running XP is connected to this via a LAN cable.

Router > wlan0 > Intrepid > eth0 > XP

- or - 

Router (192.168.1.1) > Address from router's DHCP (192.168.1.XXX) > Intrepid > (192.168.2.113) Static > (192.168.2.123) Static on the XP machine

- or - 

```

eth0      Link encap:Ethernet  HWaddr 00:08:74:38:21:6b  
          inet addr:192.168.2.113  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::208:74ff:fe38:216b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3491 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2081 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:373879 (373.8 KB)  TX bytes:240952 (240.9 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17322 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17322 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1023441 (1.0 MB)  TX bytes:1023441 (1.0 MB)

wlan0     Link encap:Ethernet  HWaddr 00:16:b6:96:ef:1b  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:b6ff:fe96:ef1b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:917770 errors:1 dropped:0 overruns:0 frame:0
          TX packets:890743 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:694470729 (694.4 MB)  TX bytes:444574335 (444.5 MB)

```As the title suggests, I can get Internet access, though no DNS.  I've spent all day on this, and have reached a roadblock.

I've followed every permutation I can muster from the following link up to the end of dnsmasq instructions before the alternative approaches section.  However, I have tried to use Firestarter while still using DHCP from the router before any of this.

Thanks in advance if anyone can help!

Michael & Dana

---

### Post by dmizer on 2009-08-21
Unless you have configured a [local DNS server](https://help.ubuntu.com/community/BIND9ServerHowto), you'll have to manually set the DNS servers.

Here's one way: [https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)

---

### Post by Michael&amp;Dana on 2009-08-21
I really should have tried a static IP on the gateway machine and Open DNS in both machines as I did now.

You've made Dana a happy girl, and that makes me happy.

Sorry to bother you with this.

Thanks again!

---

### Post by zot171 on 2009-08-21
dmizer, thank you very much. i had set the DNS servers as static on my router (linksys WRT54G running dd-wrt, give it a try if youd like) but i hadnt configured the laptop to use the static DNS servers (i made an assumption and paid the price for it...) but well, now i feel kinda foolish because ive been operating under this assumption for 3 DAYS trying everything else!

thanks again!

---

