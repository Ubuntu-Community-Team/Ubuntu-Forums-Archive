---
title: "No access to the internet - Intel PRO/Wireless 5100 AGN"
date: 2012-07-21
forum: Networking &amp; Wireless
---

### Post by ml0dy on 2012-07-21
Hi!

I've just installed xubuntu 12.04 and after updating the system I don't have a connection to the internet. I've tried this soultion [http://ubuntuforums.org/showthread.php?t=1980142]("http://ubuntuforums.org/showthread.php?t=1980142") but it does not work... Any advices?

lspci
```

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 VGA compatible controller: NVIDIA Corporation G96 [GeForce GT 130M] (rev a1)
04:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)

```

sudo lshw -class network
```
  *-network               
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 00
       serial: 00:22:fa:b2:6d:1e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-26-generic firmware=8.83.5.1 build 33692 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:48 memory:f7100000-f7101fff

```

rfkill list all
```

0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

dmesg | grep iwl
```

[   17.123943] iwlwifi 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   17.123953] iwlwifi 0000:04:00.0: setting latency timer to 64
[   17.123983] iwlwifi 0000:04:00.0: pci_resource_len = 0x00002000
[   17.123985] iwlwifi 0000:04:00.0: pci_resource_base = ffffc90000650000
[   17.123988] iwlwifi 0000:04:00.0: HW Revision ID = 0x0
[   17.124097] iwlwifi 0000:04:00.0: irq 48 for MSI/MSI-X
[   17.124149] iwlwifi 0000:04:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   17.124212] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   17.147255] iwlwifi 0000:04:00.0: device EEPROM VER=0x11f, CALIB=0x4
[   17.147259] iwlwifi 0000:04:00.0: Device SKU: 0Xf0
[   17.153075] iwlwifi 0000:04:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   17.442401] iwlwifi 0000:04:00.0: loaded firmware version 8.83.5.1 build 33692
[   17.465823] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   18.869089] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   18.871997] iwlwifi 0000:04:00.0: Radio type=0x1-0x2-0x0
[   18.989072] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   18.991978] iwlwifi 0000:04:00.0: Radio type=0x1-0x2-0x0

```

---

### Post by chili555 on 2012-07-23
May I please see:```
cat /etc/modprobe.d/iwlwifi.conf
dmesg | grep wlan
```Thanks.

---

