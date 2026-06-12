---
title: "RTL8187 and ndiswrapper"
date: 2009-08-20
forum: Networking &amp; Wireless
---

### Post by greg0ry on 2009-08-20
Previously, I had some bad luck with the internal wireless of my laptop. I purchased a new usb adapter(Rosewill RNX-G1) after reading some reviews that it worked out-of-the-box with Ubuntu 9.04. The adapter uses a Realtek RTL8187 chip.
My experience has not been that good. The default module for the adapter(rtl8187) does not work that well with my system. I get random fluxes in throughput and occasionally the connection stalls or drops completely, which requires a restart to work again. Also the adapter's indicator light does not function correctly using rtl8187, and NetworkManager Applet lists all available networks at 20% strength all the time.
I'm now trying to use ndiswrapper. If I don't use any encryption then everything works great, perfectly even. However, once encryption is involved, even WEP, NetworkManager will not make the connection. I'll post some output below. If anyone has any suggestion or ideas, I would be appreciative.


Output from 'sudo lshw -C network':
 ```
 *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: removed
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: removed
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netrtuw driverversion=1.53+Realtek Semiconductor Corp. link=no multicast=yes wireless=IEEE 802.11g
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: removed
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```Output from 'lsmod | grep -e ndis -e rtl8187':
```
ndiswrapper           193436  0
```Output from 'dmesg | grep -e ndis -e rtl8187':
```
[   13.721687] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   14.300534] ndiswrapper: driver netrtuw (Realtek Semiconductor Corp.,05/18/2007,5.1293.0518.2007) loaded
[   18.165604] usbcore: registered new interface driver ndiswrapper
```Output from 'iwlist scan': Cell 01 is my AP.
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: removed
                    ESSID:""
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:57/100  Signal level:-59 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:01:38:5B:B7:10
                    ESSID:"ShawneeLink-Znaa"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:40/100  Signal level:-70 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:23:97:33:E1:31
                    ESSID:"09FX04045868"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:39/100  Signal level:-71 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

pan0      Interface doesn't support scanning.
```Output from 'sudo iwlist auth':
```
lo        no authentication information.

eth0      no authentication information.

wlan0     Authentication capabilities :
        WPA
        WPA2
        CIPHER-TKIP
        CIPHER-CCMP
          Current WPA version :
        WPA2
          Current Key management :
        PSK
          Current Pairwise cipher :
        none
          Current Pairwise cipher :
        none
          Current Authentication algorithm :
        open


pan0      no authentication information.
```Output from 'ndiswrapper -l':
```
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netrtuw : driver installed
    device (0BDA:8187) present (alternate driver: rtl8187)
```

---

### Post by x22 on 2009-08-20
have you tried the native Linux driver in recent
kernels?

CONFIG_RTL8187 in .config

---

### Post by greg0ry on 2009-08-21
Linux is very new to me, so pardon my ignorance.

> **x22 said:**
> have you tried the native Linux driver in recent
kernels?

The "default module" I mentioned not to be working correctly in my first post --rtl8187, is the only module I've tried --excluding ndiswrapper. It was installed with Ubuntu and automatically takes control of my wireless adapter unless blacklisted. Is this the one you're talking about?

Ubuntu: 9.04 i686
Kernel: 2.6.28-11-generic

---

### Post by greg0ry on 2009-09-04
Bumpy McBumperton.

---

