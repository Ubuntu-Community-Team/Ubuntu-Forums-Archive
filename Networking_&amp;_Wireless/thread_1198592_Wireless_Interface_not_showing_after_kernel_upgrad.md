---
title: "Wireless Interface not showing after kernel upgrade"
date: 2009-06-27
forum: Networking &amp; Wireless
---

### Post by smithwaysecurity on 2009-06-27
hey everyone I running a HP G60 Ubuntu 9.04  and I got no wireless in-face also my wifi card is saying status unclaimed .
Atheros Communications Inc. AR242x 802.11abg Wireless PCI  is the one that is unclaimed also I just using a usb card for now which wlan1 but still I need to fix this issu
here are some commands print out info because I need some help trying to fix this issue

lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation MCP78S [GeForce 8200] Memory Controller [10de:0754] (rev a2)
00:01.0 ISA bridge [0601]: nVidia Corporation Device [10de:075e] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP78S [GeForce 8200] SMBus [10de:0752] (rev a1)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP78S [GeForce 8200] Co-Processor [10de:0753] (rev a2)
00:01.4 RAM memory [0500]: nVidia Corporation MCP78S [GeForce 8200] Memory Controller [10de:0568] (rev a1)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller [10de:077b] (rev a1)
00:02.1 USB Controller [0c03]: nVidia Corp.oration MCP78S [GeForce 8200] EHCI USB 2.0 Controller [10de:077c] (rev a1)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller [10de:077d] (rev a1)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller [10de:077e] (rev a1)
00:06.0 IDE interface [0101]: nVidia Corporation MCP78S [GeForce 8200] IDE [10de:0759] (rev a1)
00:07.0 Audio device [0403]: nVidia Corporation MCP78S [GeForce 8200] High Definition Audio [10de:0774] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge [10de:075a] (rev a1)
00:09.0 IDE interface [0101]: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) [10de:0ad0] (rev a2)
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP78S [GeForce 8200] Ethernet [10de:0760] (rev a2)
00:0b.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge [10de:0569] (rev a1)
00:14.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge [10de:077a] (rev a1)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration [1022:1300] (rev 40)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Address Map [1022:1301]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h DRAM Controller [1022:1302]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control [1022:1303]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Link Control [1022:1304]
02:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8200M G [10de:0845] (rev a2)
07:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)


root@CIA-laptop:~# lshw -C Network
  *-network               
       description: Ethernet interface
       product: MCP78S [GeForce 8200] Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:16:4e:d9:06
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:1c:df:9d:d9:96
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.100 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 1a:07:2d:59:2b:be
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


root@CIA-laptop:~# uname -rm
2.6.28-13-generic i686
root@CIA-laptop:~# 

root@CIA-laptop:~# uname -rm
2.6.28-13-generic i686
root@CIA-laptop:~# dmesg | grep -e ath -e wlan
[    4.006066] device-mapper: multipath: version 1.0.5 loaded
[    4.006069] device-mapper: multipath round-robin: version 1.0.0 loaded
[   13.363491] udev: renamed network interface wlan0 to wlan1
[   13.857450] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   13.869862] wlan: 0.9.4
[   13.876525] ath_pci: 0.9.4
[   13.876583] ath_pci 0000:07:00.0: PCI INT A -> Link[Z012] -> GSI 23 (level, low) -> IRQ 23
[   13.876596] ath_pci 0000:07:00.0: setting latency timer to 64
[   19.051063] ath_pci 0000:07:00.0: PCI INT A disabled
[   19.085514] ath5k 0000:07:00.0: enabling device (0000 -> 0002)
[   19.085528] ath5k 0000:07:00.0: PCI INT A -> Link[Z012] -> GSI 23 (level, low) -> IRQ 23
[   19.085542] ath5k 0000:07:00.0: setting latency timer to 64
[   19.085619] ath5k 0000:07:00.0: registered as 'phy2'
[   19.095649] ath5k phy2: failed to wakeup the MAC Chip
[   19.095746] ath5k 0000:07:00.0: PCI INT A disabled
[   19.095754] ath5k: probe of 0000:07:00.0 failed with error -5
[   35.697462] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   35.768336] bridge-wlan1: is a Wireless Adapter
[   35.768340] bridge-wlan1: up
[   35.768344] bridge-wlan1: attached
[   35.768369] bridge-wlan1: disabling the bridge
[   35.797014] bridge-wlan1: down
[   35.797018] bridge-wlan1: detached
[   93.090000] wlan1: authenticate with AP f62fe6b8
[   93.097511] wlan1: authenticated
[   93.097514] wlan1: associate with AP f62fe6b8
[   93.104635] wlan1: RX AssocResp from f5ff103e (capab=0x431 status=0 aid=11)
[   93.104638] wlan1: associated
[   93.108831] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   93.109620] bridge-wlan1: is a Wireless Adapter
[   93.109625] bridge-wlan1: up
[   93.109629] bridge-wlan1: attached
[  103.608020] wlan1: no IPv6 routers present
[ 1661.535147] wlan1: beacon loss from AP f62fe6b8 - sending probe request
[ 1669.512040] wlan1: no probe response from AP f62fe6b8 - disassociating
[ 1669.512921] bridge-wlan1: disabling the bridge
[ 1669.513628] bridge-wlan1: down
[ 1669.517442] bridge-wlan1: enabling the bridge
[ 1669.517449] bridge-wlan1: is a Wireless Adapter
[ 1669.517458] bridge-wlan1: up
[ 1669.517487] bridge-wlan1: disabling the bridge
[ 1669.525165] bridge-wlan1: down
[ 1669.525180] bridge-wlan1: detached
[ 1676.154506] wlan1: direct probe to AP f62fe6b8 try 1
[ 1676.352055] wlan1: direct probe to AP f62fe6b8 try 2
[ 1676.355045] wlan1 direct probe responded
[ 1676.355055] wlan1: authenticate with AP f62fe6b8
[ 1676.359649] wlan1: authenticated
[ 1676.359655] wlan1: associate with AP f62fe6b8
[ 1676.361889] wlan1: RX ReassocResp from f503003e (capab=0x431 status=0 aid=11)
[ 1676.361894] wlan1: associated
[ 1676.368247] bridge-wlan1: is a Wireless Adapter
[ 1676.368256] bridge-wlan1: up
[ 1676.368262] bridge-wlan1: attached

---

