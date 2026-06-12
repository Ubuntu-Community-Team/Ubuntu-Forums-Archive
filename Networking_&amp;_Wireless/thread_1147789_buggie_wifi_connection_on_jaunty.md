---
title: "buggie wifi connection on jaunty"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by juje on 2009-05-03
ok, my wifi connection on jaunty it's pretty buggie too...i can only connect thru nm, only wpa, no mac address filter allowed and the transfer rate become slower and slower every second, until i have to restart my pc (half an hour or so, maybe an hour).
My wpa2 connection had been working pretty straight (thanks [wieman01]("http://ubuntuforums.org/showthread.php?t=202834")!) since feisty.
Now, i can't barely open my "/etc/network/interfaces" config file...anything i do there it shut down the wifi connection...

This is my "iwlist scan":

> 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: ***************
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"***************"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000094a2538e
                    Extra: Last beacon: 368ms ago
                    IE: Unknown: 0012582540324232355F356E75774B3331257154
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F4000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


and here is my "lshw -C network"

> 
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:18:f3:f3:ea:78
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: RT2561/RT61 rev B 802.11g
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 00
       serial: **************
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.1.100 latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11bg


any clue how to make this workout?
thanks in advance!

---

