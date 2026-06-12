---
title: "Wireless disappears"
date: 2012-12-17
forum: Networking &amp; Wireless
---

### Post by dranorter on 2012-12-17
Hullo,

I have just gotten rid of Windows after having a dual-boot setup for a year or two. But I'd forgotten, I occasionally rebooted in Windows just to fix a problem with the wireless disappearing. So now I don't know the proper fix.

What happens is, sometimes the wireless switch turns orange and toggling it doesn't get it back blue again (though the event does show up in the rfkill events). During this problem, wlan0 does not exist. I used to simply reboot in Windows (Vista), whereupon the uh light would turn blue again for whatever reason and then I could go back into Ubuntu. (Just rebooting Ubuntu didn't/doesn't help.)

I am using Ubuntu 12.10 on an hp TX2-1020US. (I love my tx2. But the stylus is dead :P)

Here is the output of rfkill.
0: hp-wifi: Wireless LAN
         Soft Blocked: no
         Hard Blocked: no

Of iwconfig:
eth0        no wireless extensions.

lo            no wireless extensions.

Of sudo lshw -C network

*-network UNCLAIMED
         description: Network controller
         product: BCM4322 802.11a/b/g/n Wireless LAN Controller
         vendor: Broadcom Corporation
         physical id: 0
         bus info: pci@0000:08:00.0
         version: 01
         width: 64 bits
         clock: 33MHz
         capabilities: pm msi pciexpress bus_master cap_list
         configuration: latency=0
         resources: memory:d1100000-d1103fff
*-network
         description: Ethernet interface
         product: RTL8111/8168B PCI Express Gigabit Ethernet controller
         vendor: Realtek Semiconductor Co., Ltd.
         physical id: 0
         bus info: pci@0000:09:00.0
         logical name: eth0
         version: 02
         serial: 00:23:8b:f5:c3:7d
         size: 10Mbit/s
         capacity: 1Gbit/s
         width: 64 bits
         clock: 33MHz
         capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
         configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
         resources: irq:43 ioport:2000(size=256) memory:d1010000-d1010fff memory:d1000000-d100ffff memory:d1020000-d102ffff

---

