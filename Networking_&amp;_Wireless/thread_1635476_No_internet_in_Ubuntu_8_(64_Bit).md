---
title: "No internet in Ubuntu 8 (64 Bit)"
date: 2010-12-01
forum: Networking &amp; Wireless
---

### Post by naushad97 on 2010-12-01
I have a airtel broadband connection (Dynamic IP). After installing Ubuntu 8 on my Dell studio 15 laptop (i3 processor) I am not able to connect to the internet (this is the only ubuntu that works on my system in dual boot with windows7).
In any other flavour of liunx, the internet connection is recognized as soon as I plug in the Internet cable.
Please help me to fix this problem.

---

### Post by uncaspi on 2010-12-02
Please post the content of sudo lshw -C network
lsusb and lspci -nn

---

### Post by naushad97 on 2010-12-04
```

naushad@nash:~$ sudo lshw -C network
[sudo] password for naushad: 
  *-network UNCLAIMED     
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 03
       serial: b8:ac:6f:53:bd:b3
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical fibre 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full latency=0 link=no module=r8169 multicast=yes port=fibre speed=1GB/s

naushad@nash:~$ sudo lsusb
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 413c:8162 Dell Computer Corp. 
Bus 001 Device 005: ID 413c:8161 Dell Computer Corp. 
Bus 001 Device 004: ID 0c45:6417 Microdia 
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 0000:0000  

naushad@nash:~$ sudo lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Unknown device [8086:0044] (rev 12)
00:01.0 PCI bridge [0604]: Intel Corporation Unknown device [8086:0045] (rev 12)
00:16.0 Communication controller [0780]: Intel Corporation Unknown device [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation Unknown device [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation Unknown device [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation Unknown device [8086:3b42] (rev 06)
00:1c.1 PCI bridge [0604]: Intel Corporation Unknown device [8086:3b44] (rev 06)
00:1c.3 PCI bridge [0604]: Intel Corporation Unknown device [8086:3b48] (rev 06)
00:1c.4 PCI bridge [0604]: Intel Corporation Unknown device [8086:3b4a] (rev 06)
00:1c.5 PCI bridge [0604]: Intel Corporation Unknown device [8086:3b4c] (rev 06)
00:1d.0 USB Controller [0c03]: Intel Corporation Unknown device [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation Unknown device [8086:3b09] (rev 06)
00:1f.2 SATA controller [0106]: Intel Corporation Unknown device [8086:3b29] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation Unknown device [8086:3b30] (rev 06)
02:00.0 VGA compatible controller [0300]: ATI Technologies Inc Unknown device [1002:68e0]
02:00.1 Audio device [0403]: ATI Technologies Inc Unknown device [1002:aa68]
04:00.0 Network controller [0280]: Broadcom Corporation Unknown device [14e4:4353] (rev 01)
07:00.0 SD Host controller [0805]: Ricoh Co Ltd Unknown device [1180:e822] (rev 01)
07:00.1 System peripheral [0880]: Ricoh Co Ltd Unknown device [1180:e230] (rev 01)
07:00.2 System peripheral [0880]: Ricoh Co Ltd Unknown device [1180:e852] (rev 01)
07:00.3 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd Unknown device [1180:e832] (rev 01)
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
ff:00.0 Host bridge [0600]: Intel Corporation Unknown device [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation Unknown device [8086:2d01] (rev 02)
ff:02.0 Host bridge [0600]: Intel Corporation Unknown device [8086:2d10] (rev 02)
ff:02.1 Host bridge [0600]: Intel Corporation Unknown device [8086:2d11] (rev 02)
ff:02.2 Host bridge [0600]: Intel Corporation Unknown device [8086:2d12] (rev 02)
ff:02.3 Host bridge [0600]: Intel Corporation Unknown device [8086:2d13] (rev 02)

```

---

