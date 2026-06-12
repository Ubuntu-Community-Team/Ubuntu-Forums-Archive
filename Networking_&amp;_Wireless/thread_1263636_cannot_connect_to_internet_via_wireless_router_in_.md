---
title: "cannot connect to internet via wireless router in ubuntu 9.0.4"
date: 2009-09-11
forum: Networking &amp; Wireless
---

### Post by friday.joseph20 on 2009-09-11
Hi,

I have recently set up a wireless router with my broadband and it works file with Windows vista. But I never succeeded in getting to Internet via  this wireless router in ubuntu 9.0.4 in the same computer. The problem seemed to be initially ESSID and AP are not getting set in wireless interface eth1. I tried to set it up from command line but failed to do so. Further now the wireless interface eth1 is not visible at all. Following are some env details
---------------------------------------------------------------------------------------------------------------------------
1) uname -a
Linux ubuntu 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux

2) cat /etc/udev/rules.d/70-persistent-net.rules
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:21:cc:38:72:64", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x432b (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:24:2c:32:4a:60", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

3) iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

4) lspci | grep -i network
02:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

5) sudo ifconfig eth1 up
eth1: ERROR while getting interface flags: No such device
--------------------------------------------------------------------------------------------------------------------------
Can someone please help me? 

Regards,
Joseph

---

### Post by friday.joseph20 on 2009-09-12
Can anyone please help me resolving this issue?

-joseph

---

### Post by friday.joseph20 on 2009-09-12
Further this is the output of the following command:
sudo lshw -C network
--------------------------------------------------------
  *-network UNCLAIMED              
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:21:cc:38:72:64
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.100 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 1a:f2:80:e5:31:ff
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
-------------------------------------------------------
why does the wlan controller is showing unclaimed? Any one knows the answer?

Thanks
joseph

---

### Post by friday.joseph20 on 2009-09-22
Don't bother folks, I have solved my problem. The solutions I found are:

1) The driver for my Broadcom 43322 wireless card got deactivated for some reason. So I re-activated it from sys administration and rebooted my laptop.

2) I discovered ubuntu does not work well with WEP keys with key index != 1 even though it allows you to set key index while setting up a wireless connection which is hugely misleading.

After this my wireless connection is up & running and I can use internet without any trouble whatsoever.

Thanks to those who read my earlier posts and spend time thinking on the problem.

cheers
-Joseph

---

### Post by Bucky Ball on 2009-09-22
Good work! To help others could you please mark as solved  from 'thread tools'.

---

