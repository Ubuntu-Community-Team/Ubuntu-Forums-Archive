---
title: "bridge problem for a virtual machine"
date: 2010-06-10
forum: Networking &amp; Wireless
---

### Post by tapas_mishra on 2010-06-10
I am using Ubuntu 9.04 and want to create a network 
bridge for the guest Operating System.

```

auto lo
iface lo inet loopback

auto br0
iface br0 inet static
        address 192.168.1.9
        network 192.168.1.0
        netmask 255.255.255.0
        broadcast 192.168.100.255
        gateway 192.168.1.100
        bridge_ports eth0
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.1.11
        dns-search local.domain.com
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

```After this I restarted my computer
and my internet and every other thing stopped working


```

#brctl show 

 bridge name     bridge id               STP enabled     interfaces
 br0           8000.00004c9f0bd2       no                eth0
pan0
virbr0

```Showed eth0 included in bridge which I did not wanted.

eth0 is some thing separate.
pan0 and virbr0 I have not added.

So after this I removed the above lines for bridge from /etc/network/interfaces looks now like

```

auto lo
iface lo inet loopback

```and I got all network things back internet etc.
But I want to know what was the error in above when I tried to create a bridge I do not want the eth0 to be included in bridge.

I want a separate LAN on the Ubuntu for the Guest OSes which is routed through eth0 and all trafic to eth0 should come from bridge.

The ifconfig -a output shows (After I deleted the bridge entries from /etc/network/interfaces)
```


eth1      Link encap:Ethernet  HWaddr 
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:5eff:fe30:1fa5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:448
          TX packets:47 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3404 (3.4 KB)  TX bytes:7464 (7.4 KB)
          Interrupt:17 Base address:0xc000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:158 (158.0 B)  TX bytes:158 (158.0 B)

pan0      Link encap:Ethernet  HWaddr 32:eb:7a:ea:b9:b3  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

virbr0    Link encap:Ethernet  HWaddr 7e:29:7a:15:6c:66  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::7c29:7aff:fe15:6c66/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:4043 (4.0 KB)

```I have not added virbr0 or pan0 don't know from where is it coming.How can I check that also ?

---

### Post by Peter09 on 2010-06-10
youe host ethernet connection needs to be set in promiscuous mode for everything to work.

---

### Post by tapas_mishra on 2010-06-10
Ok thanks for that.
Any thing else I need to check.

---

### Post by Peter09 on 2010-06-10
If it works go with it :p

---

### Post by tapas_mishra on 2010-06-10
Ok sure I will try just want to know if you can give some idea as what is the role of Spanning Tree Protocol in bridges.

---

