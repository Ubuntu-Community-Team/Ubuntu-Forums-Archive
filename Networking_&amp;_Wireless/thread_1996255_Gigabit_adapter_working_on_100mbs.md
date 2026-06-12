---
title: "Gigabit adapter working on 100mbs"
date: 2012-06-04
forum: Networking &amp; Wireless
---

### Post by Apocalypse_X on 2012-06-04
Hello, 
I hope you can help me out diagnose a strange and annoying problem with my network. 

My home network is based on TP-Link 1043nd router (running dd-wrt) set as dhcp router and wifi ap (looking to move the dhcp server to the homeserver). Hooked to it are several machines and a repotec G3800gc swich. My main machine and homserver are connected to the swich. Both are running 12.04 precise respectivly amd64 desktop and i386 server. 

On both machines there is problem with connecting on gigabit speed. 
I don't know how but after multiple ifup/down and so on the server managed to connect on gigabit, however I'm unable to do the same for the desktop machine. I tried setting it manually with ethtool, however there wasn't any results. 

The equipment (router, swich, cables) are fine, and the Windows machines connect fine. Here's the output from my homeserver 

```
master@homeserver:~$ lspci -k | grep Ethernet
05:02.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5782 Gigabit Ethernet (rev 03)
05:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RTL8169/8110 Family PCI Gigabit Ethernet NIC
master@homeserver:~$ ethtool eth1
Settings for eth1:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Advertised pause frame use: Symmetric
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: Unknown
Cannot get wake-on-lan settings: Operation not permitted
        Current message level: 0x000000ff (255)
                               drv probe link timer ifdown ifup rx_err tx_err
Cannot get link status: Operation not permitted
master@homeserver:~$ ifconfig 
eth1      Link encap:Ethernet  HWaddr 00:40:ca:8e:2a:6f  
          inet addr:100.10.10.100  Bcast:100.10.10.255  Mask:255.255.255.0
          inet6 addr: fe80::240:caff:fe8e:2a6f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6577034 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14403428 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3542079184 (3.5 GB)  TX bytes:19980774001 (19.9 GB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:137245 errors:0 dropped:0 overruns:0 frame:0
          TX packets:137245 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4499512610 (4.4 GB)  TX bytes:4499512610 (4.4 GB)

master@homeserver:~$ uname -a
Linux homeserver 3.2.0-24-generic-pae #39-Ubuntu SMP Mon May 21 18:54:21 UTC 2012 i686 i686 i386 GNU/Linux


```

And here is from the desktop machine

```
user@dc7900:~$ lspci -k | grep Ethernet
00:19.0 Ethernet controller: Intel Corporation 82567LM-3 Gigabit Network Connection (rev 02)
user@dc7900:~$ ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 2
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: on
Cannot get wake-on-lan settings: Operation not permitted
	Current message level: 0x00000001 (1)
			       drv
Cannot get link status: Operation not permitted
user@dc7900:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:24:81:14:df:c9  
          inet addr:100.10.10.108  Bcast:100.10.10.255  Mask:255.255.255.0
          inet6 addr: fe80::224:81ff:fe14:dfc9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1060128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:812817 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1057449512 (1.0 GB)  TX bytes:131916692 (131.9 MB)
          Interrupt:19 Memory:f2000000-f2020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1044 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1044 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:149793 (149.7 KB)  TX bytes:149793 (149.7 KB)

user@dc7900:~$ uname -a
Linux dc7900 3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by Apocalypse_X on 2012-06-08
Notice something interesting while still trying to fix this issue.

This is the working adapter
```
master@homeserver:~$ sudo mii-tool -vv eth1
Using SIOCGMIIPHY=0x8947
eth1: negotiated 1000baseT-FD flow-control, link ok
  registers for MII PHY 1: 
    1000 796d 0020 61a2 05e1 cde1 000d 2001
    4011 0300 3800 0000 0000 0000 0000 3000
    0000 2f00 0000 0000 0000 0331 0000 4003
    7277 871f 0000 ffff 2801 34f4 8000 0000
  product info: vendor 00:08:18, model 26 rev 2
  basic mode:   autonegotiation enabled
  basic status: autonegotiation complete, link ok
  capabilities: 1000baseT-HD 1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  advertising:  1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control
  link partner: 1000baseT-HD 1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control

```


As far as i can see from the output below, the problem is that for sume !@#$%%^ reason the NIC isn't advertising correctly...

```
user@dc7900:~$ sudo mii-tool -vv eth0
Using SIOCGMIIPHY=0x8947
SIOCGMIIREG on eth0 failed: Input/output error
SIOCGMIIREG on eth0 failed: Input/output error
SIOCGMIIREG on eth0 failed: Input/output error
SIOCGMIIREG on eth0 failed: Input/output error
SIOCGMIIREG on eth0 failed: Input/output error
SIOCGMIIREG on eth0 failed: Input/output error
SIOCGMIIREG on eth0 failed: Input/output error
SIOCGMIIREG on eth0 failed: Input/output error
SIOCGMIIREG on eth0 failed: Input/output error
SIOCGMIIREG on eth0 failed: Input/output error
SIOCGMIIREG on eth0 failed: Input/output error
SIOCGMIIREG on eth0 failed: Input/output error
SIOCGMIIREG on eth0 failed: Input/output error
SIOCGMIIREG on eth0 failed: Input/output error
SIOCGMIIREG on eth0 failed: Input/output error
SIOCGMIIREG on eth0 failed: Input/output error
SIOCGMIIREG on eth0 failed: Input/output error
SIOCGMIIREG on eth0 failed: Input/output error
SIOCGMIIREG on eth0 failed: Input/output error
SIOCGMIIREG on eth0 failed: Input/output error
SIOCGMIIREG on eth0 failed: Input/output error
SIOCGMIIREG on eth0 failed: Input/output error
eth0: negotiated 100baseTx-FD flow-control, link ok
  registers for MII PHY 2: 
    1140 796d 0141 0cb0 0de1 4de1 0005 ffffffff
    ffffffff 0200 4000 ffffffff ffffffff ffffffff ffffffff 3000
    ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff
    ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff
  product info: vendor 00:50:43, model 11 rev 0
  basic mode:   autonegotiation enabled
  basic status: autonegotiation complete, link ok
  capabilities: 1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  advertising:  100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control
  link partner: 1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control

```

---

### Post by daniel.pool on 2012-08-08
Apocalypse_X,

Did you get any further with this issue, I am having exactly the same problem with an Intel 82547L Gigabit NIC.

My output from mii-tool is near identical to yours.

~Dan

---

