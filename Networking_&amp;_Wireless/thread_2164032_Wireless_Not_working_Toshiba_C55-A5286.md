---
title: "Wireless Not working Toshiba C55-A5286"
date: 2013-07-20
forum: Networking &amp; Wireless
---

### Post by hjsteve on 2013-07-20
Hey fellow Ubuntu users!

I am not a novice but no where near an expert user.

I am setting up a Toshiba Laptop Dual boot, Ubuntu/Windows 8.  The dual boot is working and wireless works on Windows 8.

It was a clean install of Ubuntu 12.04 LTS on a 92GB Partition, 20GB Swap.

To get network connectivity, I installed compat-wireless-2012-02-28-p manually and to my surprise, this got the wired interface working.  

I performed an update with Update Manager and everything except the Wireless seems to work. 

I then used the install.sh from the RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105 package because the Realtek is the Wireless controller, maybe?

I am wondering if the first driver, compat-wireless-2012-02-28-p, that I installed wasn't correct and is now causing problems.

Any help is greatly appreciated!

lspci shows:
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 Ethernet controller: Atheros Communications Inc. AR8162 Fast Ethernet (rev 10)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8179 (rev 01)

lshw shows the following network info:

           *-network
                description: Ethernet interface
                product: AR8162 Fast Ethernet
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 10
                serial: 00:8c:fa:4e:7d:88
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=alx driverversion=1.2.3 duplex=full firmware=N/A ip=192.168.1.11 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:16 memory:c8500000-c853ffff ioport:3000(size=128)
        *-pci:1
             description: PCI bridge
             product: Panther Point PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:2000(size=4096) memory:c8400000-c84fffff
           *-network UNCLAIMED
                description: Network controller
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: ioport:2000(size=256) memory:c8400000-c8403fff

---

### Post by chili555 on 2013-07-30
> I am wondering if the first driver, compat-wireless-2012-02-28-p, that I installed wasn't correct and is now causing problems.I doubt it.

Let's further identify your wireless device before we proceed:```
lspci -nn | grep 0280
```Thanks.

---

### Post by gordintoronto on 2013-07-30
This is the wireless adapter:
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8179 (rev 01)

The instructions here might be useful:
[http://peppermintos.net/viewtopic.php?f=8&t=5619](http://peppermintos.net/viewtopic.php?f=8&t=5619)

And this bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1096989](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1096989)
(which says the device is supported in the Linux 3.10 kernel.)

---

### Post by praseodym on 2013-07-31
[http://forum.ubuntuusers.de/topic/realtek-rtl8188ce-treiber-installieren/2/?highlight=8179+realtek#post-5443987](http://forum.ubuntuusers.de/topic/realtek-rtl8188ce-treiber-installieren/2/?highlight=8179+realtek#post-5443987)

Try these instructions (black boxes), 8179 is supported.

---

