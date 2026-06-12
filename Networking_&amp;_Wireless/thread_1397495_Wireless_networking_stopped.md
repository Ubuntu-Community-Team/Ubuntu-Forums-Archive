---
title: "Wireless networking stopped"
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by Keith_Beef on 2010-02-03
My wireless network connection disappeared after doing some updates a couple of days ago.

Which is to say, that the wireless was working, I let update manager install updates, and a couple of days later I came to use the computer to find that there was no networking.

```
$ uname -a
Linux Saturn 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64 GNU/Linux
```

```
$ sudo lspci -v
...
05:00.0 Network controller: RaLink RT2561/RT61 802.11g PCI
	Subsystem: RaLink Device 2561
	Flags: bus master, slow devsel, latency 32, IRQ 20
	Memory at fa100000 (32-bit, non-prefetchable) [size=32K]
	Capabilities: [40] Power Management version 2
	Kernel driver in use: rt61pci
	Kernel modules: rt61pci
...
```


I read several other threads on here, and found advice to try ifconfig, lshw, iwconfig...


```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:55:99:60  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:29 Base address:0xe000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1a:4d:55:99:60  
          inet addr:169.254.5.248  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:29 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9676 (9.6 KB)  TX bytes:9676 (9.6 KB)

```


```
$ sudo lshw 
...
           *-network DISABLED
                description: Wireless interface
                product: RT2561/RT61 802.11g PCI
                vendor: RaLink
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: wmaster0
                version: 00
                serial: 00:1a:ef:02:d8:41
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=rt61pci latency=32 multicast=yes wireless=IEEE 802.11bg
                resources: irq:20 memory:fa100000-fa107fff
...
```

```
$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.
```

The wireless networking has failed in the past after updates, but only temporarily and has come back after a reboot. The problems then seemed to be linked to keyrings and authentication. This time, I have seen no messages about authentication... What could have happened to completely wreck my wireless networking this time?

K.

---

