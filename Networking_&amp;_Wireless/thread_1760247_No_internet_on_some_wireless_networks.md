---
title: "No internet on some wireless networks"
date: 2011-05-16
forum: Networking &amp; Wireless
---

### Post by spintriae on 2011-05-16
I've recently acquired a Samsung SCH-LC11 which is a Verizon 4G wifi hotspot. It works flawlessly with my iPod Touch, Android phone, and my laptop running Windows 7. On the same laptop running Ubuntu 10.04, it doesn't work at all.

At first, I couldn't connect to the network. Changing the encryption method got my connected, but I can't access the internet. Even with the network open, I can connect, but cannot access the internet. I can't even ping the router at 192.168.1.1.

I've had the same problem with other networks and read threads online suggesting installing the network card's Windows drivers. I installed ndisgtk, installed the Windows driver, blacklisted the generic driver and got wifi working, but it didn't fix my problem.

I read that Ubuntu has trouble with mixed 802.11 modes, so I tried changing them in the router. With b only, I can't even see the SSID. With g only, b/g, and b/g/n, I can connect, but without internet.

Here are some relevant logs.

```
kc@ubuntu:~/Downloads$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010]
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012]
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:00.0 Ethernet controller [0200]: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter [1969:1062] (rev c0)
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
```

```
kc@ubuntu:~/Downloads$ sudo lshw -C Network
[sudo] password for kc: 
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan1
       version: 01
       serial: 1c:4b:d6:bc:1b:ea
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netathw driverversion=1.55+,02/13/2009,7.7.0.233 ip=10.2.171.148 latency=0 link=yes multicast=yes wireless=IEEE 802.11g
       resources: irq:17 memory:fbff0000-fbffffff
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: c0
       serial: 48:5b:39:3e:b7:43
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A ip=192.168.1.101 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:29 memory:f7fc0000-f7ffffff ioport:ec00(size=128)
```

```
kc@ubuntu:~/Downloads$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netathw : driver installed
	device (168C:002B) present (alternate driver: ath9k)
```

---

### Post by spintriae on 2011-05-16
I turned off wifi, rebooted and ran dmesg with the following results.

```
kc@ubuntu:~$ dmesg | grep -e ndis -e wlan
[   21.491295] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   21.657543] eeepc_laptop: wlan hotplug disabled
[   22.480664] ndiswrapper: driver netathw (,02/13/2009,7.7.0.233) loaded
[   22.481302] ndiswrapper 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   22.482512] ndiswrapper 0000:02:00.0: setting latency timer to 64
[   22.482685] ndiswrapper (NdisMAllocateMapRegisters:971): Windows driver netathw requesting too many (256) map registers
[   22.554957] ndiswrapper: using IRQ 17
[   22.763457] wlan0: ethernet device 1c:4b:d6:bc:1b:ea using serialized NDIS driver: netathw, version: 0x70007, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:002B.5.conf
[   22.799146] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   22.803807] usbcore: registered new interface driver ndiswrapper
[   22.821818] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
[   22.821906] udev: renamed network interface wlan0 to wlan1
```

Then I turned on wifi, connected the network and ran dmesg again. These were the new messages.

```
[  104.076660] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  119.216458] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  119.261317] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
```

Finally, I loaded Chrome and tried refreshing this page. This was the new message.

```
[  130.025044] wlan1: no IPv6 routers present
```

---

