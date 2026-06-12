---
title: "I Cant Connect Internet..."
date: 2010-02-11
forum: Networking &amp; Wireless
---

### Post by Wingate on 2010-02-11
```
lspci
00:0d.0 Ethernet controller: ALi Corporation ULi 1689,1573 integrated ethernet. (rev 40)
```Config with sudo ifconfig eth0 192.168.2.255 netmask 255.255.255.0
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:d4:57:56:97  
          inet addr:192.168.2.25  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fe57:5697/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30 errors:83 dropped:0 overruns:0 frame:83
          TX packets:143 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2499 (2.4 KB)  TX bytes:19849 (19.8 KB)
          Interrupt:17 Base address:0xc400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```But cant connect, i configured DNS so cant connect. I'm trying to connect to internet about 2 weeks but i cant :(
On WinXp i have to configure my eth configuration (10Mbps/Full Duplex) if i use 100Mpbs i cant connect on XP. I Need to config on Ubuntu.


```
engin@EnGiN-LiNuX:~$ sudo ethtool -s eth0 speed 100 duplex full autoneg off
Cannot set new settings: Operation not supported
  not setting speed
  not setting duplex
  not setting autoneg
engin@EnGiN-LiNuX:~$ 


engin@EnGiN-LiNuX:~$ sudo mii-tool
SIOCGMIIPHY on 'eth0' failed: Operation not supported
no MII interfaces found
engin@EnGiN-LiNuX:~$ 
``````
engin@EnGiN-LiNuX:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 1652
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:13:d4:57:56:97
Sending on   LPF/eth0/00:13:d4:57:56:97
Sending on   Socket/fallback
Cannot set new settings: Operation not supported
  not setting speed
  not setting duplex
  not setting autoneg
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:13:d4:57:56:97
Sending on   LPF/eth0/00:13:d4:57:56:97
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```Sorry about my bad English. Please heLp me. Ty.

---

### Post by Iowan on 2010-02-11
What does **sudo lshw -C network** report about the interface? 
I'm a little confused whether you're trying to set speed for 10 or 100 Mbps. With the static configuration, can you ping router/modem/gateway?

---

### Post by Wingate on 2010-02-13
```
engin@engin-desktop:~$ ping 192.168.2.1
connect: Network is unreachable
``````
engin@engin-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:d4:57:56:97  
          inet6 addr: fe80::213:d4ff:fe57:5697/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:4 dropped:0 overruns:0 frame:4
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2988 (2.9 KB)
          Interrupt:17 Base address:0xc400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
```
```

engin@engin-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: ULi 1689,1573 integrated ethernet.
       vendor: ALi Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       logical name: eth0
       version: 40
       serial: 00:13:d4:57:56:97
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=uli526x driverversion=0.9.3 duplex=full latency=64 link=yes maxlatency=40 mingnt=20 multicast=yes port=MII speed=100MB/s
       resources: irq:17 ioport:c400(size=256) memory:faefec00-faefecff
```
```
engin@engin-desktop:~$ sudo ethtool eth0
Settings for eth0:
    Supported ports: [ MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 1
    Transceiver: external
    Auto-negotiation: on
    Supports Wake-on: pg
    Wake-on: d
    Link detected: yes
```

```
engin@engin-desktop:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.2.1
```
```
engin@engin-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
```

What is problem i dont know :(

---

### Post by Iowan on 2010-02-13
I've never used **ethtool** before - but have you tried:```
sudo ethtool -s eth0 speed 10
``` Afterwards, you may need to try  **dhclient eth0** again.

---

### Post by Wingate on 2010-02-14
```
engin@engin-desktop:~$ sudo ethtool -s eth0 speed 10
[sudo] password for engin: 
Cannot set new settings: Operation not supported
  not setting speed
```

```

engin@engin-desktop:~$ dmesg | grep eth0
[   13.742165] eth0: ULi M5263 at pci0000:00:0d.0, 00:13:d4:57:56:97, irq 17.
[   14.231095] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.231385] uli526x: eth0 NIC Link is Up 100 Mbps Full duplex
[   17.231646] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   28.104021] eth0: no IPv6 routers present

```

i'm on ubuntu now. But first i start xp then restart and ubuntu. Maybe I dont have a chance.

---

### Post by Iowan on 2010-02-15
After you pull the XP->Ubuntu trick, what are results of **ifconfig -a** and **lshw -C network**? (I'm curious what XP changes to make Ubuntu work - usually that combination *causes* problems)

---

### Post by Wingate on 2010-02-17
After Xp then Ubuntu and

```
engin@engin-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:d4:57:56:97  
          inet addr:192.168.2.35  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fe57:5697/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2004 (2.0 KB)  TX bytes:5063 (5.0 KB)
          Interrupt:17 Base address:0xc400 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

``````
root@engin-desktop:~# lshw -C Network
   *-network
       description: Ethernet interface
       product: ULi 1689,1573 integrated ethernet.
       vendor: ALi Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       logical name: eth0
       version: 40
       serial: 00:13:d4:57:56:97
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=uli526x driverversion=0.9.3 duplex=full ip=192.168.2.35 latency=64 link=yes maxlatency=40 mingnt=20 multicast=yes port=MII speed=100MB/s
       resources: irq:17 ioport:c400(size=256) memory:f9ffec00-f9ffecff
```


Note: I found something about memories. When i xp then ubuntu; memory:f9ffec00-f9ffecff
Just ubuntu; memory:faefec00-faefecff
What it means i dont know.

---

### Post by Wingate on 2010-02-21
I bought a new cat5 cable. There is no problem now. Thanks for your help ;)

---

