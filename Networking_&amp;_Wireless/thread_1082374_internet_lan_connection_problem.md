---
title: "internet lan connection problem"
date: 2009-02-27
forum: Networking &amp; Wireless
---

### Post by Gagle on 2009-02-27
Regards ,

Just installed Ubuntu on lab computer and I can't get it to connect to the internet (ethernet lan).  The computer detects the networks,hosts, workgroups and attached computers.  I can't ping the router, but will accept packets in dhcp mode.

command outputs in order of relevance :

```

user:~$ dmesg | grep eth
[   23.482858] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   23.499144] Driver 'sd' needs updating - please use bus_type methods
[   23.505305]  sdb:<4>Driver 'sr' needs updating - please use bus_type methods
[   33.359594] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[   89.504201] eth0: no IPv6 routers present
[  185.371452] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  186.850788] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[  186.851342] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  188.207592] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  189.729236] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[  189.729754] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  198.098533] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  199.631728] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[  199.632291] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  210.329416] eth0: no IPv6 routers present


user:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:25:0f:ab:02  
          inet addr:132.210.25.46  Bcast:132.210.25.255  Mask:255.255.255.0
          inet6 addr: fe80::211:25ff:fe0f:ab02/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2662 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:274196 (267.7 KB)  TX bytes:15485 (15.1 KB)
          Base address:0x2000 Memory:e8100000-e8120000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:55100 (53.8 KB)  TX bytes:55100 (53.8 KB)


user:~$ cat /etc/network/interfaces

auto lo
iface lo inet loopback




iface eth0 inet dhcp

auto eth0


user:~$ netstat -an | grep "LISTEN"
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
/*  irrelevant output ommited */


```

As you can see, it seems to be a driver problem.  It's an all-on-one-chip IBM computer and I recon that somehow something went a skew in the detection part of the installation.

Any ideas as to how to fix this situation ?

---

### Post by Gagle on 2009-03-02
Anyone here know how to fix the e1000 intel Gigabit driver problem I have ?

At least point to relevant documentation please ...

G

---

