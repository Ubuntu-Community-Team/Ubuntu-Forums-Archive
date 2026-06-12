---
title: "Atheros 802.11 Wireless LAN/Ubuntu 8.10/Acer Aspire 5720"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by graa on 2009-01-20
I'm trying to connect to the wireless. Can somebody tell me where I can download the driver for my wireless card? 
Thanks.

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:5c:22:96
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5787m-v3.22 ip=192.168.1.4 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 96:c9:e6:76:3a:c4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by Bright_View on 2009-01-20
My brother had an Acer Aspire laptop (can't remember the model) and I got his wireless up and running using a MadWifi driver.  Their homepage:

[http://madwifi-project.org/](http://madwifi-project.org/)

Can't remember the exact commands, but if you do some digging in that site you'll come across the instructions for installing the driver that you need, and that is how I ended up getting it to work.  Are you comfortable with that?  If not, then can you get the exact model number of your wireless card so that I can find the instructions again?

A word of warning: don't punch this in to Google to get instructions.  I started out that way, but ended up following instructions for getting MadWifi drivers that were out of date a few times.  Only use the instructions from the MadWifi homepage.

---

### Post by graa on 2009-01-20
Thanks.
i'm really new to this so am quite slow. I can't really understand what to do once i get to the site you suggested.
I did a few more commands, which may or may not have given useful info:

:~$ lspci -vn
00:00.0 0600: 8086:2a00 (rev 03)
	Subsystem: 1025:011e
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 0300: 8086:2a02 (rev 03)
	Subsystem: 1025:011e
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 94000000 (64-bit, non-prefetchable) [size=1M]
	Memory at 80000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 5110 [size=8]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:02.1 0380: 8086:2a03 (rev 03)
	Subsystem: 1025:011e
	Flags: bus master, fast devsel, latency 0
	Memory at 98500000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1a.0 0c03: 8086:2834 (rev 04)
	Subsystem: 1025:011e
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 50c0 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.1 0c03: 8086:2835 (rev 04)
	Subsystem: 1025:011e
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 50a0 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.7 0c03: 8086:283a (rev 04) (prog-if 20)
	Subsystem: 1025:011e
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at 98404c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1b.0 0403: 8086:284b (rev 04)
	Subsystem: 1025:011e
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at 98400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 0604: 8086:283f (rev 04)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: 97400000-983fffff
	Prefetchable memory behind bridge: 0000000090000000-0000000090ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 0604: 8086:2841 (rev 04)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: 96400000-973fffff
	Prefetchable memory behind bridge: 0000000091000000-0000000091ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 0604: 8086:2843 (rev 04)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 95300000-963fffff
	Prefetchable memory behind bridge: 0000000092000000-0000000092ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 0604: 8086:2845 (rev 04)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 94200000-952fffff
	Prefetchable memory behind bridge: 0000000093000000-0000000093ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 0c03: 8086:2830 (rev 04)
	Subsystem: 1025:011e
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 5080 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 0c03: 8086:2831 (rev 04)
	Subsystem: 1025:011e
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 5060 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 0c03: 8086:2832 (rev 04)
	Subsystem: 1025:011e
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 5040 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 0c03: 8086:2836 (rev 04) (prog-if 20)
	Subsystem: 1025:011e
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at 98404800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 0604: 8086:2448 (rev f4) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=32
	Memory behind bridge: 94100000-941fffff
	Capabilities: <access denied>

00:1f.0 0601: 8086:2815 (rev 04)
	Subsystem: 1025:011e
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.1 0101: 8086:2850 (rev 04) (prog-if 8a [Master SecP PriP])
	Subsystem: 1025:011e
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 50e0 [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.2 0106: 8086:2829 (rev 04) (prog-if 01)
	Subsystem: 1025:011e
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 219
	I/O ports at 50f8 [size=8]
	I/O ports at 511c [size=4]
	I/O ports at 50f0 [size=8]
	I/O ports at 5118 [size=4]
	I/O ports at 5020 [size=32]
	Memory at 98404000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 0c05: 8086:283e (rev 04)
	Subsystem: 1025:011e
	Flags: medium devsel, IRQ 11
	Memory at 98405000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 5000 [size=32]
	Kernel modules: i2c-i801

05:00.0 0200: 14e4:1693 (rev 02)
	Subsystem: 1025:011e
	Flags: bus master, fast devsel, latency 0, IRQ 218
	Memory at 95300000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at <ignored> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: tg3
	Kernel modules: tg3

06:00.0 0200: 168c:001c (rev 01)
	Subsystem: 1468:0428
	Flags: fast devsel, IRQ 19
	Memory at 94200000 (64-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel modules: ath_pci

07:00.0 0c00: 1180:0832 (rev 05) (prog-if 10)
	Subsystem: 1025:011e
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at 94100000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

07:00.1 0805: 1180:0822 (rev 22)
	Subsystem: 1025:011e
	Flags: bus master, medium devsel, latency 0, IRQ 22
	Memory at 94100b00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

07:00.2 0880: 1180:0843 (rev 12)
	Subsystem: 1025:011e
	Flags: bus master, medium devsel, latency 0, IRQ 11
	Memory at 94100a00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ricoh-mmc
	Kernel modules: ricoh_mmc

07:00.3 0880: 1180:0592 (rev 12)
	Subsystem: 1025:011e
	Flags: bus master, medium devsel, latency 0, IRQ 11
	Memory at 94100900 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

07:00.4 0880: 1180:0852 (rev ff) (prog-if ff)
	!!! Unknown header type 7f




$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 04)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
07:00.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:00.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:00.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:00.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:00.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by J A Smith on 2009-01-20
Running the same laptop (almost), I found this helped:

[https://help.ubuntu.com/community/AspireOne110L#WLan](https://help.ubuntu.com/community/AspireOne110L#WLan)

---

### Post by graa on 2009-01-20
I'm just posting the output from trying the link you posted:

hamlet@ubuntu:~$ wget [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz)
--2009-01-20 20:22:30--  [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz)
Resolving snapshots.madwifi-project.org... 217.24.1.134
Connecting to snapshots.madwifi-project.org|217.24.1.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4421921 (4.2M) [application/x-gzip]
Saving to: `madwifi-hal-0.10.5.6-current.tar.gz'

100%[======================================>] 4,421,921   90.3K/s   in 48s     

2009-01-20 20:23:18 (90.2 KB/s) - `madwifi-hal-0.10.5.6-current.tar.gz' saved [4421921/4421921]

hamlet@ubuntu:~$ sudo apt-get install build-essential linux-headers-$(uname -r)
[sudo] password for hamlet: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.3 libstdc++6-4.3-dev linux-headers-2.6.27-9 patch
Suggested packages:
  debian-keyring g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg
  libstdc++6-4.3-doc diff-doc
The following NEW packages will be installed
  build-essential dpkg-dev g++ g++-4.3 libstdc++6-4.3-dev
  linux-headers-2.6.27-9 linux-headers-2.6.27-9-generic patch
0 upgraded, 8 newly installed, 0 to remove and 214 not upgraded.
Need to get 12.6MB of archives.
After this operation, 73.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main libstdc++6-4.3-dev 4.3.2-1ubuntu11 [1354kB]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main g++-4.3 4.3.2-1ubuntu11 [4128kB]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main g++ 4:4.3.1-1ubuntu2 [1444B] 
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main patch 2.5.9-5 [100kB]        
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main dpkg-dev 1.14.20ubuntu6 [612kB]
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main build-essential 11.4 [7172B] 
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main linux-headers-2.6.27-9 2.6.27-9.19 [5771kB]
Get: 8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main linux-headers-2.6.27-9-generic 2.6.27-9.19 [621kB]
Fetched 12.6MB in 1min6s (188kB/s)                                             
Selecting previously deselected package libstdc++6-4.3-dev.
(Reading database ... 103410 files and directories currently installed.)
Unpacking libstdc++6-4.3-dev (from .../libstdc++6-4.3-dev_4.3.2-1ubuntu11_i386.deb) ...
Selecting previously deselected package g++-4.3.
Unpacking g++-4.3 (from .../g++-4.3_4.3.2-1ubuntu11_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.3.1-1ubuntu2_i386.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.5.9-5_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.20ubuntu6_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.4_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.27-9.
Unpacking linux-headers-2.6.27-9 (from .../linux-headers-2.6.27-9_2.6.27-9.19_all.deb) ...
Selecting previously deselected package linux-headers-2.6.27-9-generic.
Unpacking linux-headers-2.6.27-9-generic (from .../linux-headers-2.6.27-9-generic_2.6.27-9.19_i386.deb) ...
Processing triggers for man-db ...
Setting up patch (2.5.9-5) ...
Setting up dpkg-dev (1.14.20ubuntu6) ...
Setting up linux-headers-2.6.27-9 (2.6.27-9.19) ...
Setting up linux-headers-2.6.27-9-generic (2.6.27-9.19) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common

Setting up g++-4.3 (4.3.2-1ubuntu11) ...
Setting up libstdc++6-4.3-dev (4.3.2-1ubuntu11) ...
Setting up g++ (4:4.3.1-1ubuntu2) ...

Setting up build-essential (11.4) ...
hamlet@ubuntu:~$ make
make: *** No targets specified and no makefile found. Stop.
hamlet@ubuntu:~$ sudo make install
make: *** No rule to make target `install'. Stop.
hamlet@ubuntu:~$ sudo modprobe ath_pci
FATAL: Module ath_pci not found.
hamlet@ubuntu:~$ sudo gedit /etc/modules ath_pci
hamlet@ubuntu:~$ /etc/default/linux-restricted-modules-common
bash: /etc/default/linux-restricted-modules-common: Permission denied
hamlet@ubuntu:~$ make
make: *** No targets specified and no makefile found. Stop.
hamlet@ubuntu:~$ sudo make install
make: *** No rule to make target `install'. Stop.
hamlet@ubuntu:~$ sudo modprobe ath_pci



Any ideas of what i'm doing wrong?

---

### Post by graa on 2009-01-21
In fact when i turned it on and went into ubuntu this morning it found my wireless network, so it did work. Thanks!:D

---

### Post by Bright_View on 2009-01-21
Right on!  MadWifi is pretty wicked for coming up with all those drivers.  I'll have to remember that link for next time this problem pops up.  Nice find J A Smith.

Enjoy your new wireless capable system graa!

---

