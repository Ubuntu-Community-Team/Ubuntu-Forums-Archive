---
title: "no connecting with wired or wireless"
date: 2010-04-01
forum: Networking &amp; Wireless
---

### Post by bottomdweller on 2010-04-01
in short : installed 9.10 on a dell inspiron 600m which has a broadcom bcm4401 ethernet and an intel PRO/Wireless LAN 2100 3B mini PCI. At this point, i'm not too picky about which one works (meaning neither of them currently work). nm-tool seems to pick up on both :
  the broadcom (eth0) is using the b44 driver, State is unavailable;
  the intel (eth1) is using the ipw2100 driver, it's State is disconnected.

i have encryption turned off, and the wireless sees a number of AP's (including mine).

help.

i'm jumping off the good ship m$ and determined to make this work!!!

thanks.

---

### Post by Iowan on 2010-04-01
Laptops are always tricky... What are results of **sudo lshw -C network**? (guess I haven't used **nm-tool** before...)

---

### Post by bottomdweller on 2010-04-02
sorry all, i hate it when people do what i just did - my poor excuse is that i was tired. ;) here is all the different (i think relevant) info from various commands :

dmesg :
```

[    1.515606] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:12:3f:00:f5:c3
[   14.591954] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.652674] ADDRCONF(NETDEV_UP): eth1: link is not ready

```ifconfig :
```

eth0      Link encap:Ethernet  HWaddr 00:12:3f:00:f5:c3  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:0c:f1:28:97:6f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Base address:0xe000 Memory:faffd000-faffdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```iwconfig :
```

eth1      unassociated  ESSID:"undefined"  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```lshw :
```

  *-network:0
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:00:f5:c3
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:11 memory:faffe000-faffffff
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth1
       version: 04
       serial: 00:0c:f1:28:97:6f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=32 link=no maxlatency=34 mingnt=2 multicast=yes wireless=unassociated
       resources: irq:5 memory:faffd000-faffdfff

```interfaces :
```

auto lo
iface lo inet loopback

```nm-system-settings.conf
```

[main]
plugins=ifupdown,keyfile

no-auto-default=00:12:3f:00:f5:c3,

[ifupdown]
managed=false

```tiafah!

---

### Post by bottomdweller on 2010-04-05
touch -m

---

