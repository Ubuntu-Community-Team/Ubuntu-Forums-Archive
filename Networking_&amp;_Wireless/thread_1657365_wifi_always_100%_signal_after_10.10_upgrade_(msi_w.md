---
title: "wifi: always 100% signal after 10.10 upgrade (msi wind u100)"
date: 2011-01-01
forum: Networking &amp; Wireless
---

### Post by blueberries on 2011-01-01
hello,

since the upgrade i see all avaible wifi networks as they have 100% signal, both in NetworkManager and Wicd.
in iwconfig and iwlist the signal levels change, but the link quality remains the same: 70/70 (see below). What could be worng? What can i do?

comp. model:
msi wind u100 netbook, ubuntu 10.10, kernel: 2.6.35-24-generic i686

lspci:
```
02:00.0 Network controller: RaLink RT2860
        Subsystem: Micro-Star International Co., Ltd. Device 6890
        Physical Slot: 0-1
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at dfc00000 (32-bit, non-prefetchable) [size=64K]
        Kernel driver in use: rt2800pci
        Kernel modules: rt2860sta, rt2800pci
```

iwconfig (yesterday):
```
wlan0     IEEE 802.11bgn  ESSID:"Dyellin_Buillding_4_k4"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:24:73:66:4E:C0   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          ***Link Quality=70/70  Signal level=-191 dBm  ***
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


iwconfig (few minutes later):
```
wlan0     IEEE 802.11bgn  ESSID:"toya"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:26:5A:7F:CE:20   
          Bit Rate=1 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          ***Link Quality=70/70  Signal level=42 dBm  ***
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

lsmod | grep rt2860sta, rt2800pci
```
rt2860sta             504366  0 
crc_ccitt               1351  2 rt2860sta,rt2800pci
...
rt2800pci               8565  0 
rt2800lib              28897  1 rt2800pci
rt2x00pci               6029  1 rt2800pci
crc_ccitt               1351  2 rt2860sta,rt2800pci
rt2x00lib              27275  4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
eeprom_93cx6            1345  1 rt2800pci
```

lshw -C network:
```
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:24:21:96:84:b6
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.35-24-generic firmware=N/A ip=10.0.0.6 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:dfc00000-dfc0ffff
```


thank you!

---

### Post by Karmic_Kim on 2011-01-23
Just to say that I have the same problem after a new install of 10.10 also on an MSI Wind U100. It is certainly not there with 10.04 which I have still running on another machine. Hardly a show-stopper but I'd love to know if there's a way to fix it.

---

### Post by Gourgi on 2011-01-23
i solved the signal problem by disabling the rt2x* modules and i only use the Ralink's driver 2.1.0.0

to do the same you need to :
create a new file in **/etc/modprobe.d/blacklist-rt2x.conf**
and put the following inside:
```

# This file lists those modules which we don't want to be loaded by
# the ralink wireless adapter rt2860

blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib

```

and restart.
i hope that helps
:popcorn:


edit: also if you want to install the latest driver (2.4) from Ralink look at the instructions in this thread 
[http://ubuntuforums.org/showthread.php?t=1592731](http://ubuntuforums.org/showthread.php?t=1592731)

---

### Post by Karmic_Kim on 2011-01-23
Many thanks Gourgi. The blacklisting didn't work for me so I'll have a look at installing the latest driver. Would be good if it solves the Type n problem also as I've recently installed a Type N modem/router.

---

