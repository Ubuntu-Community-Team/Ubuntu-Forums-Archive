---
title: "wireless stopped working"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by xpix on 2009-05-15
MORE NEW INFO:
After vacuuming the laptop, and tring to get to the wireless module without success I restarted once more and the wireless is working now. Weird?
Thx anyway. Sorry for the spam :)

NEW INFO: I booted in Ubuntu 9.04 32 and I get the same behavior.  Is it possible that the wireless card broke.
If so can you recommend one I can buy and is compatible with ubuntu.

Thx


HI,

I installed Ubuntu 9.04 64 and everything was ok till today. After reset the wireless stopped working. 

The day before I installed B of wesnoth maybe did some upgrades used Computer Janitor, maybe installed some other packages.

Is there a way I can reload the initial wireless setup?

Here are some informations:

02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

--------------
iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

-----------------
sudo lshw -C network

  *-network DISABLED      
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:19:7d:ee:a9:dc
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:ca:ed:15
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.100.105 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

-------------

iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results


Thank you


PS: If I click on the network icon it says:
Wired Network: Auto eth0
Wireless Network: Device not ready
(enable Wireless checkbox is checked)

More:

sudo ifconfig wlan0 up
SIOCSIFFLAGS: Resource temporarily unavailable

This one is big
```
dmesg | tail -n 50
[   14.718833] type=1505 audit(1242431297.480:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2044
[   14.858224] type=1505 audit(1242431297.619:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2048
[   14.895213] type=1505 audit(1242431297.655:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2052
[   20.625694] pci 0000:01:05.0: power state changed by ACPI to D0
[   20.625712] pci 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.773149] [drm] Initialized drm 1.1.0 20060810
[   20.867892] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   20.885599] ppdev: user-space parallel port driver
[   21.352137] [drm] Setting GART location based on new memory map
[   21.352625] [drm] Loading R300 Microcode
[   21.352646] [drm] Num pipes: 4
[   21.352652] [drm] writeback test succeeded in 1 usecs
[   25.236747] eth0: link down
[   25.237434] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.541233] ath5k phy0: gain calibration timeout (2412MHz)
[   25.541239] ath5k phy0: can't reset hardware (-11)
[   25.894861] ath5k phy0: gain calibration timeout (2412MHz)
[   25.894866] ath5k phy0: can't reset hardware (-11)
[   58.038124] ath5k phy0: gain calibration timeout (2412MHz)
[   58.038129] ath5k phy0: can't reset hardware (-11)
[   83.720072] Clocksource tsc unstable (delta = -171748935 ns)
[  206.142668] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  206.453372] ath5k phy0: gain calibration timeout (2412MHz)
[  206.453384] ath5k phy0: can't reset hardware (-11)
[  214.847549] ath5k phy0: gain calibration timeout (2412MHz)
[  214.847561] ath5k phy0: can't reset hardware (-11)
[  217.024058] eth0: no IPv6 routers present
[  220.906990] eth0: link down
[  225.562948] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1521.599714] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[ 1521.599719] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[ 1521.599722] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.
[ 1575.842854] eth0: link down
[ 1587.893926] ath5k phy0: gain calibration timeout (2412MHz)
[ 1587.893938] ath5k phy0: can't reset hardware (-11)
[ 1600.054851] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1734.574209] eth0: link down
[ 1750.590808] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1750.844345] eth0: link down
[ 1752.404232] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1991.386639] eth0: link down
[ 1996.724839] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 2006.716841] ath5k phy0: gain calibration timeout (2412MHz)
[ 2006.716852] ath5k phy0: can't reset hardware (-11)
[ 2712.775172] ath5k phy0: gain calibration timeout (2412MHz)
[ 2712.775183] ath5k phy0: can't reset hardware (-11)
[ 2903.782506] ath5k phy0: gain calibration timeout (2412MHz)
[ 2903.782518] ath5k phy0: can't reset hardware (-11)
[ 2910.081971] ath5k phy0: gain calibration timeout (2412MHz)
[ 2910.081982] ath5k phy0: can't reset hardware (-11)

```

---

