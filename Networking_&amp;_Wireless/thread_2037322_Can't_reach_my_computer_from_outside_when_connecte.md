---
title: "Can't reach my computer from outside when connected via Bluetooth"
date: 2012-08-04
forum: Networking &amp; Wireless
---

### Post by hamesjetfield on 2012-08-04
Hello,
I've connected my Ubuntu 12.04 laptop to Sony Ericsson J10i2 Elm via Bluetooth
in order to access the Internet. I can browse web pages and stuff, but
it's impossible even to ping it from outside. Assuming it's a firewall issue,
I've downloaded gufw and allowed entire incoming traffic. Unfortunately, it didn't help.
Thanks in advance for all hints and suggestions.

---

### Post by Sergius14 on 2012-08-04
To allow incoming connections you have to have a direct Public Address.

I don't think that you have this, but instead a kind of NAT from your provider.


To be sure, paste a full ifconfig -a output in this thread.

---

### Post by hamesjetfield on 2012-08-04
Here's my **ifconfig -a**:

```

bnep0     Link encap:Ethernet  HWaddr 00:1e:37:0e:30:3f  
          inet addr:79.162.101.86  Bcast:79.162.101.87  Mask:255.255.255.248
          inet6 addr: fe80::21e:37ff:fe0e:303f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:294 errors:0 dropped:0 overruns:0 frame:0
          TX packets:313 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:198911 (198.9 KB)  TX bytes:61672 (61.6 KB)

eth0      Link encap:Ethernet  HWaddr 00:1f:16:01:07:9b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:46 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1537 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1537 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:115230 (115.2 KB)  TX bytes:115230 (115.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:ea:52:fa:60  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

---

### Post by Sergius14 on 2012-08-07
Ok, you have a Public Address and that's good.

you can use 'tcpdump' to 'sniffer' the interface for incoming traffic.


So for example you may listen for any incoming traffic in a given interface from a selected IP source address.

With this, you are going to see if the traffic is coming or not.


If it is coming, maybe it is a local issue (Firewall?) but if it is not coming at all, it may be filtered by your provider.

---

