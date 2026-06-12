---
title: "Inconsistent/very slow wifi - BCM4311 Ubuntu 12.10"
date: 2012-11-29
forum: Networking &amp; Wireless
---

### Post by mace2 on 2012-11-29
Hi all,

I recently upgraded to 12.10 (clean install) and I have had some wireless issues. I installed the proper driver for my BCM4311 (b43-fwcutter and all that) but my internet has been very inconsistent. Sometimes it struggles to load Google, and other times I can pull over 1MB/s.

I had no problems with 12.04. If you could give me any advice I would be very grateful. Thanks.

P.S. I have attached some information based on previous threads which might be relevant (?).

```
koma@Voyager:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) [8086:2a03] (rev 0c)
00:1a.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 02)
00:1d.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] [8086:2829] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

```

```
koma@Voyager:~$ lsmod | grep -e b43 -e ssb -e wl
b43                   369753  0 
mac80211              539908  1 b43
cfg80211              206566  2 b43,mac80211
bcma                   35656  1 b43
ssb_hcd                12869  0 
ssb                    52036  2 b43,ssb_hcd
koma@Voyager:~$ dmesg | grep -e b43 -e ssb -e wl
[    1.252204] ssb: Found chip with id 0x4311, rev 0x01 and package 0x00
[    1.252221] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[    1.252231] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[    1.252240] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[    1.252249] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[    1.316163] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
[   12.982922] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   13.399086] Registered led device: b43-phy0::tx
[   13.399112] Registered led device: b43-phy0::rx
[   13.399134] Registered led device: b43-phy0::radio
[   17.708062] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   17.805528] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.805856] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.256781] wlan0: authenticate with 68:7f:74:01:39:ee
[   20.280220] wlan0: send auth to 68:7f:74:01:39:ee (try 1/3)
[   20.287626] wlan0: authenticated
[   20.288075] wlan0: associate with 68:7f:74:01:39:ee (try 1/3)
[   20.297137] wlan0: RX AssocResp from 68:7f:74:01:39:ee (capab=0x411 status=0 aid=1)
[   20.297599] wlan0: associated
[   20.298174] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
koma@Voyager:~$ 
```

---

### Post by mace2 on 2012-12-05
Anyone have any ideas? When the connection gets really slow my other wifi-connected devices (e.g. tablet, phone) have no issues. So I'm not sure what's going on.

It couldn't be an IP conflict or something, right? When I booted into Windows on my laptop it seemed to say something about that... but I tried rebooting the router/cable modem and it didn't help.

---

### Post by slimsbims on 2013-01-03
Dear all,

I had the same issue with a BCM4313 under Ubuntu 12.10 64 bit, a Lenovo Ideapad.

What improved the situation were 2 things:

1) Switch in the router to wireless-mode b+g only (thus turning off 'n')
2) Assign a dedicated channel within this band, which means manually trying out what works best, and not letting decide the router in auto mode.

Maybe this can be of any help to you as well.

---

