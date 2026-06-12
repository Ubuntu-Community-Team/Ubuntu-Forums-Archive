---
title: "Bridging computer cannot connect out after several hours"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by fusioned on 2009-02-28
I have recently installed Ubuntu server 8.10 (and gnome-desktop) onto a computer (lets call this computer A) which I intend to run headless in the future. 

I've managed to set it up to bridge the two ethernet adapters so I can connect the other desktop (I will call this B) which I mainly use into the rest of the network (and thus the internet). 

This works fine, until after several hours, or in most cases when I notice it, overnight after I wake up. I find that A cannot ping or connect anywhere else beyond pinging localhost.

B, which is connected to eth0 of A, can browse the internet fine, ping etc. A, does not connect out until i restart networking /etc/init.d/networking restart - but it has to recreate br0 (usually via editing /etc/network/interfaces); left alone, networking will see no need to recreate br0 , and the problem continues.

My interfaces file contains:

```
# The loopback network interface
auto lo
iface lo inet loopback

# connects to the other desktop
#auto eth0
iface eth0 inet manual

# 2nd network adapter - connects to the rest of the network
auto eth1
iface eth1 inet manual

# the bridge between eth0 and eth1
auto br0
iface br0 inet static
    address 192.168.1.10
    network 192.168.1.0
    netmask 255.255.255.0
    broadcast 192.168.1.255
    gateway 192.168.1.254

bridge_ports eth0 eth1

```

I have tried commenting out auto eth1 and eth0, left uncommented, ran eth1/eth0 with dhcp, and ran br0 with dhcp (but preferably I need computer A on a static IP address), but in all cases I still have the same issues with A being unable to connect out after several hours.

ifconfig returns this, at the time when A cannot connect out:

```
br0       Link encap:Ethernet  HWaddr 00:1f:d0:98:05:cf  
          inet6 addr: fe80::21f:d0ff:fe98:5cf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:721887 errors:0 dropped:0 overruns:0 frame:0
          TX packets:686284 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:135539140 (135.5 MB)  TX bytes:324245685 (324.2 MB)

br0:avahi Link encap:Ethernet  HWaddr 00:1f:d0:98:05:cf  
          inet addr:169.254.7.167  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:1f:d0:98:05:cf  
          inet6 addr: fe80::21f:d0ff:fe98:5cf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6799362 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6734295 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2747414425 (2.7 GB)  TX bytes:2913117601 (2.9 GB)
          Interrupt:253 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:e0:4c:02:5e:e8  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe02:5ee8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6781137 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7198267 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2219100329 (2.2 GB)  TX bytes:3142956330 (3.1 GB)
          Interrupt:20 Base address:0xce00 

eth0:avahi Link encap:Ethernet  HWaddr 00:1f:d0:98:05:cf  
          inet addr:169.254.7.167  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:253 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18595 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18595 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3026491 (3.0 MB)  TX bytes:3026491 (3.0 MB)

```

The only difference between the ifconfig output above, and ifconfig now (when it is working) is the presence of the br0:avahi entry - there is no such item when it is working fine.

There is no log entry in messages relating to br0 , except the points when i restart networking.

Anyone have a clue as to why the system is not connecting out whilst the bridge itself is still functional ?

---

### Post by fusioned on 2009-03-01
Update:

Around 25 hours after I last restarted br0, (A) cannot connect to outside addresses, i.e. google.com or [www.bbc.co.k](www.bbc.co.k), nor ping them. Pinging the router at 192.168.1.254 and this desktop works fine.

The DNS lookup seems to be working fine via the router, as new previously unlooked-up domains seem to be picking up their addresses, but no actual data transfer seems to work.

tracepath google.com gives me this:
```
 tracepath google.com
 1:  infiniti.local.intranet (192.168.1.10)                 0.362ms pmtu 1500
 1:  BThomehub.home (192.168.1.254)                       101.580ms 
 1:  BThomehub.home (192.168.1.254)                        94.440ms 
 2:  no reply
 3:  no reply

```

Everything is working fine from this desktop (B), which is connected to eth0 of (A), one of the bridge sockets. eth1 is connected to the homeplug AV ethernet socket which transmits to the router.

This is the output from running routel:
```
         target            gateway          source    proto    scope    dev tbl
    192.168.1.0 24                    192.168.1.10   kernel     link    br0 
    192.168.1.0 24                    192.168.1.68   kernel     link   eth1 
  192.168.122.0 24                   192.168.122.1   kernel     link  vnet0 
    169.254.0.0 16                   169.254.7.167   kernel     link   eth0 
    169.254.0.0 16                                              link    br0 
        default      192.168.1.254                                     eth1 
        default      192.168.1.254                                      br0 
        default                                                 link   eth0 
    192.168.1.0          broadcast    192.168.1.10   kernel     link    br0 local
    192.168.1.0          broadcast    192.168.1.68   kernel     link   eth1 local
127.255.255.255          broadcast       127.0.0.1   kernel     link     lo local
    169.254.0.0          broadcast   169.254.7.167   kernel     link   eth0 local
  192.168.122.1              local   192.168.122.1   kernel     host  vnet0 local
   192.168.1.68              local    192.168.1.68   kernel     host   eth1 local
  192.168.122.0          broadcast   192.168.122.1   kernel     link  vnet0 local
  192.168.1.255          broadcast    192.168.1.10   kernel     link    br0 local
  192.168.1.255          broadcast    192.168.1.68   kernel     link   eth1 local
169.254.255.255          broadcast   169.254.7.167   kernel     link   eth0 local
   192.168.1.10              local    192.168.1.10   kernel     host    br0 local
  169.254.7.167              local   169.254.7.167   kernel     host   eth0 local
      127.0.0.0          broadcast       127.0.0.1   kernel     link     lo local
192.168.122.255          broadcast   192.168.122.1   kernel     link  vnet0 local
      127.0.0.1              local       127.0.0.1   kernel     host     lo local
      127.0.0.0 8            local       127.0.0.1   kernel     host     lo local
         fe80:: 64                                   kernel           vnet0 
         fe80:: 64                                   kernel            eth1 
         fe80:: 64                                   kernel            eth0 
         fe80:: 64                                   kernel             br0 
        default        unreachable                     none              lo unspec
            ::1                 ::                     none              lo local
fe80::21f:d0ff:fe98:5cf                 ::                     none              lo local
fe80::21f:d0ff:fe98:5cf                 ::                     none              lo local
fe80::2e0:4cff:fe02:5ee8                 ::                     none              lo local
fe80::2848:b3ff:fe10:cac8                 ::                     none              lo local
      ff02::1:3          ff02::1:3                                      br0 
          cache                                                             
         ff00:: 8                                                     vnet0 local
         ff00:: 8                                                      eth1 local
         ff00:: 8                                                      eth0 local
         ff00:: 8                                                       br0 local
        default        unreachable                     none              lo unspec

```

The standard route output is:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 br0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
192.168.122.0   *               255.255.255.0   U     0      0        0 vnet0
link-local      *               255.255.0.0     U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 br0
default         BThomehub.home  0.0.0.0         UG    100    0        0 eth1
default         BThomehub.home  0.0.0.0         UG    100    0        0 br0
default         *               0.0.0.0         U     1000   0        0 eth0

```

ifconfig gives me at this moment:
```
br0       Link encap:Ethernet  HWaddr 00:1f:d0:98:05:cf  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fe98:5cf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2655799 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2586904 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:553530790 (553.5 MB)  TX bytes:904580069 (904.5 MB)

eth0      Link encap:Ethernet  HWaddr 00:1f:d0:98:05:cf  
          inet6 addr: fe80::21f:d0ff:fe98:5cf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9073651 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9169409 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3456105799 (3.4 GB)  TX bytes:4046709987 (4.0 GB)
          Interrupt:253 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:e0:4c:02:5e:e8  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe02:5ee8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9374416 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9816302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3129660095 (3.1 GB)  TX bytes:3965054433 (3.9 GB)
          Interrupt:20 Base address:0xce00 

eth0:avahi Link encap:Ethernet  HWaddr 00:1f:d0:98:05:cf  
          inet addr:169.254.7.167  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:253 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22353 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22353 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3288680 (3.2 MB)  TX bytes:3288680 (3.2 MB)

vnet0     Link encap:Ethernet  HWaddr 2a:48:b3:10:ca:c8  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::2848:b3ff:fe10:cac8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2370 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:507182 (507.1 KB)

```

Restarting /etc/init.d/networking gives the following output:
```
 * Reconfiguring network interfaces...                                                                                            * if-up.d/mountnfs[eth1]: waiting for interface br0 before doing NFS mounts
 * Stopping NTP server ntpd
   ...done.
 * Starting NTP server ntpd
   ...done.

Waiting for br0 to get ready (MAXWAIT is 32 seconds).
 * Stopping NTP server ntpd
   ...done.
                                                                                                                          [ OK ]
root@infiniti:/etc/apache2/mods-enabled#  * Starting NTP server ntpd
   ...done.

```

..with the result that it finally works - 
```
root@infiniti:~# ping google.com
PING google.com (74.125.67.100) 56(84) bytes of data.
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=1 ttl=237 time=172 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=2 ttl=237 time=144 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=3 ttl=237 time=147 ms
^C
--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2016ms
rtt min/avg/max/mdev = 144.900/154.901/172.395/12.412 ms

```

I can't figure out why this is happening! Unfortunately I need this bridging setup as I do not have a switch in the room, as I only have one port in this room to the router. Having to restart the networking setup on this computer will be inconvenient in the long run, as I plan to leave it in a corner unattended whilst it acts as a local server. Any ideas?

---

