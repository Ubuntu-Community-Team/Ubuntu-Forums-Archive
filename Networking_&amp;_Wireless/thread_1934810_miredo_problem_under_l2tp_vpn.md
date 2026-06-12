---
title: "miredo problem under l2tp vpn"
date: 2012-03-02
forum: Networking &amp; Wireless
---

### Post by koyabr on 2012-03-02
[SIZE=3]I`m using l2tp vpn network, and tying to get a ipv4-to-ipv6 teredo by tending to miredo. Sadly it just failed.[/SIZE]:(

[SIZE=4]
1 For my /etc/default/ufw   I`ve set "ipv6=yes".[/SIZE]

[SIZE=4]2 The server is OK Cau`z my friend using an ADSL  has his miredo working fine.[/SIZE]

[SIZE=4]3  the "ifconfig teredo" result:[/SIZE]

[SIZE=1]teredo    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          POINTOPOINT NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/SIZE]
[SIZE=4]
4  the "ifconfig"  result:[/SIZE]
eth0      Link encap:Ethernet  HWaddr 00:23:8b:cb:a9:c6  
          inet6 addr: fe80::223:8bff:fecb:a9c6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17537 errors:0 dropped:1213 overruns:0 frame:0
          TX packets:10021 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11197344 (11.1 MB)  TX bytes:1853548 (1.8 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1400 (1.4 KB)  TX bytes:1400 (1.4 KB)

ppp0      Link encap: Point-to-Point Protocol  
          inet addr:10.171.17.55  P-t-P:10.171.16.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:15907 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9740 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:10630416 (10.6 MB)  TX bytes:1579122 (1.5 MB)

ppp1      Link encap: Point-to-Point Protocol  
          inet addr:222.205.38.5  P-t-P:10.5.6.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1442  Metric:1
          RX packets:9787 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9163 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:10007165 (10.0 MB)  TX bytes:1186467 (1.1 MB)

wlan0     Link encap: Ethernet  HWaddr 00:22:fa:e6:59:54  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



Looking forward to someone`s help, thanks.

---

