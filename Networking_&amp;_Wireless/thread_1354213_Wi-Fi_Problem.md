---
title: "Wi-Fi Problem"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by shade5 on 2009-12-13
Hi,

I can't connect to my Wi-Fi network. My next step is to edit /etc/network/interface and set the wpa-driver entry. Buthow do I find out which driver I use?

I am using the HP Compaq Mini 110c netbook. 

```
/etc/hosts

127.0.0.1	localhost
127.0.1.1	netbookx
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

```
/etc/network/interfaces

auto lo
iface lo inet loopback
auto eth2
iface eth2 inet static
address 192.168.2.65
netmask 255.255.255.0
gateway 192.168.2.1
```

```
/etc/resolv.conf

nameserver 192.168.2.1
```

```
ifconfig

eth0      Link encap:Ethernet  HWaddr 18:a9:05:8b:b6:68  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 

eth2      Link encap:Ethernet  HWaddr 0c:60:76:5b:8e:4f  
          inet addr:192.168.2.65  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::e60:76ff:fe5b:8e4f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2574 (2.5 KB)  TX bytes:2574 (2.5 KB)

```

```
lspci

01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
	Kernel driver in use: wl
	Kernel modules: wl, ssb
02:00.0 Ethernet controller [0200]: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter [1969:1062] (rev c0)
	Kernel driver in use: atl1c
	Kernel modules: atl1c
```

```
lsusb

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 10f1:1a13  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

```
pccardctl

#empty
```

```
uname

Linux netbookx 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux
```

```
iwconfig

eth2      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
```

Many thanks.

---

