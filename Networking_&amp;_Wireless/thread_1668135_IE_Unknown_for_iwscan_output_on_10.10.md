---
title: "IE: Unknown: for iwscan output on 10.10"
date: 2011-01-15
forum: Networking &amp; Wireless
---

### Post by lucard on 2011-01-15
I installed a wireless card and it does see the card but when i do a iwscan I get this.
I get a lot of IE: Unknown:
This is on Ubuntu 10.10 server with no GUI. 
I setup scripts to take down and change the interface then put it back up but for this card it does not work.
I have two other wireless devices that do work but i would like to remove then and replace them with this one.
The other two are USB Wifi Sticks.
I am setting this PC to replace a Wifi Router.

**sudo iwlist wlan0 scan**
wlan0     Scan completed :
          Cell 01 - Address: C0:3F:0E:28:B7:28
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-23 dBm  
                    Encryption key:on
                    ESSID:"Pagan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000009aa3cfee7
                    Extra: Last beacon: 3200ms ago
                    IE: Unknown: 0005506167616E
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: DD790050F204104A00011010440001021041000100103B00010310470010AC7E3AB798D8A33E0BD8014BD9F093D51021000D4E4554474541522C20496E632E10230009574E5232303030763210240009574E523230303076321042000230311054000800060050F2040001101100065562756E7475100800020084
                    IE: Unknown: DD090010180202F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B080400000000000000000000000000000000000000

---

### Post by lucard on 2011-01-15
** lshw -C Network**

  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:26:82:58:d8:b9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-22-server firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:18 memory:dfff0000-dfffffff

---

### Post by lucard on 2011-01-15
** uname -r**
2.6.35-22-server

---

