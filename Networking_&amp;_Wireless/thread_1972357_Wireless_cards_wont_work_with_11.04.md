---
title: "Wireless cards wont work with 11.04"
date: 2012-05-03
forum: Networking &amp; Wireless
---

### Post by prophet0 on 2012-05-03
Ok for several weeks i have been searching for a solution to this problem on 2 different cards 

WiFi ADP 1: RTL8188CE
WiFi ADP 2: RT2870 (Belkin F5D8053 USB ADP)

lsusb
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0af0:8120 Option 
Bus 001 Device 005: ID 090c:3710 Feiya Technology Corp. Silicon Motion Camera
Bus 001 Device 006: ID 1a40:0101 TERMINUS TECHNOLOGY INC. USB-2.0 4-Port HUB
Bus 003 Device 002: ID 0bda:0002 Realtek Semiconductor Corp. 
Bus 003 Device 003: ID 1aad:000f  
Bus 001 Device 007: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 001 Device 008: ID 1a40:0101 TERMINUS TECHNOLOGY INC. USB-2.0 4-Port HUB
Bus 001 Device 009: ID 050d:815c Belkin Components F5D8053 N Wireless USB Adapter v3000 [Ralink RT2870]

```

lsmod |grep rt2
```

rt2800usb              22300  0 
rt2800lib              48717  1 rt2800usb
crc_ccitt              12595  1 rt2800lib
rt2x00usb              20092  1 rt2800usb
rt2x00lib              48114  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              272785  6 rtl8192ce,rt2800lib,rtl8192c_common,rtlwifi,rt2x00usb,rt2x00lib
cfg80211              172392  3 rtlwifi,rt2x00lib,mac80211

```

lsmod |grep rtl
```

rtl8192ce              75448  0 
rtl8192c_common        69519  1 rtl8192ce
rtlwifi                95614  1 rtl8192ce
mac80211              272785  6 rtl8192ce,rt2800lib,rtl8192c_common,rtlwifi,rt2x00usb,rt2x00lib
cfg80211              172392  3 rtlwifi,rt2x00lib,mac80211

```

both say Disabled by hardware switch 

output of 
lshw -C network
```

  *-network DISABLED      
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 00:0d:f0:9a:06:91
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.0.0-12-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 ioport:e000(size=256) memory:fea00000-fea03fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: 00:13:95:08:60:d1
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:40 ioport:d000(size=256) memory:fe900000-fe900fff memory:d0000000-d0003fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@1:5.3.3
       logical name: wlan1
       serial: 00:1c:df:93:1d:5d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.0.0-12-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn

```

and last but not least 
rfkill list
```

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

Please help none of my wireless adapters are working have searched any tired everything i have found on google/forums 

please note this is on pc and i do not have fn keys thanks

---

### Post by prophet0 on 2012-05-04
If there is anything that i missed please let me know and i can provide an output ](*,)

---

### Post by chili555 on 2012-05-04
I have no doubt that they are not going to work at the same time. Also notice that phy1 is not showing as blocked; I assume it's this one:>  *-network DISABLED
       description: Wireless interface
       [COLOR="Red"]physical id: 1[/COLOR]
       bus info: usb@1:5.3.3
       logical name: wlan1
       serial: 00:1c:df:93:1d:5d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.0.0-12-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgnI suggest you open up the case, remove the internal PCI device and try again. Please be sure to use the usual safety measures.

---

