---
title: "update manager has screwed up my wireless. No card detected !"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by DeusExM1 on 2009-07-29
Hey everyone !

I have recently run an update as requested by the update manager. Upon reboot my wireless card seems to be gone. If i click on the top right wireless network manager, i see the message " no network devices available". Well it was available yesterday before the updates...

So what should i do ? I will post the outputs of :

lspci -nn
lshw -C Network
dmesg | grep -e ath -e wlan
uname -rm







00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8600M GT [10de:0407] (rev a1)
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)



  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: da:bb:bf:83:ec:03
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes






[    3.428322] device-mapper: multipath: version 1.0.5 loaded
[    3.428325] device-mapper: multipath round-robin: version 1.0.0 loaded
[   60.925588] wlan0: register 'rndis_wlan' at usb-0000:00:1d.7-1, Wireless RNDIS device, BCM4320b based, 00:1a:70:3a:ca:27
[   60.925615] usbcore: registered new interface driver rndis_wlan
[   60.928526] udev: renamed network interface wlan0 to wlan1
[   61.816735] rndis_wlan 2-1:1.0: rndis media disconnect
[   65.043304] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   81.348621] rndis_wlan 2-1:1.0: rndis media connect
[   81.374595] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   83.988572] rndis_wlan 2-1:1.0: rndis media connect
[   88.373328] rndis_wlan 2-1:1.0: rndis media connect
[   91.760170] wlan1: no IPv6 routers present
[   92.755602] rndis_wlan 2-1:1.0: rndis media connect
[   97.135861] rndis_wlan 2-1:1.0: rndis media connect
[  101.516578] rndis_wlan 2-1:1.0: rndis media connect
[  111.558117] rndis_wlan 2-1:1.0: rndis media disconnect
[  112.267435] rndis_wlan 2-1:1.0: rndis media connect
[  114.853213] rndis_wlan 2-1:1.0: rndis media connect
[  119.236680] rndis_wlan 2-1:1.0: rndis media connect
[  123.624551] rndis_wlan 2-1:1.0: rndis media connect
[  127.139221] rndis_wlan 2-1:1.0: rndis media disconnect
[  127.889506] rndis_wlan 2-1:1.0: rndis media connect
[  133.418043] wlan1: unregister 'rndis_wlan' usb-0000:00:1d.7-1, Wireless RNDIS device, BCM4320b based
[  162.655428] wlan0: register 'rndis_wlan' at usb-0000:00:1d.7-2, Wireless RNDIS device, BCM4320b based, 00:1a:70:3a:ca:27
[  162.656884] udev: renamed network interface wlan0 to wlan1
[  163.805117] rndis_wlan 2-2:1.0: rndis media disconnect
[  167.040096] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  182.865930] rndis_wlan 2-2:1.0: rndis media connect
[  182.893309] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  193.508060] wlan1: no IPv6 routers present
[  622.946996] wlan1: unregister 'rndis_wlan' usb-0000:00:1d.7-2, Wireless RNDIS device, BCM4320b based


2.6.28-14-generic x86_64

---

### Post by DeusExM1 on 2009-07-31
due to lack of replies i have reinstalled ubuntu 9.04 64 bit. seems like it was indeed the update since everything works now. I hope this does not happen again though.

---

