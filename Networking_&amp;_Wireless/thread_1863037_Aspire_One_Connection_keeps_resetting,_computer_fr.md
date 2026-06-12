---
title: "Aspire One: Connection keeps resetting, computer freezes for 5-10 secs each time"
date: 2011-10-17
forum: Networking &amp; Wireless
---

### Post by Cigue on 2011-10-17
Hi guys, my wireless is broken. It works once in a while (like right now), but depending on the area/time of the day it just breaks. I haven't been able to find out a constant that makes it break, it happen on both the school network and my home network, it happens in some classes during some classes and it works perfectly fine the next week...

I'll paypal $10 to whoever will be able to help me solve my problem. I hope that doesn't sound insultingly low, because I'm a student and I have no monies :(

Laptop : Asus Aspire One AOE255 on Ubuntu 11.04
Kernel/Architecture : 2.6.38-11-generic i686
Using wicd and the default wireless software.

lpsci result :

```
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
```

Nothing plugged in USB

```
IEEE 802.11bgn  ESSID:"wpa.mcgill.ca"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: D8:C7:C8:96:C6:83   
          Bit Rate=54 Mb/s   Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:34  Invalid misc:144   Missed beacon:0
```

lsmod | grep "wlan" returns nothing

dmesg | grep "wlan" returns a lengthy amount of stuff which I PB'd : [http://pastebin.com/2vyZz6MH](http://pastebin.com/2vyZz6MH)

sudo lshw -C network returns :

```
  *-network               
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c1
       serial: 88:ae:1d:6a:d9:fb
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:57000000-5703ffff ioport:5000(size=128)
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 5c:ac:4c:2f:a7:e3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-11-generic firmware=N/A ip=142.157.166.169 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:56000000-5600ffff
```

iwlist scan returns :

```
wlan0     Scan completed :
          Cell 01 - Address: D8:C7:C8:96:C6:83
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"wpa.mcgill.ca"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001e2ca885a7
                    Extra: Last beacon: 95312ms ago
                    IE: Unknown: 000D7770612E6D6367696C6C2E6361
                    IE: Unknown: 01088B8C121618243048
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 3202606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD0A00037F04010000000000
```

Restarting the network :

```
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                                        Ignoring unknown interface wlan0=wlan0.
                                                                                                                       [ OK ]
```

---

