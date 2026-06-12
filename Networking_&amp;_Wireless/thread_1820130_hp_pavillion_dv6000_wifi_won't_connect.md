---
title: "hp pavillion dv6000 wifi won't connect"
date: 2011-08-07
forum: Networking &amp; Wireless
---

### Post by ravengirl1960 on 2011-08-07
I'm running dual boot, Windows 7 and Zorin. The Windows Wifi side works fine. The install for Zorin (including updates, programs I selected from the repos, etc) worked fine, but now I can't connect to the net.

It recognizes my router (Belkin), recognizes other networks (neighbors, school), and it says I'm connected but anything to do with the net (firefox, chrome, synaptic, etc) won't connect.

Checking lspci, I get:

pgirl@leslie-nest:~$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0547] (rev a2)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP67 ISA Bridge [10de:0548] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP67 SMBus [10de:0542] (rev a2)
00:01.2 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0541] (rev a2)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP67 Co-processor [10de:0543] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:06.0 IDE interface [0101]: nVidia Corporation MCP67 IDE Controller [10de:0560] (rev a1)
00:07.0 Audio device [0403]: nVidia Corporation MCP67 High Definition Audio [10de:055c] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Bridge [10de:0561] (rev a2)
00:09.0 IDE interface [0101]: nVidia Corporation MCP67 AHCI Controller [10de:0550] (rev a2)
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP67 Ethernet [10de:054c] (rev a2)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:0d.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:12.0 VGA compatible controller [0300]: nVidia Corporation C67 [GeForce 7150M / nForce 630M] [10de:0531] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
02:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
02:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
02:05.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
02:05.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
pgirl@leslie-nest:~$ 


- Device: wlan0  [PenguinPower] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             connected
  Default:           no
  HW Address:        00:1F:E2:A7:5C:F8

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    karenniphu-guest:Infra, C0:C1:C0:DF:6A:8E, Freq 2462 MHz, Rate 54 Mb/s, Strength 27
    PenguinPower:    Infra, 00:22:75:5D:46:B2, Freq 2412 MHz, Rate 54 Mb/s, Strength 92
    coke:            Infra, 00:25:9C:59:CB:65, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA
    karenniphu:      Infra, C0:C1:C0:DF:6A:8D, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    Dahir:           Infra, 00:24:A0:D4:CB:5E, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA
    fowiza1:         Infra, 00:24:A0:E8:EE:51, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA                                                                                                        
    Whitemonson:     Infra, E0:91:F5:B4:30:59, Freq 2412 MHz, Rate 54 Mb/s, Strength 82 WPA WPA2                                                                                                   
    *PenguinPower:   Ad-Hoc, 8E:18:37:65:8E:2D, Freq 2412 MHz, Rate 0 Mb/s, Strength 255                                                                                                           
                                                                                                                                                                                                   
  IPv4 Settings:                                                                                                                                                                                   
    Address:         10.42.43.1                                                                                                                                                                    
    Prefix:          24 (255.255.255.0)                                                                                                                                                            
    Gateway:         0.0.0.0

---

### Post by chili555 on 2011-08-07
> PenguinPower: Ad-Hoc, 8E:18:37:65:8E:2D, Freq 2412 MHz, Rate 0 Mb/s, Strength 255

IPv4 Settings:
Address: 10.42.43.1
Prefix: 24 (255.255.255.0)
Gateway: 0.0.0.0Is PenguinPower another computer that you want to connect to in an internet connection sharing scheme? That's how your settings look. Is it actually your Belkin router? Notice that all the other access points, probably routers, in your scan are set to 'Infra.' PenguinPower is evidently set to Ad Hoc. If it is an ordinary router, it ought to be set for Infrastructure.

Then, on your computer, click the Network Manager icon, Edit Connections, select Wireless and make sure you are set to Infrastructure as well. Please see attached.

Notice you have a 10.42.xx address. That's typical of ad-hoc internet connection sharing. I doubt that's what you intend.

---

