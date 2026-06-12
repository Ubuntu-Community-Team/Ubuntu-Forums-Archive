---
title: "Cannot connect to Wireless LAN in Ad-Hoc mode"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by mn_lay on 2009-03-11
First, I have WindowsXP-based desktop with TP-Link TL-WN821N Wi-Fi card, mode set to Ad-Hoc. Security mode is None/Unencrypted. I use ICS on that interface, so DHCP is working there.
Second, I have HP 6830s laptop with Ubuntu 8.10 x64 and Intel 5100 Wi-Fi card, mode set to Ad-Hoc too. Driver is iwlagn, and I suppose it works fine. SSIDs on both machines are same.

The problem is, I cannot connect from Ubuntu laptop to Windows PC. Network Manager was useless, so I switched to WICD. It hangs during "Obtaining IP address" stage. I tried to follow these instructions: [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)
I got same results in manual mode: upon executing **dhclient wlan0** I have no DHCPOFFER reply from PC, and PC shows "no link" status as well.

However, I was able to connect using Windows 7 x64 (beta) on this laptop. Didn't enter anything, just made a single click. More interesting, I'm able to connect **from** Windows PC **to** Ubuntu laptop. I press "connect" in Windows and in the same time execute **dhclient wlan0** on Ubuntu. Windows connects and Ubuntu receives DHCP settings. Everything works but WICD behaves oddly: about 10 seconds it shows "Connected to my_ssid at 0% (192.168.0.1)", then about 3 seconds it shows "Not connected", and round and round.

So how can I connect **from** Ubuntu?

Oh, BTW here's ls-es:
> lsusb
Bus 001 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]

lspci
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
86:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 436c

lshw -C network
  *-network
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:6b:1f:c0:70
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:86:00.0
       logical name: eth0
       version: 00
       serial: 00:22:64:5b:f0:6e
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.0.172 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=1GB/s
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 1e:3c:a7:6a:fd:61
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by mn_lay on 2009-03-11
Just tried Network Manager again. Same thing: I can only connect from Windows to Ubuntu. Network Manager also shows 0% signal quality while it's 96-100% in real.

---

