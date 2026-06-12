---
title: "Upgrade to 8.10 from 8.04, DLink PCI wireless card does not connect."
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by masonj7 on 2008-12-27
DLink DWL 520+ worked by manual configuration in 8.04.  After upgrade, the system sees the card but does not offer any way to show the available networks.

Any ideas?

---

### Post by masonj7 on 2008-12-30
The following is the results from following the ndiswrapper steps:

jeremiah@christians-desktop:~$ ndiswrapper -l
airplus : driver installed
	device (104C:8400) present (alternate driver: acx)
jeremiah@christians-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: a
       bus info: pci@0000:02:0a.0
       logical name: eth0
       version: 74
       serial: 00:04:76:21:76:cf
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x ip=192.168.1.103 latency=32 maxlatency=10 mingnt=10 module=3c59x multicast=yes
  *-network:1 UNCLAIMED
       description: Network controller
       product: ACX 100 22Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: b
       bus info: pci@0000:02:0b.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=32
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 1e:89:0a:82:01:d8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
jeremiah@christians-desktop:~$ lsmod | grep ndis
ndiswrapper           196380  0 
usbcore               148848  4 ndiswrapper,usbhid,uhci_hcd
jeremiah@christians-desktop:~$ sudo -s
[sudo] password for jeremiah: 
root@christians-desktop:~# echo 'ndiswrapper' | sudo tee -a /etc/modules
ndiswrapper
root@christians-desktop:~# dmesg | grep -e ndis -e wlan
[   18.118001] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   18.432454] usbcore: registered new interface driver ndiswrapper
[  195.156503] usbcore: deregistering interface driver ndiswrapper
[  195.205026] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  195.249341] ndiswrapper: driver airplus (D-Link,03/05/2003,3.0.5.0) loaded
[  195.252463] ndiswrapper 0000:02:0b.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[  195.253152] ndiswrapper: using IRQ 23
[  195.300711] ndiswrapper (NdisWriteErrorLogEntry:190): log: C000138A, count: 1, return_address: dd0867d1
[  195.300733] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x4
[  195.304834] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[  195.304872] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[  195.304904] ndiswrapper (mp_halt:262): device d9757480 is not initialized - not halting
[  195.304912] ndiswrapper: device eth%d removed
[  195.313109] ndiswrapper 0000:02:0b.0: PCI INT A disabled
[  195.314709] ndiswrapper: probe of 0000:02:0b.0 failed with error -22
[  195.319633] usbcore: registered new interface driver ndiswrapper
[  225.547041] usbcore: deregistering interface driver ndiswrapper
[  225.550747] ndiswrapper (ntoskernel_exit:2671): object db512320(2) was not freed, freeing it now
[  225.594999] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  225.638771] ndiswrapper: driver airplus (D-Link,03/05/2003,3.0.5.0) loaded
[  225.640060] ndiswrapper 0000:02:0b.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[  225.640741] ndiswrapper: using IRQ 23
[  225.687971] ndiswrapper (NdisWriteErrorLogEntry:190): log: C000138A, count: 1, return_address: dd0863f1
[  225.687992] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x4
[  225.689051] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[  225.689084] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[  225.689114] ndiswrapper (mp_halt:262): device d9755480 is not initialized - not halting
[  225.689121] ndiswrapper: device eth%d removed
[  225.697282] ndiswrapper 0000:02:0b.0: PCI INT A disabled
[  225.698855] ndiswrapper: probe of 0000:02:0b.0 failed with error -22
[  225.703778] usbcore: registered new interface driver ndiswrapper
[  255.902879] usbcore: deregistering interface driver ndiswrapper
[  255.906653] ndiswrapper (ntoskernel_exit:2671): object db537f20(2) was not freed, freeing it now
[  255.945965] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  255.989019] ndiswrapper: driver airplus (D-Link,03/05/2003,3.0.5.0) loaded
[  255.990270] ndiswrapper 0000:02:0b.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[  255.990950] ndiswrapper: using IRQ 23
[  256.038287] ndiswrapper (NdisWriteErrorLogEntry:190): log: C000138A, count: 1, return_address: dce392af
[  256.038307] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x4
[  256.039335] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[  256.039366] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[  256.039397] ndiswrapper (mp_halt:262): device d9757480 is not initialized - not halting
[  256.039406] ndiswrapper: device eth%d removed
[  256.047345] ndiswrapper 0000:02:0b.0: PCI INT A disabled
[  256.048975] ndiswrapper: probe of 0000:02:0b.0 failed with error -22
[  256.053835] usbcore: registered new interface driver ndiswrapper
root@christians-desktop:~# 

ideas?

---

### Post by wieman01 on 2008-12-30
Also please provide:
> sudo lshw -C network
> sudo iwlist scan

---

### Post by masonj7 on 2008-12-30
jeremiah@christians-desktop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
pan0      Interface doesn't support scanning.

jeremiah@christians-desktop:~$ sudo lshw -C network
[sudo] password for jeremiah: 
  *-network:0             
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: a
       bus info: pci@0000:02:0a.0
       logical name: eth0
       version: 74
       serial: 00:04:76:21:76:cf
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=32 link=no maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=10MB/s
  *-network:1 UNCLAIMED
       description: Network controller
       product: ACX 100 22Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: b
       bus info: pci@0000:02:0b.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=32
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 1e:89:0a:82:01:d8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
jeremiah@christians-desktop:~$

---

### Post by wieman01 on 2008-12-31
You have performed an upgrade, right? What were the manual steps you described while you were on 8.04? You might have to go through the same procedure again, as upgrades tend to temper with these things.

---

