---
title: "Static IPs for bridges in local network"
date: 2009-06-11
forum: Networking &amp; Wireless
---

### Post by Gustavo Narea on 2009-06-11
Hello, everyone.

In my home network, I have a server to which I want to assign an static local IP and create multiple bridges with one static IP each. The reason is that this server will run several virtual machines, and I want the host and the guests to have dedicated IPs via eth0 and bridges, respectively. I'm posting this in the Networking section because I don't believe it's specific to virtualization.

This is what I want to have in such a server:
[LIST]
[*]eth0 (or anything that could be used by the host) with 192.168.1.150.
[*]A first bridge using eth0, but with the IP address 192.168.1.151.
[*]A second bridge using eth0, but with the IP address 192.168.1.152.
[*]A third bridge using eth0, but using the Ip address 192.168.1.153.
[*]And so on...
[/LIST]

I've spent two days trying to make it work this way, but I haven't had luck. I've made the following attempts:
[LIST]
[*]```

**/etc/network/interfaces**
auto lo
iface lo inet loopback

# Adding the bridge:
auto br0
iface br0 inet dhcp
        bridge_ports eth0 tap0

auto tap0
iface tap0 inet manual
    tunctl_user gustavo

auto eth0
iface eth0 inet manual
    up    ip link set $IFACE promisc on
    down  ip link set $IFACE promisc off
```

With this, both eth0 and br0 work, but share the same address and the same MAC:
```

**ifconfig**
br0       Link encap:Ethernet  HWaddr 00:15:c5:a7:f0:19                                                                                                     
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0                                                                                  
          inet6 addr: fe80::215:c5ff:fea7:f019/64 Scope:Link                                                                                                
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1                                                                                                
          RX packets:167 errors:0 dropped:0 overruns:0 frame:0                                                                                              
          TX packets:107 errors:0 dropped:0 overruns:0 carrier:0                                                                                            
          collisions:0 txqueuelen:0                                                                                                                         
          RX bytes:26392 (26.3 KB)  TX bytes:30323 (30.3 KB)                                                                                                

eth0      Link encap:Ethernet  HWaddr 00:15:c5:a7:f0:19  
          inet6 addr: fe80::215:c5ff:fea7:f019/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:282 errors:0 dropped:0 overruns:0 frame:0      
          TX packets:217 errors:0 dropped:0 overruns:0 carrier:0    
          collisions:0 txqueuelen:1000                              
          RX bytes:43505 (43.5 KB)  TX bytes:55965 (55.9 KB)        
          Interrupt:17                                              

eth1      Link encap:Ethernet  HWaddr 00:16:cf:21:17:1f  
          inet6 addr: fe80::216:cfff:fe21:171f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1        
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000                        
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)              
          Interrupt:16 Base address:0xc000                    

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:832 (832.0 B)  TX bytes:832 (832.0 B)

tap0      Link encap:Ethernet  HWaddr ae:7d:44:67:e4:bb
          inet6 addr: fe80::ac7d:44ff:fe67:e4bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:143 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

virbr0    Link encap:Ethernet  HWaddr 6e:07:f5:78:01:a7
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::6c07:f5ff:fe78:1a7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:14683 (14.6 KB)

virbr1    Link encap:Ethernet  HWaddr 26:13:3a:f7:15:ae
          inet addr:192.168.100.1  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::2413:3aff:fef7:15ae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:14683 (14.6 KB)
```

Also, when I use br0, I cannot connect to other hosts by their name (e.g., gustavo-laptop.local), but only by IP, and vice versa.

[*]While with the following, br0 works but eth0 doesn't work:
```
auto lo
iface lo inet loopback

# Adding the bridge:
auto br0
iface br0 inet dhcp
    address 192.168.1.152
        bridge_ports eth0 tap0

auto tap0
iface tap0 inet manual
    tunctl_user gustavo

auto eth0
iface eth0 inet static
    address 192.168.1.151
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255
    gateway 192.168.1.1
    dns-nameservers 192.168.1.1
    dns-search france
```
[/LIST]

What am I doing wrong?

Thanks in advance.

---

