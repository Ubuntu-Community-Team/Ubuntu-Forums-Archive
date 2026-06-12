---
title: "Bond Interface with slaves of Virtual and phisycal Interface"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by S&amp;S on 2011-04-28
I created a virtual interface (wlan0:1) and I want to bond it with my physical interface (wlan0) , My goal is to make more virtual interfaces and bond them with each other and balance the bandwidth between them , and make my default route that bond interface (bond0) ,the reason is I use a network witch is bandwidth limit by ip address:( and I want to get much more bandwidth by using virtual interfaces and balance my bandwidth by bond interface:).
:confused:but there is some think wrong , the HWAddress of  the bond interface is  00:00:00:00:00:00  and I don't know how to set it , when I down the interface and up it again to change its' HWAddress , it doesn't work at all !!
Is the problem is that I want to make a the slaves from virtual interface ?
"ifconfig" output:
```

lo           Link encap:Local Loopback 
             inet addr:127.0.0.1  Mask:255.0.0.0
             inet6 addr: ::1/128 Scope:Host
             UP LOOPBACK RUNNING  MTU:16436  Metric:1
             RX packets:96568 errors:0 dropped:0 overruns:0 frame:0
             TX packets:96568 errors:0 dropped:0 overruns:0 carrier:0
             collisions:0 txqueuelen:0
             RX bytes:66621279 (66.6 MB)  TX bytes:66621279 (66.6 MB)

bond0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00 
              inet addr:192.168.2.15  Bcast:192.168.2.255  Mask:255.255.255.0
              UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
              RX packets:0 errors:0 dropped:0 overruns:0 frame:0
              TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0
              RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:22:fa:91:53:90 
             inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
             inet6 addr: fe80::222:faff:fe91:5390/64 Scope:Link
             UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
             RX packets:102351 errors:0 dropped:0 overruns:0 frame:0
             TX packets:85337 errors:0 dropped:0 overruns:0 carrier:0
             collisions:0 txqueuelen:1000
             RX bytes:75117513 (75.1 MB)  TX bytes:14909368 (14.9 MB)
wlan0:1  Link encap:Ethernet  HWaddr 00:22:fa:91:53:90 
             inet addr:192.168.2.25  Bcast:192.168.2.255  Mask:255.255.255.0
             UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1



```"cat /etc/network/interfaces" output :
```

auto lo
iface lo inet loopback

auto wlan0:1
iface wlan0:1 inet static
address 192.168.2.25
netmask 255.255.255.0
gateway 192.168.2.1

auto bond0
iface bond0 inet static
address 192.168.2.15
gateway 192.168.2.1
netmask 255.255.255.0
bond-slaves wlan0 wlan0:1
bond_mode 0
bond_miimon 100
bond_lacp_rate 1

```

---

