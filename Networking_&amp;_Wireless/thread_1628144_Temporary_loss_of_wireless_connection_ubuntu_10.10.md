---
title: "Temporary loss of wireless connection ubuntu 10.10 and couple versions before"
date: 2010-11-22
forum: Networking &amp; Wireless
---

### Post by Kenny85 on 2010-11-22
I've got that problem since ubuntu 7.10.namely  loosing connection  during surfing the websites..after wee while  network-manager is getting offline and can't show me the list of available wireless connection. 
 When i tried to scann  it throught terminal  ( iwlist wlan0 scanning ) it shows no result. After couple days couple restarts wireless connection starts working but its really annoyiny...here u have list of all usefull commands i guess..
```
**iwconfig**
oot@amilo:/home/kenny# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
vboxnet0  no wireless extensions

[B]lshw -C network
[/B]
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:14:0b:46:c5:43
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.3 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:43 memory:f0788000-f0788fff ioport:30f8(size=8) memory:f0789c00-f0789cff memory:f0789800-f078980f
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 04
       serial: 00:16:44:c2:82:ba
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-22-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:f0400000-f040ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
root@amilo:/home/kenny# oot@amilo:/home/kenny# iwconfig
bash: oot@amilo:/home/kenny#: No such file or directory
root@amilo:/home/kenny# lo        no wireless extensions.
lo: command not found
root@amilo:/home/kenny# 
root@amilo:/home/kenny# eth0      no wireless extensions.
eth0: command not found
root@amilo:/home/kenny# 
root@amilo:/home/kenny# wlan0     IEEE 802.11bg  ESSID:off/any  
wlan0: command not found
root@amilo:/home/kenny#           Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
Mode:Managed: command not found
root@amilo:/home/kenny#           Retry  long limit:7   RTS thr:off   Fragment thr:off
Retry: command not found

[B]lspci
[/B]
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
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 04)


let me know if u need any more details...
```

---

