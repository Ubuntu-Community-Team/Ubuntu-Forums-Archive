---
title: "Wifi only connects when ethernet cable is plugged in"
date: 2009-08-17
forum: Networking &amp; Wireless
---

### Post by sethier on 2009-08-17
Ok, so here it is:

I have a machine with both Wireless and Ethernet cards installed, and I know that both work fine because I am able to ping both cards.

The Wired card has IP 192.068.0.4
The Wireless card has IP 192.168.0.3

When Ethernet cable is connected I can ping both address fine, and when I disconnect the Ethernet cable I continue to get responses from the wireless card. 

On first boot, (after disconnecting the Ethernet) I am continuously pinging both IPs and after waiting 10 minutes or so I am still getting no response from both. However once I connect the Ethernet cable, at the same time I start getting responses from both addresses. At this point if I disconnect the Ethernet cable the wireless stays active...

I am hoping to install the PC somewhere where a wired connection will not be possible.  So I would like to have the PC go online using the Wireless only. Is there anything I am doing wrong here? Here are all the specs, please let me know if you require more:

$ sudo lshw -C Network
[sudo] password for sethier:
  *-network:0
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: wifi0
       version: 01
       serial: 00:15:e9:3f:83:70
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.0.3 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: ADMtek
       physical id: 13
       bus info: pci@0000:00:13.0
       logical name: eth0
       version: 11
       serial: 00:04:5a:66:46:d3
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.0.4 latency=64 maxlatency=255 mingnt=255 module=tulip multicast=yes

$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:1B:11:67:6C:C9
                    ESSID:"Believe"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=63/70  Signal level=-32 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    Extra:ath_ie=dd0900037f0101000eff7f

$ sudo lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge [8086:7190] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge [8086:7191] (rev 03)
00:07.0 ISA bridge [0601]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 02)
00:07.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
00:07.2 USB Controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112] (rev 01)
00:07.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 02)
00:11.0 Multimedia audio controller [0401]: Ensoniq ES1371 [AudioPCI-97] [1274:1371] (rev 06)
00:12.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)
00:13.0 Ethernet controller [0200]: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 [1317:0985] (rev 11)
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 86C326 5598/6326 [1039:6326] (rev 0b)

---

