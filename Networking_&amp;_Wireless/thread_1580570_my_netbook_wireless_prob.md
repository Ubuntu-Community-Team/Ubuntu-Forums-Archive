---
title: "my netbook wireless prob"
date: 2010-09-23
forum: Networking &amp; Wireless
---

### Post by hauyuan on 2010-09-23
1. HP Mini 110-3000

2. 02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe

3. wlan0     RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

4. cant find...

5. nothing come out...

6. *-network DISABLED
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt3090 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:17 memory:52000000-5200ffff

7. wlan0     No scan results

8. Description:	Ubuntu 10.04.1 LTS

9. 2.6.32-24-generic i686

10.  * Reconfiguring network interfaces...


i cant see any access point from my router...

---

### Post by jmdlcar on 2010-09-23
Are you looking for this "Ralink 3090 driver"? If so here the link for it [https://launchpad.net/~markus-tisoft/+archive/rt3090/+packages](https://launchpad.net/~markus-tisoft/+archive/rt3090/+packages) Open rt3090 - 1:2.3.1.7-0ubuntu0~ppa2 this is the file name to download rt3090-dkms_2.3.1.7-0ubuntu0~ppa2_all.deb.

---

