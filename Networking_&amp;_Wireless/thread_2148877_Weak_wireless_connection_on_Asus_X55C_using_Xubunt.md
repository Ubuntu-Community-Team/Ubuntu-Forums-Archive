---
title: "Weak wireless connection on Asus X55C using Xubuntu 13.04"
date: 2013-05-27
forum: Networking &amp; Wireless
---

### Post by China Diapers on 2013-05-27
[COLOR=#333333][FONT=Ubuntu Beta]I had windows 8 initially installed on my Asus notebook before wiping and replacing with Xubuntu 13.04. The wireless signal on windows was fairly strong, but under Ubuntu rarely goes above 50% and the internet is running very slow.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Hopefully some of the below info is helpful is resolving the problem:
[/FONT][/COLOR]

lshw -C network:```
[COLOR=#222222]*-network               [/COLOR]
       description: Wireless interface       product: RT5390 Wireless 802.11n 1T/1R PCIe       vendor: Ralink corp.       physical id: 0       bus info: pci@0000:02:00.0       logical name: wlan0       version: 00       serial: 08:3e:8e:3f:63:7b       width: 32 bits       clock: 33MHz       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless       configuration: broadcast=yes driver=rt2800pci driverversion=3.8.0-22-generic firmware=0.34 ip=192.168.0.6 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn       resources: irq:17 memory:f7d00000-f7d0ffff  *-network       description: Ethernet interface       product: AR8161 Gigabit Ethernet       vendor: Qualcomm Atheros       physical id: 0       bus info: pci@0000:03:00.0       logical name: eth0       version: 10       serial: 08:60:6e:99:e2:76       capacity: 1Gbit/s       width: 64 bits       clock: 33MHz       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation       configuration: autonegotiation=on broadcast=yes driver=alx driverversion=1.2.3 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:19 memory:f7c00000-f7c3ffff ioport:e000(size=128)
```
iwconfig```
[COLOR=#222222]wlan0     IEEE 802.11bgn  ESSID:"virginmedia6684984"  [/COLOR]
          Mode:Managed  Frequency:2.437 GHz  Access Point: A0:21:B7:4E:DB:DD             Bit Rate=6.5 Mb/s   Tx-Power=20 dBm             Retry  long limit:7   RTS thr:off   Fragment thr:off          Encryption key:off          Power Management:on          Link Quality=39/70  Signal level=-71 dBm            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0          Tx excessive retries:5531  Invalid misc:165   Missed beacon:0lo        no wireless extensions.
eth0      no wireless extensions.
```Any ideas?

---

