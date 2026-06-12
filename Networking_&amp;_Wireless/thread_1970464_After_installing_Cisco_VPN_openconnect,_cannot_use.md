---
title: "After installing Cisco VPN openconnect, cannot use http throught normal network"
date: 2012-05-01
forum: Networking &amp; Wireless
---

### Post by Melclic on 2012-05-01
I have a very weird problem. I am running ubuntu 12.04 (fully upgraded) and an HP pavilion dm4. I was able to connect to my home wireless network without a problem when installing and everything was running smoothly.

My University required the installation of the Cisco VPN openconnect software, and which worked without a problem. 

However when I tried to connect to my home network, I connect to my router and seem to be 'online', but I cannot use any type of http. Skype works, ping works, dig works but firefox, empathy and updating does not.

I can use the openconnect VPN software to connect to the internet ONLY through my university network.

I tried uninstalling the software, and the problem persists. As well I have tried connecting with a ethenet cable, same problem.

I would appreciate any pointers as to where the problem could be and what other information you need. Sounds like an easy fix but I do not know where to look!

---

### Post by steeldriver on 2012-05-01
it sounds like either your university VPN server does not allow **split tunneling**, or you didn't configure your client to use it (e.g. "Use this connection only for resources on its network")

however I don't know why it would persist after you removed the VPN client - your old routes should be restored as soon as you disconnect - perhaps the routing table just didn't update/revert for some reason?

---

### Post by Melclic on 2012-05-01
How do I update the routing table. Google tells me that it involves ```
netstat -rn
``` 
I'm not sure how to use that or what is the default settings.

---

### Post by Melclic on 2012-05-01
Ok here are the iwconfig ifconfig and netstat, when I'm not going through the University's VPN:

```
$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:4  Signal level:193  Noise level:162
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 1c:c1:de:a5:ab:eb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 70:f3:95:36:6a:84  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::72f3:95ff:fe36:6a84/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:785 errors:0 dropped:0 overruns:0 frame:5042
          TX packets:879 errors:18 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:75945 (75.9 KB)  TX bytes:84834 (84.8 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
```

Hope this leads to the right answer

---

### Post by Melclic on 2012-05-03
Ok I solved the problem. For some reason the resolv.conf file in /etc was being modified by the VPN program which somehow ported everything through the Uni. Or something like that....

So what I did is used this defualt configuration of the resolv.conf file
[HTML]http://theos.in/desktop-linux/resolve-conf-linux-example/[/HTML]

```
cd /etc
gksudo resolv.conf
```

Delete everything and paste
```
nameserver 202.54.1.10
 nameserver 202.54.1.11
```

That fixed it. What can be done so that the resolv.conf file cannot be modified?

---

