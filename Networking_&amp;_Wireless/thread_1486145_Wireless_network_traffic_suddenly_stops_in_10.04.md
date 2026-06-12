---
title: "Wireless network traffic suddenly stops in 10.04"
date: 2010-05-17
forum: Networking &amp; Wireless
---

### Post by neoclaw on 2010-05-17
My problem is that my wireless network traffic sometimes just stop.
Like when I tries to update my system, update NetBeans or just download using Uget. I have no clue on what's wrong, but any kind of help is welcome! :)


Here is my system info:

Laptop model: ```
Lenovo R500
```
Ubuntu version: ```
Ubuntu 10.04 LTS (64bit)
```
Network card (from lspci): ```
Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
```

iwconfig wlan0 output:
```
wlan0     IEEE 802.11abg  ESSID:"Kasper og Mie"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:26:F2:14:E4:05   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-30 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Wireless driver: ```
"iwlagn"
```

lshw -C network output:
```
  *-network               
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:22:fa:c3:30:6a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.0.12 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:31 memory:f8100000-f8101fff

```

---

### Post by ChadiM on 2010-06-08
Same problem, same wireless driver (iwlagn).

---

