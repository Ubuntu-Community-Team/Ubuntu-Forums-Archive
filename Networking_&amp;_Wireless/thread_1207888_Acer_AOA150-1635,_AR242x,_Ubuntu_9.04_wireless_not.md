---
title: "Acer AOA150-1635, AR242x, Ubuntu 9.04: wireless not working"
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by deh on 2009-07-08
I've set up the Acer Netbook to dual boot XP and Ubuntu 9.04.  The wireless works fine with XP, but isn't recognized with Linux.  I've tried some of the suggestions in the posts on the AR242x with no success.  I'm not sure what to do next.

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
        Subsystem: Foxconn International, Inc. Device e008
        Flags: fast devsel, IRQ 18
        Memory at 55200000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel modules: ath5k, ath_pci

deh@Acer150:/$ lsb_release -d
Description:	Ubuntu 9.04

deh@Acer150:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

If I go into System/Administration/Hardware Drivers I get the following, and it is shown as active and in use--

Alternate "madwifi" driver for Atheros wireless LAN cards.

Only activate this driver if you have problems with your wireless LAN connection.

The free "ath5k" driver should work with most Atheros cards nowadays, but on some computers this alternate (but proprietary) driver still works better, or at all.

deh@Acer150:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:5a:0d:b3
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.1.1.32 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 0a:9b:0a:57:3d:f0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
deh@Acer150:~$ 

The "DISABLED" suggests something needs to be enabled, but I don't what that might be.

---

### Post by deh on 2009-07-14
I got it working by following the procedure in the following thread--

[http://ubuntuforums.org/showthread.php?t=1213119](http://ubuntuforums.org/showthread.php?t=1213119)

I found that the worked fine with Suse 11.1 with the ath5k driver, so it should work with Ubuntu and the ath5k driver.

---

