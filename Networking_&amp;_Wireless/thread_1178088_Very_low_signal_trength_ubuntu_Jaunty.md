---
title: "Very low signal trength ubuntu Jaunty"
date: 2009-06-04
forum: Networking &amp; Wireless
---

### Post by Sisco88 on 2009-06-04
hi there!

before Jaunty i always used ubuntu 8.10 and always had 80-100% signal strength. ever since i did a clean install of 9.04 the signal strength of my wireless network is very low (10-15%) and alot of the time web pages wont load because of it.
I'm using the wicd network manager because the original one kept freezing the system, wich is not the problem. the original netword manager had the same low signal strength.

lspci:

```
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
```lshw -C network:
```

  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:43:1d:98:d8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=145.74.183.19 latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn

```my other desktop that runs Vista has full signal strength, and the notebook never gets over 15% even when im sitting right next to the wireless router.

can anybody help me with this?

thanks,

Sisco

---

### Post by patioheater on 2009-06-06
Very same problem here, wondering if the IPv6 will do it, tho there's no mention of IPv6 in my wireless menu

02:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

---

### Post by patioheater on 2009-06-06
:pwicd seems to have sorted my problem for the time being

---

### Post by alexander_s on 2009-06-16
Same issue here.
My reception starts around 30% at boot time, but usually hovers around 8% while neighbors appear full strength or close
any suggestions?

---

### Post by alexander_s on 2009-06-16
Bump. anyone?
will this help?

alexander@alexander-laptop:~$ sudo iwconfig
[sudo] password for alexander: 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Zhitomir"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:17:3F:BE:EB:63   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:D192-5E0B-E8AC-8C13-24C9-88B9-D33F-1629-3475-C660-44F2-D59D-3264-BA45-35B3-B4E8 [2]   Security mode:open
          Power Management:off
          Link Quality=10/100  Signal level:-182 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

