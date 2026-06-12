---
title: "Can't get Broadcom BCM43XX connected"
date: 2009-03-06
forum: Networking &amp; Wireless
---

### Post by WildMNT on 2009-03-06
Hi. I had this posted a little while ago but got no responses from it.  Rather than bumping it over and over (I hate that) I decided to try and repost it.  

I'm pretty new(b) to Linux and have been reading and trying many things posted here and on the Mint forums, in an attempt to get my wireless working. I'm a Mint user but I can't seem to get my activation password sent to my email to activate my account on the Mint forums, plus there seemed to be a higher response rate over here. Not knowing exactly how different Ubuntu and Mint are in terms of networking, I decided to try and ask for help from here anyways. The Broadcom drivers listed in the hardware drivers app gets my wireless network listed, but cannot connect. Any help would be greatly appreciated, as I have no idea how to fix this, I'm a true Linux newb.

lshw -C Network
```
WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED   
       description: Network controller
       product: BCM43XG
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:05:07.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=32
  *-network:1
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: c
       bus info: pci@0000:05:0c.0
       logical name: eth1
       version: 13
       serial: 00:15:f2:09:c2:0c
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=skge driverversion=1.13 firmware=N/A ip=192.168.1.100 latency=32 maxlatency=31 mingnt=23 module=skge multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ea:05:11:d7:c3:63
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

lspci -nn
```
00:00.0 Memory controller [0580]: nVidia Corporation CK804 Memory Controller [10de:005e] (rev a3)
00:01.0 ISA bridge [0601]: nVidia Corporation CK804 ISA Bridge [10de:0050] (rev a3)
00:01.1 SMBus [0c05]: nVidia Corporation CK804 SMBus [10de:0052] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation CK804 USB Controller [10de:005a] (rev a2)
00:02.1 USB Controller [0c03]: nVidia Corporation CK804 USB Controller [10de:005b] (rev a3)
00:04.0 Multimedia audio controller [0401]: nVidia Corporation CK804 AC'97 Audio Controller [10de:0059] (rev a2)
00:06.0 IDE interface [0101]: nVidia Corporation CK804 IDE [10de:0053] (rev f2)
00:07.0 IDE interface [0101]: nVidia Corporation CK804 Serial ATA Controller [10de:0054] (rev f3)
00:08.0 IDE interface [0101]: nVidia Corporation CK804 Serial ATA Controller [10de:0055] (rev f3)
00:09.0 PCI bridge [0604]: nVidia Corporation CK804 PCI Bridge [10de:005c] (rev a2)
00:0a.0 Bridge [0680]: nVidia Corporation CK804 Ethernet Controller [10de:0057] (rev a3)
00:0b.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3)
00:0c.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3)
00:0d.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3)
00:0e.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: nVidia Corporation G70 [GeForce 7800 GT] [10de:0092] (rev a1)
05:07.0 Network controller [0280]: Broadcom Corporation BCM43XG [14e4:4329] (rev 01)
05:0a.0 RAID bus controller [0104]: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller [1095:3114] (rev 02)
05:0b.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) [104c:8023]
05:0c.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller [11ab:4320] (rev 13)
```

---

