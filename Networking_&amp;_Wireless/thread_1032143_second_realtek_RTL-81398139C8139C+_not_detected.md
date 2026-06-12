---
title: "second realtek RTL-8139/8139C/8139C+ not detected"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by DataMatrix on 2009-01-06
I have the folloing hardware on my machine:
Attansic Technology Corp. L1 Gigabit Ethernet Adapter (onboard) [eth2]
Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (pci) [eth1]
Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (pci) <problem>

The two realtek cards are 1:1 identical. The problem is that ubuntu doesn't detect the second card, not in lspci, nor it's in dmesg. I used to have a different card there (a Reaktek 8139D infact), but it had to be replaced, so now there is a hole in place of eth0. Is there any way to get the second card working, or do I have to find a different card from different manufacturer?

```
uname -a
Linux pripyat 2.6.27-9-server #1 SMP Thu Nov 20 22:53:41 UTC 2008 i686 GNU/Linux
```
```
dmesg | grep -i eth
[    3.208880] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    4.575542] 8139too Fast Ethernet driver 0.9.28
[    4.811942] eth1: RealTek RTL8139 at 0xe800, 00:19:e0:13:c6:24, IRQ 18
[    4.812005] eth1:  Identified 8139 chip type 'RTL-8100B/8139D'
[    5.018793] Driver 'sd' needs updating - please use bus_type methods
[   15.107956] udev: renamed network interface eth0 to eth2
[   19.516521] atl1 0000:04:00.0: eth2 link is up 100 Mbps full duplex
[   20.397433] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
```
```
lspci -nn
01:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
04:00.0 Ethernet controller [0200]: Attansic Technology Corp. L1 Gigabit Ethernet Adapter [1969:1048] (rev b0)
```
:confused:

Edit:
I've tried **sudo update-initramfs -c -v -k `uname -r`**, but it didn't work ether.
I think I had similar problem before, but it disappeared by itself back then, I have no idea how.

---

### Post by DataMatrix on 2009-01-06
I've solved the problem though I'm not sure if it was the right way to go:
I've halted the machine, puled out the problematic eth out of the pci slot, started the machine again. As expected, all readings of lspci, lshw and dmesg are about the same as before, as if the card wasn't there in the first place. I've halted again and put the card back. After the machine started, I now get 
```
lspci -nn
01:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
01:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
04:00.0 Ethernet controller [0200]: Attansic Technology Corp. L1 Gigabit Ethernet Adapter [1969:1048] (rev b0)
```

I remember that when I changed the old card with this new one, I didn't boot the machine inbetween, and it probably was looking for the old card where the new one was and it didn't remove it (I don't have any hard evidence on that statement). Now the new card is eth3 instead of eth0, but that isn't that much of a problem.

Should this be filed as a bug report?

---

