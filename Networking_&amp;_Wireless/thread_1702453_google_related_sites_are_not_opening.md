---
title: "google related sites are not opening"
date: 2011-03-07
forum: Networking &amp; Wireless
---

### Post by rajashraful on 2011-03-07
hi,
I have shared my PPTP VPN connection to another computer. The procedure was like-- the 1st computer has two LAN connection port and 2nd computer has one LAN connection port. The 1st computer is connected to LAN via "Auto eth1" directly and "Auto eth0" is open. Then the "Auto eth0" of the 2nd computer is connected to the "Auto eth0" of the first computer. All cables are normal straight LAN cables. then I am connected to Internet via PPTP VPN via 1st computer. my "ifconfig" for the 1st computer is like below:

```
eth0      Link encap:Ethernet  HWaddr 00:30:4f:06:24:7d  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::230:4fff:fe06:247d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5333 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5500 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:896497 (896.4 KB)  TX bytes:874482 (874.4 KB)
          Interrupt:17 Base address:0xcc00 

eth1      Link encap:Ethernet  HWaddr 00:22:15:00:4f:c7  
          inet addr:192.168.35.214  Bcast:192.168.35.255  Mask:255.255.252.0
          inet6 addr: fe80::222:15ff:fe00:4fc7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24742 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11893 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7030108 (7.0 MB)  TX bytes:2285953 (2.2 MB)
          Interrupt:45 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6998 (6.9 KB)  TX bytes:6998 (6.9 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.0.1.12  P-t-P:10.0.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1400  Metric:1
          RX packets:6055 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6789 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:4934537 (4.9 MB)  TX bytes:1307586 (1.3 MB)

My IPv4 Settings of "Auto eth0" of the 1st computer is:

[Method:Shared to other computers. ]

Then I have configured the "Auto eth0" of 2nd computer like this:

I had gone to IPv4 settings and then "Routes..." and then "Add" and then:

Address :127.0.0.1 Netmask:255.0.0.0 Gateway:192.168.32.1 Metric:1 
```

*****192.168.32.1 is the gateway for my PPTP VPN too.

after all of those I am connected and can open other sites except google.com, youtube.com i.e. google related sites on the 2nd computer. On the 1st computer everything is normal.
I have tried changing the DNS but it did not work.
What is the problem here? Help please.

---

