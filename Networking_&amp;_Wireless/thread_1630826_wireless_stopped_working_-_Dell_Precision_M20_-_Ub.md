---
title: "wireless stopped working - Dell Precision M20 - Ubuntu 10.10 - TKIP, AES"
date: 2010-11-25
forum: Networking &amp; Wireless
---

### Post by aweller on 2010-11-25
Hi all,

My wireless stopped working the other day - I've tried a few (basic) things to get it up and running again to no avail.

I don't think there's a hardware problem as Ubuntu can still see it (and my neighbours' wireless) through Network Manager - it just repeatedly asks for my password (which I enter correctly).

One thing I have done recently - my wireless router's security was set to TKIP (default), I changed this to AES around the time the wireless stopped (to get other hardware working).  Since then I've tinkered with AES, TKIP and TKIPAES on the router to no avail...

```
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
03:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)
```

Any help would be greatly appreciated - it's driving me nuts!

---

### Post by uncaspi on 2010-11-25
Try to figure out which encryptions protocols the card support.
See if can read it in sudo iwlist scan

---

### Post by aweller on 2010-11-26
Thanks for the response, uncaspi.

Does this mean anything to anyone?!  My wireless is "wonky wireless".

```

$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:17:3F:40:5C:80
                    ESSID:"Belkin_N1_Wireless_405C80"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=68/100  Signal level=-59 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 244ms ago
          Cell 02 - Address: 00:1F:FB:0C:1F:00
                    ESSID:"wonky wireless"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:0
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 11 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-13 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 172ms ago
                    Extra: Channel flags: INVALID 
          Cell 03 - Address: 00:19:DB:0E:81:59
                    ESSID:"Hawthorn"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=33/100  Signal level=-80 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 4588ms ago
```

---

### Post by aweller on 2010-11-26
Also:

```
$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:1f:fe:05
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 duplex=full firmware=5751-v3.29a ip=192.168.1.100 latency=0 link=yes multicast=yes port=twisted pair speed=10MB/s
       resources: irq:16 memory:dfcf0000-dfcfffff
  *-network
       description: Wireless interface
       product: PRO/Wireless 2915ABG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:2c:d3:02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:dfbff000-dfbfffff
```

---

### Post by uncaspi on 2010-11-26
I seems to be something with your router settings. Btw you have  low signal strength. Try to increase the txpower of your card and change the channel of your router.

sudo ifconfig eht1 txpower 20 


These setting you've try to set TKIP is only seen at the first network.(Belkin....)
You have

Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP


if that could mean anything

---

### Post by aweller on 2010-11-26
Thanks uncaspi - I changed the channel from "Auto" to "9" and it seems to be working again.  Strange, I didn't touch the channel?!

---

