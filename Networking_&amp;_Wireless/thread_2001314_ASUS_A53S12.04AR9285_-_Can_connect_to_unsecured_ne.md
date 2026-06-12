---
title: "ASUS A53S/12.04/AR9285 - Can connect to unsecured networks, but not WPA2"
date: 2012-06-10
forum: Networking &amp; Wireless
---

### Post by polong on 2012-06-10
[LIST]
[*]Dual booting Ubuntu 12.04 64-bit with Win7
[*]Previously fixed WPA2 on 11.04 from this thread: [http://ubuntuforums.org/showthread.php?t=1836867](http://ubuntuforums.org/showthread.php?t=1836867), but doesn't work on 12.04
[*]Win7 can connect to all networks
[*]Currently Ubuntu is connected to an unsecured network
[*]WPA Supplicant is installed
[/LIST]

                                  lshw -C network
  ```
 *-network                
        description: Wireless interface 
        product: AR9285 Wireless Network Adapter (PCI-Express) 
        vendor: Atheros Communications Inc. 
        physical id: 0 
        bus info: pci@0000:03:00.0 
        logical name: wlan0 
        version: 01 
        serial: 48:5d:60:be:60:a8 
        width: 64 bits 
        clock: 33MHz 
        capabilities: bus_master cap_list ethernet physical wireless 
        configuration: broadcast=yes driver=ath9k driverversion=3.2.0-23-generic
 firmware=N/A ip=172.18.23.98 latency=0 multicast=yes wireless=IEEE 802.11bgn 
        resources: irq:17 memory:de200000-de20ffff
  
```                                  sudo iwlist scan (of the network I want to connect to)
```
Address: 00:0B:86:3C:33:30 
                     Channel:1 
                     Frequency:2.412 GHz (Channel 1) 
                     Quality=42/70  Signal level=-68 dBm   
                     Encryption key:on 
                     ESSID:"UWresnet" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 
                               11 Mb/s; 12 Mb/s; 18 Mb/s 
                     Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s 
                     Mode:Master 
                     Extra:tsf=00000003a7794181 
                     Extra: Last beacon: 920ms ago 
                     IE: Unknown: 000855577265736E6574 
                     IE: Unknown: 010882840B0C12161824 
                     IE: Unknown: 030101 
                     IE: Unknown: 2A0102 
                     IE: Unknown: 32043048606C 
                     IE: IEEE 802.11i/WPA2 Version 1 
                         Group Cipher : TKIP 
                         Pairwise Ciphers (1) : CCMP 
                         Authentication Suites (1) : 802.1x 
                     IE: WPA Version 1 
                         Group Cipher : TKIP 
                         Pairwise Ciphers (1) : TKIP 
                         Authentication Suites (1) : 802.1x 
                     IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00 
                     IE: Unknown: DD0A00037F04010000000000 
  
```Any help or insight is greatly appreciated!

---

