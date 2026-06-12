---
title: "ath 928x installed, showing up, not working"
date: 2009-02-21
forum: Networking &amp; Wireless
---

### Post by booshire on 2009-02-21
Alright, gonna start off saying this was working. I was trying to get the wireless button working for some reason and it randomly worked (don't ask) and disabled wireless. Could not get it back. Had many other unrelated issues, audio being one, so I just did a fresh install after backing up.

ISSUE:
Have HP G60-230US with 8.10_x86
Wireless shows up lspci as Atheros 928X:

02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Hewlett-Packard Company Device 1381
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at d2600000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

Have installed compat-wireless-ath9k (9/16/08) after upgrading from 8.04
Obviously the card shows up just fine. I can see it in if- and iwconfig
as well as iwlist. It is showing up:

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:0f:c4:f4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

If I try to connect to a network it tries and times out, cannot scan for networks and manually settings (obviously) do not help either.

AFAICT nothing blacklisted by ath9k install.

Here is what I remember doing last time I got it working (don't quote me on this i was a little drunk):

1 - tried using madwifi, did not work at all
2 - remember installing script for Mac drivers (realized during script what I was doing but let it go) - nothing
3 - installed ath9k off of their website and saw what I see now
4 - modprobe'd ath9k and it started working permanently

SIDE NOTE: I know this works OoB with Fedora 10 x86 because it was installed too but never actually used for anything

I have to use this for work Monday and want it working.
Please Help, assume just missing some file or a command

btw, here is OP for modprobe -l|grep ath:
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/ath5k/ath5k.ko
/lib/modules/2.6.27-11-generic/volatile/ath_hal.ko
/lib/modules/2.6.27-11-generic/volatile/ath_pci.ko
/lib/modules/2.6.27-11-generic/volatile/ath_rate_amrr.ko
/lib/modules/2.6.27-11-generic/volatile/ath_rate_minstrel.ko
/lib/modules/2.6.27-11-generic/volatile/ath_rate_onoe.ko
/lib/modules/2.6.27-11-generic/volatile/ath_rate_sample.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/ath9k/ath9k.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/md/multipath.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/md/dm-multipath.ko

Hope this is some good information to go by.

---

