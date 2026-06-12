---
title: "Broadcom BCM4312 stop working after update"
date: 2013-05-24
forum: Networking &amp; Wireless
---

### Post by upchucky on 2013-05-24
I am running Ubuntu 13.04

Please check my wireless info,
I did a update and the wireless stopped working, there is a section that says Unclaimed, I tried the suggestions as shown and no glory, at the bottom it says Fatal, Module wl not found



itsme@xpsm1730:~$ sudo lshw -C network
[sudo] password for itsme: 
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0efc000-f0efffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5754M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth1
       version: 02
       serial: 00:21:9b:f9:21:86
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=full firmware=5754m-v3.23 ip=192.168.0.180 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:47 memory:f0bf0000-f0bfffff
itsme@xpsm1730:~$ lspci -nnk | grep -iA2 net
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5754M Gigabit Ethernet PCI Express [14e4:1672] (rev 02)
	Subsystem: Dell Device [1028:01f7]
	Kernel driver in use: tg3
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Dell Wireless 1395 WLAN Mini-Card [1028:000b]
	Kernel modules: wl, ssb
itsme@xpsm1730:~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
itsme@xpsm1730:~$ echo "blacklist brcmwl" | sudo tee -a
blacklist brcmwl
itsme@xpsm1730:~$ sudo apt-get install --reinstall bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
Need to get 0 B/1,303 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 262075 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 6.20.155.1+bdcom-0ubuntu6 (using .../bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu6_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu6) ...
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
Building for 3.2.0-40-generic-pae and 3.8.0-19-generic
Building for architecture i686
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Building initial module for 3.8.0-19-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.8.0-19-generic/updates/dkms/

depmod....

DKMS: install completed.
FATAL: Module wl not found.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-19-generic
itsme@xpsm1730:~$

---

