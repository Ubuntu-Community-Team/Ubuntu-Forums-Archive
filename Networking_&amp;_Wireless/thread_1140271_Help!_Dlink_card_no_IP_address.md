---
title: "Help! Dlink card no IP address"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by ManyBeers on 2009-04-27
Sony laptop running Ubuntu 8.04 using external Dlink dwl g630 pcmcia wireless card. I installed ndiswrapper through Synaptic
today and also the WindowsXP driver that came with the card.
My card is recognized and the link light is on but I get no IP address. Using a 26 character WEP key(is that hexadecimal?)
Could somebody help me troubleshoot this problem please?

lsmod | grep ndis
ndiswrapper           192920  0
usbcore               146028  4 ndiswrapper,usbhid,uhci_hcd
mark@ubuntu:~$ dmesg | grep -e ndis -e wlan
[ 5382.064300] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 5382.210595] ndiswrapper: driver mrv8k51 (D-Link,12/21/2003,2.2.0.19) loaded
[ 5382.213140] ndiswrapper: using IRQ 9
[ 5382.504005] wlan0: ethernet device 00:0f:3d:04:c4:f5 using NDIS driver: mrv8k51, version: 0x202000b, NDIS version: 0x501, vendor: 'Marvell 802.11 Driver', 11AB:1FA6.5.conf
[ 5382.504036] ndiswrapper (set_iw_encr_mode:717): setting encryption mode to 6 failed (C00000BB)
[ 5382.504047] wlan0: encryption modes supported: WEP; TKIP with WPA
[ 5382.504149] usbcore: registered new interface driver ndiswrapper
[ 5383.409553] ndiswrapper (set_essid:59): setting essid failed (C0000001)
[ 5383.421139] ndiswrapper (set_essid:59): setting essid failed (C0000001)
[10804.577904] ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

