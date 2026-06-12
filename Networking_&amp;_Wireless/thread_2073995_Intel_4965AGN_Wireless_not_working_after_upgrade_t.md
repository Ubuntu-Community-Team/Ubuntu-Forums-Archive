---
title: "Intel 4965AGN Wireless not working after upgrade to 12.10"
date: 2012-10-20
forum: Networking &amp; Wireless
---

### Post by jmperkins on 2012-10-20
Wireless working fine with 12.04. 

After upgrading from 12.04 to 12.10, can only use ethernet connection.

When I try to connect to any wireless SSID, I receive message:

_Failed to add/activate connection_

_(32) None of the registered plugins support add_


Network card is INTEL PRO Wireless 4965AGN

---

### Post by jmperkins on 2012-10-21
Additional info:

sudo lshw -C network

  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 61
       serial: 00:13:e8:6d:7a:ad
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 driverversion=3.2.0-30-generic firmware=228.61.2.24 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:47 memory:fa000000-fa001fff
  *-network
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 16
       serial: 00:13:a9:c2:f1:49
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full firmware=N/A ip=192.168.0.5 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:fc200000-fc203fff ioport:5000(size=256)
  *-network
       description: Ethernet interface
       physical id: 1
       bus info: usb@2:2
       logical name: eth1
       serial: 6a:09:27:5c:b2:11
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ipheth link=no multicast=yes

Can connect via Ethernet Cable

---

### Post by heavenbender on 2012-10-23
Similar problem here too. 

Upgraded from 12.04 to 12.10 on a Dell Inspiron 1525 using ubuntu's inbuilt updater. Wireless connections show up, but unable to add them. 

Error: Failed to add/activate connection (32) None of the registered plugins support add. 

Last I checked a bug report had been filed for the wubi, but any luck with solutions for this?

---

### Post by cmw on 2012-10-29
I'm having the same problem.  System was behaving with Ubuntu 12.04.  After upgrading to 12.10 my internal Intel WLAN card is no longer detected.  My USB Alfa AWUS036NH is only detected if an ethernet cable is plugged in during boot.  If the system boots with no ethernet cable plugged in, no WLAN cards (internal or USB) are detected.

Additional info:

  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:90:f5:8d:42:b9
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.134 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:46 ioport:3000(size=256) memory:f3100000-f3100fff memory:f8000000-f800ffff memory:f8020000-f803ffff
  *-network DISABLED
       description: Wireless interface
       product: Ultimate N WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 00
       serial: 00:16:ea:5f:da:c5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.5.0-17-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:47 memory:f3000000-f3001fff

---

### Post by jmperkins on 2012-11-08
I wouldn't have upgraded to 12.10 from 12.04 if I knew I would lose my wireless capability....I can't travel with this laptop any more so it is a REAL inconvenience.  As an interim solution, I would purchase a LINKSYS AE1200 wireless adapter and use its windows provided driver assuming this is a problem specifically with the INTEL 4965AGN?

---

### Post by chili555 on 2012-11-08
> **jmperkins said:**
> I wouldn't have upgraded to 12.10 from 12.04 if I knew I would lose my wireless capability....I can't travel with this laptop any more so it is a REAL inconvenience.  As an interim solution, I would purchase a LINKSYS AE1200 wireless adapter and use its windows provided driver assuming this is a problem specifically with the INTEL 4965AGN?Let's gather some troubleshooting information. Please detach the ethernet and run and post:```
dmesg | grep iwl
rfkill list all
iwconfig
sudo iwlist wlan0 scan
cat /etc/network/interfaces
```

---

### Post by jmperkins on 2012-11-09
Thank you Chilli555 as I will post the output of the commands when I get home to my laptop tonight!

---

### Post by jmperkins on 2012-11-09
joe@joe-VGN-FZ140E:~$[COLOR=Red] dmesg | grep iwl[/COLOR]
[34692.403131] iwl4965 0000:06:00.0: RF_KILL bit toggled to disable radio.
[34692.432052] iwl4965 0000:06:00.0: Not sending command - RF KILL
[34692.432058] iwl4965 0000:06:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[34692.432063] iwl4965 0000:06:00.0: Error setting new RXON (-5)
[34692.436008] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 1 [0xa5a5a5a2]
[34692.436008] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 3 [0xa5a5a5a2]
[34692.436008] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 4 [0xa5a5a5a2]
[34692.436008] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 6 [0xa5a5a5a2]
[34695.744224] iwl4965 0000:06:00.0: RF_KILL bit toggled to enable radio.
[35752.821593] iwl4965 0000:06:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[35752.821645] iwl4965 0000:06:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xfa000004)
[35752.821664] iwl4965 0000:06:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[35752.821681] iwl4965 0000:06:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100506)
[39733.657592] iwl4965 0000:06:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[39733.657635] iwl4965 0000:06:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xfa000004)
[39733.657649] iwl4965 0000:06:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[39733.657670] iwl4965 0000:06:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100506)
[42012.569598] iwl4965 0000:06:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[42012.569641] iwl4965 0000:06:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xfa000004)
[42012.569655] iwl4965 0000:06:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[42012.569672] iwl4965 0000:06:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100506)
[44411.221670] iwl4965 0000:06:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[44411.221713] iwl4965 0000:06:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xfa000004)
[44411.221727] iwl4965 0000:06:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[44411.221744] iwl4965 0000:06:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100506)
[46994.597589] iwl4965 0000:06:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[46994.597631] iwl4965 0000:06:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xfa000004)
[46994.597645] iwl4965 0000:06:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[46994.597672] iwl4965 0000:06:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100506)
[55370.337597] iwl4965 0000:06:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[55370.337644] iwl4965 0000:06:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xfa000004)
[55370.337658] iwl4965 0000:06:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[55370.337675] iwl4965 0000:06:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100506)
[57746.521595] iwl4965 0000:06:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[57746.521637] iwl4965 0000:06:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xfa000004)
[57746.521651] iwl4965 0000:06:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[57746.521668] iwl4965 0000:06:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100506)


joe@joe-VGN-FZ140E:~$ [COLOR=Red]rfkill list all[/COLOR]
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


joe@joe-VGN-FZ140E:~$ [COLOR=Red]iwconfig[/COLOR]
lo        no wireless extensions.

vboxnet0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

[COLOR=Red]
too much data output below (no cell 00-01 thru 07 shown)for terminal program via "sudo iwlist wlan0 scan":[/COLOR]
                     IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B00010310470010357384699CE53281CC6D54CC8FCDCAFA10210005436973636F1023000D4C696E6B7379732045323530301024000776312E302E30331042000234321054000800060050F20400011011000D4C696E6B737973204532353030100800020084103C000103
                    IE: Unknown: DD090010180202F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 08 - Address: A4:7A:A4:0C:FE:B0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"ATT432"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000149d9c66893
                    Extra: Last beacon: 1752ms ago
                    IE: Unknown: 0006415454343332
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180200F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: 00:24:56:72:19:21
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"2WIRE879"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000008db13c2f117
                    Extra: Last beacon: 1508ms ago
                    IE: Unknown: 00083257495245383739
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD900050F204104A0001101044000102103B00010210470010303030303936303931393038323837391021000B32576972652C20496E632E10230011323730314847562D42204761746577617910240011323730314847562D4220476174657761791042000C3936303931393038323837391054000800060050F20400011011000A686F6D65706F7274616C10080002008E
          Cell 10 - Address: 20:AA:4B:C1:D1:9D
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"You kids, get off my lawn!"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000284fec7d85f
                    Extra: Last beacon: 524ms ago
                    IE: Unknown: 001A596F75206B6964732C20676574206F6666206D79206C61776E21
                    IE: Unknown: 01088C129824B048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AFE081EFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D16950D0000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B00010310470010357384699CE53281CC6D54CC8FCDCAFA10210005436973636F1023000D4C696E6B7379732045323530301024000776312E302E30331042000234321054000800060050F20400011011000D4C696E6B737973204532353030100800020084103C000103
                    IE: Unknown: DD090010180200F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 11 - Address: 7C:BF:B1:30:8B:A0
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"ChelseaFC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000007cc4eb183
                    Extra: Last beacon: 1448ms ago
                    IE: Unknown: 00094368656C7365614643
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180201F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 12 - Address: E8:6D:52:A8:11:D0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"ATT616"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000011a0b9d183
                    Extra: Last beacon: 1660ms ago
                    IE: Unknown: 0006415454363136
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180200F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 13 - Address: 2C:B0:5D:FC:29:C2
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"YJ"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 1468ms ago
                    IE: Unknown: 0002594A
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: DD760050F204104A0001101044000102103B0001031047001036A58A43DF4C700931230321FDFCCFB5102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F2040001101100094E6574676561724150100800020088103C000101
                    IE: Unknown: DD090010180202F00C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 14 - Address: 40:B7:F3:46:A3:A0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"ATT728"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000026e46a44ede
                    Extra: Last beacon: 1712ms ago
                    IE: Unknown: 0006415454373238
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180200F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 15 - Address: C0:3F:0E:59:C2:B0
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Coronado"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000115adab4198
                    Extra: Last beacon: 1452ms ago
                    IE: Unknown: 0008436F726F6E61646F
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B000103104700101AE66E128518EE6351D23D9DA1A5F8CD1021000D4E4554474541522C20496E632E10230009574752363134763130102400095747523631347631301042000538333235381054000800060050F204000110110009574752363134763130100800020084
                    IE: Unknown: DD090010180201F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 16 - Address: 08:86:3B:92:C7:1B
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Gosu.5GHz"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004ade6b2040
                    Extra: Last beacon: 1280ms ago
                    IE: Unknown: 0009476F73752E3547487A
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400030000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AFE081AFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D16280F0000000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180200F0040000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 17 - Address: 00:25:3C:EF:41:C1
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"2WIRE590"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a731c1c3f6
                    Extra: Last beacon: 1568ms ago
                    IE: Unknown: 00083257495245353930
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030108
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 18 - Address: 00:1D:7E:17:74:B4
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Snuggle #306"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000138c8a8183
                    Extra: Last beacon: 1544ms ago
                    IE: Unknown: 000C536E7567676C652023333036
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F5000000
          Cell 19 - Address: 08:86:3B:92:C7:19
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"Gosu"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004ade7f6e38
                    Extra: Last beacon: 1724ms ago
                    IE: Unknown: 0004476F7375
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: DDA20050F204104A00011010440001021041000100103B0001031047001019331A26BC6AE03315D4B210E5DB33621021001442656C6B696E20496E7465726E6174696F6E616C1023000A46394B3131303520763110240007312E30302E30361042000E31323131343747453130303635381054000800060050F20400011011001D42656C6B696E204E343530444220576972656C65737320526F75746572100800020084
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 20 - Address: 00:1C:DF:CE:AB:DE
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"lpkm2004"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000015fafc66183
                    Extra: Last beacon: 1656ms ago
                    IE: Unknown: 00086C706B6D32303034
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD970050F204104A0001101044000102103B00010210470010E7FE1B918CD5031098DD001CDFCEABDE1021000642656C6B696E1023000F463544373233302D342D763830303010240007575053303030311042000E32303832323732333030363133331054000800060050F204000110110020463544373233302D340000000000000000000000000000000000000000000000100800020084
                    IE: Unknown: DD090010180201F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 21 - Address: 4A:44:F7:52:16:4E
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-zc[TV]teaser"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000003fd6de72c
                    Extra: Last beacon: 1584ms ago
                    IE: Unknown: 00134449524543542D7A635B54565D746561736572
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1013FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606070000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: 0706530049012310
                    IE: Unknown: DD9D0050F204104A0001101044000102103B00010310470010BC329E001DD811B286014844F752164E1021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800070050F20400011011000952616C696E6B41505310080002018C103C000101
                    IE: Unknown: DD07000C4304000000
          Cell 22 - Address: 2C:B0:5D:DF:77:26
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Vendal WiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000152adec3205
                    Extra: Last beacon: 1496ms ago
                    IE: Unknown: 000B56656E64616C2057694669
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010A
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160A080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180202F00C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 23 - Address: 40:B7:F3:5D:B8:50
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"ATT352"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000037f3374a90
                    Extra: Last beacon: 1472ms ago
                    IE: Unknown: 0006415454333532
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180200F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 24 - Address: A0:21:B7:6F:79:BA
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"The AL'S"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000599947e4da
                    Extra: Last beacon: 1452ms ago
                    IE: Unknown: 000854686520414C2753
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 05050001004001
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180208F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00



joe@joe-VGN-FZ140E:~$ [COLOR=Red]cat /etc/network/interfaces[/COLOR]
auto lo
iface lo inet loopback
auto eth0
 iface eth0 inet dhcp
joe@joe-VGN-FZ140E:~$ 

[COLOR=Red]THANKS FOR YOUR HELP. Let me know what else I MIGHT PROVIDE.[/COLOR]

---

### Post by chili555 on 2012-11-09
> [34692.432058] iwl4965 0000:06:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[34692.432063] iwl4965 0000:06:00.0: Error setting new RXON (-5)
[34692.436008] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 1 [0xa5a5a5a2]
[34692.436008] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 3 [0xa5a5a5a2]
[34692.436008] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 4 [0xa5a5a5a2]
[34692.436008] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 6 [0xa5a5a5a2]Very ugly. Are you sure you're running 12.10? In my 12.10 install, it reports:> chili@LAPTOP410:~$ modinfo iwl4965
ERROR: modinfo: could not find module iwl4965Please let us see:```
lsb-release -d
modinfo iwl4965 | grep -i version
uname -r
```

---

### Post by jmperkins on 2012-11-10
I did an upgrade from 12.04 to 12.10 using the software updater:

joe@joe-VGN-FZ140E:~$ lsb_release -d
Description:    Ubuntu 12.10

joe@joe-VGN-FZ140E:~$ modinfo iwl4965 | grep -i version
version:        in-tree:
srcversion:     E3D7B995B1C47AE1CDDEA08
vermagic:       3.2.0-30-generic SMP mod_unload modversions 686 

joe@joe-VGN-FZ140E:~$ uname -r
3.2.0-30-generic

---

### Post by chili555 on 2012-11-10
> joe@joe-VGN-FZ140E:~$ uname -r
3.2.0-30-genericKernel version 3.2.0.xx corresponds to 12.04. My 12.10 install says:```
chili@LAPTOP410:~$ uname -r
[COLOR="Red"]3.5.0-18[/COLOR]-generic
```When you boot, does the GRUB menu appear? Can you select kernel version 3.5.0.xx?

I hope we don't have to dig into your GRUB configuration. Yikes.

Please see attached.

---

### Post by SergG on 2012-11-13
if you have a bug:


Failed to add / activate connection
(32) None of the registered plugins support hell


My English is bad, sorry.
go to the folder /etc/NetworkManager (using sudo) and delete all files !!!EXCEPT!!! NetworkManager.conf and subfolders. Then open NetworkManager.conf and check the contents:


[main]
plugins = ifupdown, keyfile
dns = dnsmasq


[ifupdown]
managed = **[COLOR=#483d8b]false[/COLOR]**




and reboot

---

### Post by jmperkins on 2012-11-15
> **chili555 said:**
> Kernel version 3.2.0.xx corresponds to 12.04. My 12.10 install says:```
chili@LAPTOP410:~$ uname -r
[COLOR=Red]3.5.0-18[/COLOR]-generic
```When you boot, does the GRUB menu appear? Can you select kernel version 3.5.0.xx?

I hope we don't have to dig into your GRUB configuration. Yikes.

Please see attached.

I am only offered  the 3.2.0.XX in my GRUB Menu (no other versions to choose from).

---

### Post by chili555 on 2012-11-15
Then something has gone awry in your upgrade to 12.10. When you open Synaptic Package Manager, are there 3.5.0-xx kernels available to install? I'd suggest you install the newest available and boot into it. I suspect your wireless troubles will be gone.

My fully updated 12.10 system runs:> $ uname -r
3.5.0-18-generic


---

### Post by jmperkins on 2012-11-15
> **chili555 said:**
> Kernel version 3.2.0.xx corresponds to 12.04. My 12.10 install says:```
chili@LAPTOP410:~$ uname -r
[COLOR=Red]3.5.0-18[/COLOR]-generic
```When you boot, does the GRUB menu appear? Can you select kernel version 3.5.0.xx?

I hope we don't have to dig into your GRUB configuration. Yikes.

Please see attached.

I only have a choice of 3.2.0.xx when the GRUB Menu appears.

---

### Post by kurt18947 on 2012-11-16
> **jmperkins said:**
> I only have a choice of 3.2.0.xx when the GRUB Menu appears.

Failed upgrade?  You wouldn't be the first, which is why some people only do fresh installs.  Did you try a live install? Live CD or Live USB?  If your network adapter works in a live install of 12.10, plus the absence of a 3.5.x kernel would indicate a flawed upgrade.

---

### Post by jmperkins on 2012-11-16
> **SergG said:**
> if you have a bug:


Failed to add / activate connection
(32) None of the registered plugins support hell


My English is bad, sorry.
go to the folder /etc/NetworkManager (using sudo) and delete all files !!!EXCEPT!!! NetworkManager.conf and subfolders. Then open NetworkManager.conf and check the contents:


[main]
plugins = ifupdown, keyfile
dns = dnsmasq


[ifupdown]
managed = **[COLOR=#483d8b]false[/COLOR]**




and reboot

joe@joe-VGN-FZ140E:/etc/NetworkManager$ dir
dispatcher.d  dnsmasq.d  system-connections  VPN
joe@joe-VGN-FZ140E:/etc/NetworkManager$

---

### Post by chili555 on 2012-11-16
> **chili555 said:**
> Then something has gone awry in your upgrade to 12.10. When you open Synaptic Package Manager, are there 3.5.0-xx kernels available to install? I'd suggest you install the newest available and boot into it. I suspect your wireless troubles will be gone.Did you check this?

---

### Post by jmperkins on 2012-11-16
> **chili555 said:**
> Did you check this?
 
I did look for the newer kernel but didn't see it in the list. Do you know what the title is specifically or what letters it begins with? 
 
That would be terrific if running under a newer kernel would resolve this!

---

### Post by chili555 on 2012-11-16
Something like attached, perhaps. You should look for 'linux-image-3.5.0-xx.' I recommend the latest, that is, the highest number. Once you select it, I'd also select 'linux-image-generic' with a matching version.

---

### Post by jmperkins on 2012-11-16
> **chili555 said:**
> Something like attached, perhaps. You should look for 'linux-image-3.5.0-xx.' I recommend the latest, that is, the highest number. Once you select it, I'd also select 'linux-image-generic' with a matching version.
 
THANK YOU  very much as I will look for the Linux image tonight after work! Cross your fingers for me that this will resolve my problem.

---

### Post by chili555 on 2012-11-16
> Cross your fingers for me that this will resolve my problem.Done!

---

### Post by jmperkins on 2012-11-17
> **chili555 said:**
> Something like attached, perhaps. You should look for 'linux-image-3.5.0-xx.' I recommend the latest, that is, the highest number. Once you select it, I'd also select 'linux-image-generic' with a matching version.

I did find the 3.5.0.18 kernel, installed it and booting with it, I still get the error when attempting to connect to wireless. My GRUB Menu will not refresh even though I tried several different things.

I agree with your earlier comment in that the 12.10 upgrade from 12.04 went sour.

I'm going to pursue a fresh install of 12.10 once I get a good backup of my current data.

Thanks for ALL your HELP!

---

### Post by chili555 on 2012-11-17
> I'm going to pursue a fresh install of 12.10 once I get a good backup of my current data.I hope it will work well for you. Post back if your wireless isn't working as expected. We'll be glad to help you.

---

