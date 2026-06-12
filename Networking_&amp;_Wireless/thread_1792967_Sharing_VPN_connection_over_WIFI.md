---
title: "Sharing VPN connection over WIFI"
date: 2011-06-28
forum: Networking &amp; Wireless
---

### Post by zefalosporin on 2011-06-28
Hello, I was trying to share my internet connection to my Iphone. Looked up some time on the internet but didn't find anyone with a similar scenario as mine. I connect using ethernet and a VPN connection (OpenVPN) and would like to use my wireless card to make my laptop serve as a hotspot for my Iphone.

Here is the output when I run ifconfig:


eth0      Link encap:Ethernet  HWaddr 00:21:9B:EF:DF:FD  
          inet addr:10.42.1.67  Bcast:10.42.255.255  Mask:255.255.0.0
          inet6 addr: fe80::221:9bff:feef:dffd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2184212 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1490352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2557618586 (2439.1 Mb)  TX bytes:385920256 (368.0 Mb)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:22:5F:5D:53:BC  
          inet6 addr: fe80::222:5fff:fe5d:53bc/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5575 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5575 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:165138 (161.2 Kb)  TX bytes:165138 (161.2 Kb)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:134.108.86.42  P-t-P:134.108.86.41  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:1953332 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1489375 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:2376696148 (2266.5 Mb)  TX bytes:258228514 (246.2 Mb)


Interface eth0 is ethernet, eth1 is wireless and tun0 is VPN. Could anyone help me out a little please? I would be very 
grateful. Thanks in advance.

---

### Post by zefalosporin on 2011-06-30
I think it's something with iptables but I cannot figure it out.. Any help? Thanks

---

### Post by zefalosporin on 2011-07-26
> **zefalosporin said:**
> I think it's something with iptables but I cannot figure it out.. Any help? Thanks

Still no help?

---

