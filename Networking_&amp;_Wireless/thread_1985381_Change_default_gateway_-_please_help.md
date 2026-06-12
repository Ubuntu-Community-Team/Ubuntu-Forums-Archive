---
title: "Change default gateway - please help"
date: 2012-05-23
forum: Networking &amp; Wireless
---

### Post by liran1 on 2012-05-23
Hello,

I need to change the default gateway on an Ubuntu PC to 10.1.3.2, which is a different PC (with Firewall / NAT / Gateway configured in it).

I have tried several ways, and did not succeed.
ifconfig output:
```
ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:04:23:c7:a6:3e  
          inet addr:10.1.2.2  Bcast:10.1.2.255  Mask:255.255.255.0
          inet6 addr: fe80::204:23ff:fec7:a63e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1026 (1.0 KB)  TX bytes:3282 (3.2 KB)

eth4      Link encap:Ethernet  HWaddr 00:14:22:23:8a:50  
          inet addr:192.168.1.153  Bcast:192.168.3.255  Mask:255.255.252.0
          inet6 addr: fe80::214:22ff:fe23:8a50/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1513 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:173508 (173.5 KB)  TX bytes:151594 (151.5 KB)

eth5      Link encap:Ethernet  HWaddr 00:14:22:23:8a:51  
          inet addr:10.1.2.2  Bcast:10.1.2.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:fe23:8a51/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:3784 (3.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:164 errors:0 dropped:0 overruns:0 frame:0
          TX packets:164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17725 (17.7 KB)  TX bytes:17725 (17.7 KB)

```


/etc/network interfaces file:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

#
# XXX abuse of mapping function follows.
# The findcnet script DHCPs on all interfaces the first time it is invoked
# and uses the results of that for every other invocation.  The script
# returns "cnet" for the interface that is the control net, and the physical
# interface name for all others.
#
mapping eth*
    script /usr/local/etc/emulab/findcnet

#
# The control network has been identified and configured indirectly
# via the mapping above.  Here we just make sure that if shutdown, we
# remove the indicator file so that we will re-DHCP next time.
#
auto eth0 eth1 eth2 eth3 eth4 eth5 eth6 eth7 eth8 eth9
#iface cnet inet manual
#    up echo "Emulab control net is $IFACE"
#    down rm -f /var/run/cnet
#    down ifconfig $IFACE down
iface eth4 inet static
address 192.168.1.153
netmask 255.255.255.0
gateway 10.1.3.2

```

Can you please write me a fixed interfaces file which will work ?

Thanks !

---

### Post by liran1 on 2012-05-24
Anyone please ?

---

### Post by nathan726 on 2012-05-24
Perhaps you could try...
```
sudo route add default gw 10.1.3.2
```
Or
```
sudo ip route add default via 10.1.3.2
```

---

### Post by liran1 on 2012-05-24
I have already tried both but there is a '... No such process' error on these.

Does anyone knows what a fixed *interfaces* file should I use ?

Thanks in advance!

---

### Post by hawkmage on 2012-05-24
What is in your /usr/local/etc/emulab/findcnet script?

---

