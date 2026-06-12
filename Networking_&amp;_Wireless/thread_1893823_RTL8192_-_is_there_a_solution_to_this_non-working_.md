---
title: "RTL8192 - is there a solution to this non-working wifi?"
date: 2011-12-11
forum: Networking &amp; Wireless
---

### Post by rickbeton on 2011-12-11
Hi,
 I posted a year ago about my non-working wifi on my Samsung R620 ([http://ubuntuforums.org/showthread.php?t=1646978](http://ubuntuforums.org/showthread.php?t=1646978)).  There have been lots of similar questions since but I can't see a solution - unless I missed it.

Did I miss it?

For reference, here's some more info about my laptop:

```
sudo lshw |grep less
                description: Wireless interface
                product: RTL8192E/RTL8192SE Wireless LAN Controller
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl819xE ip=192.168.1.71 latency=0 multicast=yes wireless=802.11bgn

sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series]
01:00.1 Audio device: ATI Technologies Inc RV710/730
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192E/RTL8192SE Wireless LAN Controller (rev 01)
06:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8057 PCI-E Gigabit Ethernet Controller (rev 10)

```

Thanks,
Rick

---

### Post by praseodym on 2011-12-11
Hi,

try this PPA for Samsung note/netbooks. 

[https://launchpad.net/~voria/+archive/ppa](https://launchpad.net/~voria/+archive/ppa)

```
sudo add-apt-repository ppa:voria/ppa
sudo apt-get update
sudo apt-get install samsung-wireless samsung-tools
```
and reboot. The Realtek driver rtl8192e is not further developed. Alternatively try the windows driver with ndiswrapper

---

