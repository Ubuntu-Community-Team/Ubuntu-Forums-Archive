---
title: "Wireless for Lenovo T400 doesn't work"
date: 2010-02-22
forum: Networking &amp; Wireless
---

### Post by libei.twer on 2010-02-22
Hi,

I just got a new T400 and installed Ubuntu. Everything is fine and I'm really impressed by this OS. But seems my wireless network is very unstable. Sometimes it just can't connect.

The wireless interface is:

       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation

Thanks!

---

### Post by libei.twer on 2010-02-22
The output from lshw -class network is

  *-network
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:27:13:6a:36:96
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=1.8-3 ip=192.35.98.72 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:fc600000-fc61ffff memory:fc625000-fc625fff ioport:1840(size=32)
  *-network
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 00
       serial: 00:26:c6:85:c6:a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:31 memory:f4200000-f4201fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

---

### Post by libei.twer on 2010-02-23
Seems it's hard to fix.

Just post some extra info. And any advice is welcomed (like buying a PCMCIA card), I just want my wireless.

Thanks!


bei@bei-laptop:~$ lspic
03:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
        Subsystem: Intel Corporation Device 1211
        Flags: bus master, fast devsel, latency 0, IRQ 31
        Memory at f4200000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: iwlagn
        Kernel modules: iwlagn


bei@bei-laptop:~$ ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:26:c6:85:c6:a2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:364522 errors:0 dropped:0 overruns:0 frame:0
          TX packets:293977 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:357317251 (357.3 MB)  TX bytes:27947132 (27.9 MB)

bei@bei-laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


bei@bei-laptop:~$ lsb_release -d:
Ubuntu 9.10


bei@bei-laptop:~$ uname -mr
2.6.31-19-generic-pae i686

---

