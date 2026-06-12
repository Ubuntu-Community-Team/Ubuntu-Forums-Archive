---
title: "same wireless problem since 8.04 till now 11.10"
date: 2012-03-20
forum: Networking &amp; Wireless
---

### Post by Kenny85 on 2012-03-20
Hi i'm having this problem since i've installed  my first ubuntu (  8.04). i'm surfing through the websites ... watching some movies    anything ....and suddenly im loosing connection .. Network-manager needs authentication when i type hey  it doesnt help when im tryin to restart network manager  it wont list for me available wireless networks..if i type  to the  console iwconfig all parameters ap , essid, Bit rate... all are empty. i do  iwlist wlan0 scanning no results.. nm-tool shows that is configuring .. funny but only thing  which helps is to  resart my laptop..with plugged off power. For the moment  it  works so i give all my details...i wish if someone could finnaly solve it for me ...i gave up..

```
iwconfig
IEEE 802.11bg  ESSID:"salsa"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:1E:2A:6C:E4:F8   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:eek:ff   Fragment thr:eek:ff
          Power Management:eek:ff
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1043   Missed beacon:0
nm-tool
 Type:              802.11 WiFi
  Driver:            ath5k
  State:             connected
  Default:           yes
  HW Address:        00:16:44:C4:82:AA

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *salsa:            Infra, 00:1E:C3:5C:E4:F8, Freq 2457 MHz, Rate 54 Mb/s, Strength 65 WPA2
    NLM:             Infra, 00:26:F2:0B:C2:76, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA

  IPv4 Settings:
    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1
lshw- C network
*-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:14:0b:46:c5:43
       capacity: 100Mbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth  driverversion=0.64 latency=0 maxlatency=20 mingnt=1 multicast=yes  port=MII
       resources: irq:43 memory:f0788000-f0788fff ioport:30f8(size=:cool: memory:f0789c00-f0789cff memory:f0789800-f078980f
  *-network
       description: Wireless interface
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 04
       serial: 00:16:44:c2:82:ba
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k  driverversion=3.0.0-16-generic firmware=N/A ip=192.168.1.5 latency=0  multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f0400000-f040ffff

uname -a 
Linux amilo 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:49:42 UTC 2012 i686 athlon i386 GNU/Linux

lspci

00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 SATA controller: nVidia Corporation MCP67 SATA Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M G] (rev a1)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 04)


dmesg[28871.485100] init: modemmanager main process ended, respawning
[28871.494897] init: modemmanager main process (12201) terminated with status 255
[28871.494940] init: modemmanager main process ended, respawning
[28871.502617] init: modemmanager main process (12203) terminated with status 255
[28871.502662] init: modemmanager respawning too fast, stopped
[28871.636314] init: network-manager main process (12185) killed by ABRT signal
[28871.636370] init: network-manager main process ended, respawning
[28871.643927] init: modemmanager main process (12205) terminated with status 255
[28871.643980] init: modemmanager main process ended, respawning
[28871.654524] init: modemmanager main process (1220:cool: terminated with status 255
[28871.654569] init: modemmanager main process ended, respawning
[28871.664846] init: modemmanager main process (12211) terminated with status 255
[28871.664889] init: modemmanager main process ended, respawning
[28871.673037] init: modemmanager main process (12213) terminated with status 255
[28871.673082] init: modemmanager main process ended, respawning
[28871.688585] init: modemmanager main process (12215) terminated with status 255
[28871.688643] init: modemmanager main process ended, respawning
[28871.695826] init: modemmanager main process (12217) terminated with status 255
[28871.695884] init: modemmanager main process ended, respawning
[28871.706585] init: modemmanager main process (12219) terminated with status 255
[28871.706628] init: modemmanager main process ended, respawning
[28871.716529] init: modemmanager main process (12221) terminated with status 255
[28871.716583] init: modemmanager main process ended, respawning
[28871.727678] init: modemmanager main process (12223) terminated with status 255
[28871.727737] init: modemmanager main process ended, respawning
[28871.738184] init: modemmanager main process (12225) terminated with status 255
[28871.738236] init: modemmanager main process ended, respawning
[28871.748884] init: modemmanager main process (12227) terminated with status 255
[28871.748927] init: modemmanager respawning too fast, stopped
[28871.880297] init: network-manager main process (12209) killed by ABRT signal
[28871.880342] init: network-manager respawning too fast, stopped
```


Please help  that is killing me softly...
Many thanks  for any useful tips

---

### Post by howefield on 2012-03-20
Thread closed.

Duplicate here : [http://ubuntuforums.org/showthread.php?p=11778210#post11778210](http://ubuntuforums.org/showthread.php?p=11778210#post11778210)

---

