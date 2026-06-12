---
title: "ASUS RT-N10 Problems"
date: 2010-08-25
forum: Networking &amp; Wireless
---

### Post by sn6uv on 2010-08-25
I have recently bought a new Asus RT-N10 router, which I am using as a wireless access point, except that I cannot access it. I think router is at 192.168.1.1, because that is the IP address that I was redirected to while trying to set it up, however I cannot access that IP address in firefox. 

When I ping 192.168.1.1 I get:
```

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 202.158.201.233 icmp_seq=1 Destination Host Unreachable
From 202.158.201.233 icmp_seq=2 Destination Host Unreachable

```The relevant (wlan0) output from ifconfig is:
```
 wlan0     Link encap:Ethernet  HWaddr 00:24:d6:2e:e0:24  
          inet addr:150.203.222.23  Bcast:150.203.223.255  Mask:255.255.254.0
          inet6 addr: 2002:96cb:dfaa:a:224:d6ff:fe2e:e024/64 Scope:Global
          inet6 addr: 2002:96cb:de53:a:224:d6ff:fe2e:e024/64 Scope:Global
          inet6 addr: fec0::a:224:d6ff:fe2e:e024/64 Scope:Site
          inet6 addr: 2002:96cb:df48:a:224:d6ff:fe2e:e024/64 Scope:Global
          inet6 addr: fec0::9:224:d6ff:fe2e:e024/64 Scope:Site
          inet6 addr: 2002:96cb:de20:9:224:d6ff:fe2e:e024/64 Scope:Global
          inet6 addr: fec0::8:224:d6ff:fe2e:e024/64 Scope:Site
          inet6 addr: 2002:96cb:def9:8:224:d6ff:fe2e:e024/64 Scope:Global
          inet6 addr: fe80::224:d6ff:fe2e:e024/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:659104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:870835 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:130535926 (130.5 MB)  TX bytes:83925924 (83.9 MB)

```I have tried plugging directly in to the router, but I cannot get a connection.

I have scanned 192.168.*.* using nmap. It gave me a few IP addresses but none of those brought me to my router setup page (when I entered the IP address into firefox).

The output from route -n is 
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
150.203.222.0   0.0.0.0         255.255.254.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         150.203.223.1   0.0.0.0         UG    0      0        0 wlan0

```I really want to get access to the router, so I can change some of the settings. I have tried resetting the router, and it allows me to access the router to set up a network, but once the network is set up I still cant change any settings. I can however access the Internet through the router. I have also run a traceroute, to google, but it didn't provide any useful information.

I am quite new to wireless networking, so any help would be greatly appreciated. I am running Ubuntu 10.04 64bit

---

### Post by Charlietje on 2010-08-25
your ip address is: 150.203.222.23
your gateway is: 150.203.223.1

I see 2 possible problems:
Or, your router is not set up correctly
Or, you have a fixed ip address setup instead of DHCP

can you post the output of:
```
cat /etc/network/interfaces
```

---

### Post by sn6uv on 2010-08-25
My output from cat /etc/network/interfaces is :
```

auto lo
iface lo inet loopback

```

---

### Post by necrosymbiont on 2010-09-02
I purchased this product today specifically because the box it came in mentioned software for Linux, and no Windows pre-requisites were mentioned. However, upon connecting everything up, I'm not getting any love.

Apparently, after connecting everything up, you should be able to open any browser and it will show the "Quick Internet Setup" page. That doesn't happen.

Network Manager shows the connection exists, but pinging produces the same response "Destination Host Unreachable" that sn6uv reported. Manually typing a few choice URLs such as "192.168.1.1" also does not help.

My ubuntu is 10.04 and my browser is firefox 3.6.8.

Any help would be much appreciated. I'm thinking about returning it, but doubt the retailer will refund an opened product.

---

### Post by necrosymbiont on 2010-09-03
So, I managed to fix my problem with this router. It turns out I made some newbish mistakes, and my fix probably won't work for most people unless they made the same mistakes. Basically, just check the following:

1. The router wants IP address 192.168.1.1. Ensure this address has not already been assigned on the network.

2. Ensure the web browser is not set to produce a blank page when it starts. I personally think it is annoying to see a so-called "home page" every time my browser starts, but if you disable this, you also disable the router's ability to interfere the way it would like to.


Once I'd covered these two steps, everything worked automagically, like it is supposed to. Again, YMMV.

---

