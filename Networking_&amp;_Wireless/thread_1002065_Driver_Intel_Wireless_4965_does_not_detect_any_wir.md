---
title: "Driver Intel Wireless 4965 does not detect any wireless network"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by okelet on 2008-12-04
Hi

I have installed Ubuntu 8.10. My laptop (JFT00) has a wireless and a wired netword card:

```

usuario@nb-usuario:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 12
       serial: 00:21:70:c1:6f:a6
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.2.152 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 16:14:f4:64:28:90
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
usuario@nb-usuario:~$ 

```

so the two interfaces are detected by Ubuntu, but no wireless network is detected (I am sure there are many wireless network, using Windows and Ubuntu 8.10 in other Laptop the wireless networks are detected).

I have installed ndiswrapper, the driver is installed ok, but not loaded, so now there is no wireless interface in Networkmanager:

```

Dec  4 15:53:10 nb-usuario kernel: [ 1371.542386] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
Dec  4 15:53:10 nb-usuario kernel: [ 1371.576165] usbcore: registered new interface driver ndiswrapper
Dec  4 15:54:19 nb-usuario kernel: [   11.936813] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
Dec  4 15:54:19 nb-usuario kernel: [   12.377413] ndiswrapper: driver netw4x32 (Intel,08/01/2007,11.1.1.21) loaded
Dec  4 15:54:19 nb-usuario kernel: [   12.377915] ndiswrapper 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec  4 15:54:19 nb-usuario kernel: [   12.377929] ndiswrapper (NdisWriteErrorLogEntry:190): log: 40001B7C, count: 2, return_address: f8c015e2
Dec  4 15:54:19 nb-usuario kernel: [   12.377933] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x56524457
Dec  4 15:54:19 nb-usuario kernel: [   12.377936] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0xe2
Dec  4 15:54:19 nb-usuario kernel: [   12.378021] ndiswrapper 0000:01:00.0: setting latency timer to 64
Dec  4 15:54:19 nb-usuario kernel: [   12.413484] ndiswrapper: using IRQ 16
Dec  4 15:54:19 nb-usuario kernel: [   12.705529] wlan0: ethernet device 00:1d:e0:c5:f5:c1 using NDIS driver: netw4x32, version: 0x10015, NDIS version: 0x501, vendor: 'Intel(R) Wireless WiFi Link 4965AG Driver', 8086:4229.5.conf
Dec  4 15:54:19 nb-usuario kernel: [   12.806778] usbcore: registered new interface driver ndiswrapper
Dec  4 15:54:23 nb-usuario NetworkManager: <info>  wlan0: driver is 'ndiswrapper'. 
Dec  4 22:05:23 nb-usuario kernel: [   12.230319] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
Dec  4 22:05:23 nb-usuario kernel: [   12.732551] ndiswrapper: driver netw4x32 (Intel,08/01/2007,11.1.1.21) loaded
Dec  4 22:05:23 nb-usuario kernel: [   12.733219] ndiswrapper 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec  4 22:05:23 nb-usuario kernel: [   12.733236] ndiswrapper (NdisWriteErrorLogEntry:190): log: 40001B7C, count: 2, return_address: f8c015e2
Dec  4 22:05:23 nb-usuario kernel: [   12.733240] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x56524457
Dec  4 22:05:23 nb-usuario kernel: [   12.733244] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0xe2
Dec  4 22:05:23 nb-usuario kernel: [   12.733326] ndiswrapper 0000:01:00.0: setting latency timer to 64
Dec  4 22:05:23 nb-usuario kernel: [   12.771203] ndiswrapper: using IRQ 16
Dec  4 22:05:23 nb-usuario kernel: [   13.020520] wlan0: ethernet device 00:1d:e0:c5:f5:c1 using NDIS driver: netw4x32, version: 0x10015, NDIS version: 0x501, vendor: 'Intel(R) Wireless WiFi Link 4965AG Driver', 8086:4229.5.conf
Dec  4 22:05:23 nb-usuario kernel: [   13.201613] usbcore: registered new interface driver ndiswrapper
Dec  4 22:05:27 nb-usuario NetworkManager: <info>  wlan0: driver is 'ndiswrapper'. 
Dec  4 22:11:56 nb-usuario kernel: [  412.227397] ndiswrapper: device wlan0 removed
Dec  4 22:11:56 nb-usuario kernel: [  412.228868] ndiswrapper 0000:01:00.0: PCI INT A disabled
Dec  4 22:11:56 nb-usuario kernel: [  412.231435] usbcore: deregistering interface driver ndiswrapper
Dec  4 22:11:56 nb-usuario kernel: [  412.266870] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
Dec  4 22:11:56 nb-usuario kernel: [  412.315331] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeBugCheck'
Dec  4 22:11:56 nb-usuario kernel: [  412.315928] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netw5x32'
Dec  4 22:11:56 nb-usuario loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver netw5x32 
Dec  4 22:11:56 nb-usuario kernel: [  412.318704] ndiswrapper (load_wrap_driver:108): couldn't load driver netw5x32; check system log for messages from 'loadndisdriver'
Dec  4 22:11:56 nb-usuario kernel: [  412.334855] usbcore: registered new interface driver ndiswrapper

```

What next can I do?

---

### Post by Clancy_s on 2008-12-04
I have that trouble with 64 bit intrepid and an Intel 4695 card, I had it with gutsy too though hardy worked OK.  I fixed it by switching to wicd instead of network manager (I was too lazy to switch back to wicd with hardy since NM was doing OK but IMO wicd does have a much more appealing interface).

Since wicd worked straight away I didn't bother trying to fix network manager.

wicd is here:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

eta: with the latest upgrades wicd has stopped working too, I'm going to look into ndiswrapper

---

