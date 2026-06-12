---
title: "Network Problem Acer Aspire 7551G on 11.04"
date: 2011-05-15
forum: Networking &amp; Wireless
---

### Post by FMKaiba on 2011-05-15
I searched everything before posting this, and tried every solution, but so far no luck, i will post my info, and hope someone smarter then me can solve this?

Wireless works fine in windows, but apears disabled in ubuntu

lspci -nn
```
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS880 Host Bridge [1022:9601]
00:02.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0) [1022:9603]
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) [1022:9604]
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) [1022:9605]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 41)
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
02:00.0 VGA compatible controller [0300]: ATI Technologies Inc Redwood [Radeon HD 5600 Series] [1002:68c1]
02:00.1 Audio device [0403]: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series] [1002:aa60]
03:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
06:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
```

sudo lshw -C network
```
 *-network               
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 00:26:2d:a2:04:95
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=sb ip=192.168.1.116 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:44 memory:d0100000-d010ffff
  *-network DISABLED
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 78:e4:00:18:bf:56
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-9-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d0200000-d020ffff
```


lsmod | grep ath
```
ath9k                 118238  0 
mac80211              294370  1 ath9k
ath9k_common           13851  1 ath9k
ath9k_hw              323077  2 ath9k,ath9k_common
ath                    23773  2 ath9k,ath9k_hw
cfg80211              178528  3 ath9k,mac80211,ath
```

lsmod | grep tg3
```
tg3                   141750  0 
```

dmesg | grep ath
```
[    0.900281]  [<ffffffff81065c9f>] ? warn_slowpath_common+0x7f/0xc0
[    0.900284]  [<ffffffff81065d96>] ? warn_slowpath_fmt+0x46/0x50
[    1.910641] device-mapper: multipath: version 1.2.0 loaded
[    1.910645] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.288635] ath9k 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.288645] ath9k 0000:06:00.0: setting latency timer to 64
[    3.716830] ath: EEPROM regdomain: 0x65
[    3.716832] ath: EEPROM indicates we should expect a direct regpair map
[    3.716835] ath: Country alpha2 being used: 00
[    3.716837] ath: Regpair used: 0x65
[    3.733868] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[    3.734528] Registered led device: ath9k-phy0::radio
[    3.734552] Registered led device: ath9k-phy0::assoc
[    3.734574] Registered led device: ath9k-phy0::tx
[    3.734592] Registered led device: ath9k-phy0::rx
```

dmesg | grep tg3
```
[    1.976038] tg3.c:v3.116 (December 3, 2010)
[    1.976059] tg3 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.976067] tg3 0000:03:00.0: setting latency timer to 64
[    2.122186] tg3 mdio bus: probed
[    2.143820] tg3 0000:03:00.0: eth0: Tigon3 [partno(BCM57780) rev 57780001] (PCI Express) MAC address 00:26:2d:a2:04:95
[    2.143824] tg3 0000:03:00.0: eth0: attached PHY driver [Broadcom BCM57780] (mii_bus:phy_addr=300:01)
[    2.143828] tg3 0000:03:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    2.143831] tg3 0000:03:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    3.111078] tg3 0000:03:00.0: irq 44 for MSI/MSI-X
[    3.144067] tg3 0000:03:00.0: eth0: Link is down
[  322.161093] tg3 0000:03:00.0: eth0: Link is up at 100 Mbps, full duplex
[  322.161104] tg3 0000:03:00.0: eth0: Flow control is on for TX and on for RX
```

rfkill list all
```
0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: acer-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

Items of note:
the laptop has no bluetooth chip, so i am not sure where "acer-bluetooth" is coming from.

Also i am quite familar with linux, so no need to hold my hand, i am just not sure what to do next in this situation. (if this makes solving this easier)

PS:
There is no 'hardware switch' on the laptop, but there is a Fn+F3 key combination which does nothing.
network-manager shows on startup 'Enable wireless' with no check next to it, checking it 'Enables' it, but the wireless remains disabled.

Wireless indicator LED on the laptop never comes on

---

### Post by FMKaiba on 2011-05-15
Solved it, for some reason the module 'acer_wmi' was being loaded.

I am not sure what it does, but 'sudo rmmod acer_wmi' solves it.

I have added acer_wmi to my blacklist, and all is well now.



Though if anyone knows, will i see any adverse affects from not having this module?

---

