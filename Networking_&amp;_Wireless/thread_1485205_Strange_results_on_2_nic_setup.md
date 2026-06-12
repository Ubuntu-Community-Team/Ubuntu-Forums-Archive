---
title: "Strange results on 2 nic setup"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by harveyd on 2010-05-16
I have 2 nic cards running on an ubuntu server. One built in on logic board, the other a pci card.

I have both nic's setup in  /etc/network/interfaces as follows:-

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth0 eth1
iface lo inet loopback

# The primary network interface
iface eth0 inet static
        address 10.1.1.2
        netmask 255.255.255.0
        network 10.1.1.0
        broadcast 10.1.1.255
        gateway 10.1.1.1

iface eth1 inet static
        address 10.1.1.3
        netmask 255.255.255.0
        network 10.1.1.0
        broadcast 10.1.1.255
        gateway 10.1.1.1
```The results of ifconfig look like this:-

```
eth0      Link encap:Ethernet  HWaddr 00:0e:2e:6f:c7:ee  
          inet addr:10.1.1.2  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fe6f:c7ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:255409 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3197782 (3.1 MB)  TX bytes:384612846 (384.6 MB)
          Interrupt:18 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:0f:fe:2f:f4:83  
          inet addr:10.1.1.3  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:feff:fe2f:f483/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:516 errors:0 dropped:0 overruns:0 frame:0
          TX packets:147 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:83145 (83.1 KB)  TX bytes:17723 (17.7 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:52307 (52.3 KB)  TX bytes:52307 (52.3 KB)
```If I ping 10.1.1.2 from another machine it pings. If I then pull the ether cable out of built in nic it continues to ping, if I pull ether cable out of card 2 it stops ping and when I plug it back in it pings again. Fine.

BUT if I ping 10.1.1.3 from another machine it pings. If I then pull the ether cable out of built in nic it STILL continues to ping and if I pull ether cable out of card 2 it AGAIN stops ping and when I plug it  back in it pings again.

So in conclusion, no matter which IP I ping it appears to be linking to the 2nd card and not the built in NIC. ifconfig shows two different mac addresses which led me to believe it's seeing both cards.

The built in nic was working fine before I put in the second card so I know ubuntu recognizes it.

Any help please?? Much obliged!

---

