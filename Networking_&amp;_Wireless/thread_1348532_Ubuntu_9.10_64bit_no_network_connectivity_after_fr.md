---
title: "Ubuntu 9.10 64bit no network connectivity after fresh install"
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by dneusitz on 2009-12-07
Hi folks. This one has me stumped. I've played around with various Ubuntu releases in the past usually overcoming any problems that I encountered. Even so I still consider my self a newbie. Here is my latest issue.

A fresh install of 9.10 64bit on my laptop results in no network connectivity after the install. I have no network connectivity with either a wired or a wireless connection to my router. I have verified the router is working and does connect wired and wirelessly.

Linux kernel I'm booting with is 2.6.31-14-generic
Here is the output from a lspci -k command on my notebook

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Kernel driver in use: i915
	Kernel modules: i915
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Kernel driver in use: uhci_hcd
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Kernel driver in use: uhci_hcd
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Kernel driver in use: uhci_hcd
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Kernel modules: iTCO_wdt
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
	Kernel driver in use: ahci
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Kernel modules: i2c-i801
01:00.0 VGA compatible controller: ATI Technologies Inc Device 9488
	Kernel modules: radeon
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
02:00.0 FireWire (IEEE 1394): O2 Micro, Inc. Device 10f7 (rev 01)
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394
02:00.1 SD Host controller: O2 Micro, Inc. Device 8120 (rev 01)
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci
02:00.2 Mass storage controller: O2 Micro, Inc. Device 8130 (rev 01)
06:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
	Kernel modules: tg3
09:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

---

### Post by dneusitz on 2009-12-07
Solved. Here's what I had to do to get my network connections functioning.
from a terminal window enter this command

cd /boot/grub

next enter the command

sudo chmod +w grub.cfg

You will be asked for your password after you hit Enter
This will change the permissions on the file grub.cfg so that you can edit it. Otherwise it is a read only file.

now enter the command

sudo gedit grub.cfg

and look for a line similar to this 
linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro quiet splash

on the same line after quiet splash you want to enter
pci=use_crs

Save the file, shutdown and reboot.
Once you login again, you should be able to connect to the network. 

Keep in mind that the file grub.cfg is a generated file. So that if you ever update grub on your systsem any changes you made to this file will be lost. You will need to re-edit the file.

Hope this helps you.

---

### Post by monkeymind90 on 2009-12-08
This made my computer unable to boot up. I was able to restore by reloading grub from the menu during bootup where it asks if you want to start in recovery mode. I cannot post the output from lspci -k because my computer has zero internet access, but I have a Broadcom Wireless card (bcm4328) and an nVidia Corporation MCP65 ethernet controller. The nVidia is using forcedeth and the Broadcom is using b43-pci-bridge with ssb as a module. If this doesn't make sense please tell me what would help. 
Thanks,
Ethan

---

