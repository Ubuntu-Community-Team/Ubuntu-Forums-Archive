---
title: "wired ethernet connection problem"
date: 2011-02-16
forum: Networking &amp; Wireless
---

### Post by Arminius Chieftan on 2011-02-16
Very frustrated newbie trying to install and configure 10.04 Server on a Toshiba Satellite ](*,) ...running into problems with the wired ethernet (eth0) internet connection. The Toshiba is connected to a Linksys WRT54G (w/ DD-WRT) and setup with its own static ip lease (192.168.1.200). 

lshw
```
root@SERVER1:~# lshw -class network
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:8b:2a:9c
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=192.168.1.200 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:25 memory:b4000000-b4003fff ioport:3000(size=256)

```
ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:8b:2a:9c  
          inet addr:192.168.1.200  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe8b:2a9c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19836 errors:1086 dropped:1086 overruns:0 frame:1086
          TX packets:5659 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1946859 (1.9 MB)  TX bytes:852580 (852.5 KB)
          Interrupt:16 

```

/etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface (dhcp)
#auto eth0
#iface eth0 inet dhcp

# The primary network interface (static ip)
auto eth0
iface eth0 inet static
        address 192.168.0.200
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

```

ping the server
```
root@SERVER1:~# ping -c 2 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=3.56 ms

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 1 received, 50% packet loss, time 1001ms
rtt min/avg/max/mdev = 3.563/3.563/3.563/0.000 ms

```

Thanks in advance.
-Will

---

### Post by dineshs on 2011-02-16
I think /etc/network/interfaces should be 
```
auto eth0
iface eth0 inet static
        address 192.168.1.200
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
```instead of 
```
auto eth0
iface eth0 inet static
        address 192.168.[COLOR="Red"]0[/COLOR].200
        netmask 255.255.255.0
        network 192.168.[COLOR="Red"]0[/COLOR].0
        broadcast 192.168.[COLOR="Red"]0[/COLOR].255
        gateway 192.168.[COLOR="Red"]0[/COLOR].1
```

---

### Post by Arminius Chieftan on 2011-02-16
Thanks dineshs. 

I think I narrowed the issue down to the /etc/resolv.conf file and improper nameservers.

---

