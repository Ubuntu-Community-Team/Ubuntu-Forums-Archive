---
title: "Why is my internet speed so &quot;slow&quot;?"
date: 2011-04-06
forum: Networking &amp; Wireless
---

### Post by quickk on 2011-04-06
Hi everyone, 

I recently subscribed to a 100/5 Mbps internet service, and have been having trouble getting the expected speeds.   The cable modem is connected to a wireless router (D-link dir-825, gigabit), which in turn broadcasts the signal throughout my house (mixed n and g).   Unfortunately, using a wired connection between my main computer (a desktop) and the router is not possible without destroying some walls and running some cabling up from the basement to the second floor.   

The router is dual band (2.4/5GHz).  When I connect on the 2.4 GHz band, the signal strength is 100%, and the connection speed is listed at 200+ Mbps (according to the router's web configuration page).  However, when I go to speedtest.net, or try to download anything from a fast server, I max out at 15 Mbps.   Using the 5 GHz band, wireless connection strength is usually 50% - 70%, and the speed is listed usually somewhere around 100 - 200 Mbps.   When I try measuring the actual speed I get from the web, it tops out at a consistent 25 Mbps.   Using a laptop directly wired to the router I get speeds of >60Mps.   What gives?   

I don't understand why I get such slow actual speeds.  If I am connected at 200 Mbps to the router, with a 100% signal strength, shouldn't I be able to actually transfer faster than 15 Mbps from the internet?   Why is the 5GHz band faster, even though the connection strength is to the router is weaker?

If anyone can enlighten me, I would be very grateful.

---

### Post by conradin on 2011-04-06
```
ifconfig
ethtool -s <your connection>

```

can you tell us about your network card type, router, etc..
and give us some info fro those commands?
i'll check back later, gtg..

---

### Post by quickk on 2011-04-06
Hi conradin

My router is the [dlink DAP-825]("http://www.dlink.ca/products/?pid=681").  The desktop is connected to the wireless network using an ethernet cable plugged into a [dlink DAP-1522 access point]("http://www.dlink.ca/products/?pid=663").  

I don't think the problem lies with the desktop's network setup.  I have a mac laptop which suffers from the same problems when it wirelessly accesses the network.   

On my kubuntu desktop, the output of the commands you requested I try are:

```
ifconfig
eth0      Link encap:Ethernet  HWaddr xxxxxxx  
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fed8:daf9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:594417 errors:0 dropped:0 overruns:0 frame:0
          TX packets:342836 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:647164814 (647.1 MB)  TX bytes:64190340 (64.1 MB)
          Interrupt:44 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:163 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14134 (14.1 KB)  TX bytes:14134 (14.1 KB)

vmnet1    Link encap:Ethernet  HWaddr xxxxxxxxx 
          inet addr:172.16.154.1  Bcast:172.16.154.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:831 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000                                                                                 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)                                                                       
                                                                                                                       
vmnet8    Link encap:Ethernet  HWaddr xxxxxxxxxx                                                               
          inet addr:172.16.247.1  Bcast:172.16.247.255  Mask:255.255.255.0                                             
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:831 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



```

and 
```
ethtool -s eth0

```
(nothing)

```
sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                             100baseT/Half 100baseT/Full 
                                             1000baseT/Full 
        Link partner advertised pause frame use: No
        Link partner advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes
```

Thanks for your help!

---

