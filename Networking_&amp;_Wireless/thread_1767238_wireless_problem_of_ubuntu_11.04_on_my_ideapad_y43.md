---
title: "wireless problem of ubuntu 11.04 on my ideapad y430a"
date: 2011-05-25
forum: Networking &amp; Wireless
---

### Post by tony04592 on 2011-05-25
I had already enabled the wireless but no wireless network is detected.

--------------------------
sudo lspci -k 

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Lenovo Device 3a00
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Lenovo Device 3a09
	Kernel driver in use: uhci_hcd
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Lenovo Device 3a0a
	Kernel driver in use: uhci_hcd
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Subsystem: Lenovo Device 3a0b
	Kernel driver in use: uhci_hcd
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
	Subsystem: Lenovo Device 3a0c
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Lenovo Device 3a0d
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Lenovo Device 3a14
	Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Lenovo Device 3a15
	Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Lenovo Device 3a16
	Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
	Subsystem: Lenovo Device 3a17
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: Lenovo Device 3a19
	Kernel modules: iTCO_wdt
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
	Subsystem: Lenovo Device 3a1a
	Kernel driver in use: ahci
	Kernel modules: ahci
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: Lenovo Device 3a1d
	Kernel modules: i2c-i801
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
	Subsystem: Lenovo Device 3a1f
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9300M GS] (rev a1)
	Subsystem: Lenovo Device 3a24
	Kernel driver in use: nvidia
	Kernel modules: nvidia-173, nouveau, nvidiafb
04:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
	Subsystem: Intel Corporation WiFi Link 5100 AGN
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn
07:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
	Subsystem: Lenovo IdeaPad S10e
	Kernel driver in use: tg3
	Kernel modules: tg3
08:06.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
	Subsystem: Lenovo Device 3a20
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci
08:06.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
	Subsystem: Lenovo Device 3a21
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci
08:06.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
	Subsystem: Lenovo Device 3a21

---------------------
lsusb

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 007: ID 0c45:7066 Microdia 
Bus 002 Device 006: ID 1631:5002 Good Way Technology 
Bus 002 Device 005: ID 0951:1613 Kingston Technology DataTraveler DT101C Flash Drive
Bus 002 Device 004: ID 1631:5400 Good Way Technology 
Bus 002 Device 003: ID 0411:0165 MelCo., Inc. 
Bus 002 Device 002: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by chili555 on 2011-05-25
How about posting:```
rfkill list all
lsmod
```Thanks.

---

