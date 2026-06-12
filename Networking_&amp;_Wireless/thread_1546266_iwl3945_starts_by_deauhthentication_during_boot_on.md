---
title: "iwl3945 starts by deauhthentication during boot on 10.04"
date: 2010-08-05
forum: Networking &amp; Wireless
---

### Post by bragaa on 2010-08-05
Hi all,

A recent upgrade to 10.04 has broken my wireless card connectivity. Other issues also arised (compiz not started by default, slow boot) and think that all that might be due to a corrupted upgrade. So I've tried to reconfigure all pkgs, to no avail.

For the wireless issues, I've noticed that the card starts by deauthentication, and that there is an extra time probably spent by the card ? (19 to 29 is spent in 'wlan0: deauthenticating from 00:13:f7:66:ed:8b by local choice (reason=3)', is'nt it ?)
Here is the the 'relevant' dmesg output :
```
[   19.233803] vga16fb: mapped to 0xc00a0000
[   19.233808] vga16fb: not registering due to another framebuffer present
[   19.609601] Console: switching to colour frame buffer device 160x50
[   29.420851] wlan0: deauthenticating from 00:13:f7:66:ed:8b by local choice (reason=3)
[   29.422183] wlan0: direct probe to AP 00:13:f7:66:ed:8b (try 1)
[   29.430015] wlan0: direct probe responded
[   29.430022] wlan0: authenticate with AP 00:13:f7:66:ed:8b (try 1)
[   29.433567] wlan0: authenticated
[   29.433683] wlan0: associate with AP 00:13:f7:66:ed:8b (try 1)
[   29.443585] wlan0: RX AssocResp from 00:13:f7:66:ed:8b (capab=0x431 status=0 aid=1)
[   29.443590] wlan0: associated
[   29.445084] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   29.445154] cfg80211: Calling CRDA for country: NL
[   29.470839] cfg80211: Received country IE:
[   29.470845] cfg80211: Regulatory domain: NL
[   29.470847] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   29.470852] 	(2402000 KHz - 2494000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
[   29.470854] cfg80211: CRDA thinks this should applied:
[   29.470857] cfg80211: Regulatory domain: NL
[   29.470859] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   29.470863] 	(2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   29.470866] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   29.470870] 	(5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   29.470873] 	(5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   29.470875] cfg80211: We intersect both of these and get:
[   29.470878] cfg80211: Regulatory domain: 98
[   29.470880] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   29.470884] 	(2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   29.470890] cfg80211: Leaving channel 5170 MHz intact on phy0 - no rule found in band on Country IE
[   29.470894] cfg80211: Leaving channel 5180 MHz intact on phy0 - no rule found in band on Country IE
[   29.470897] cfg80211: Leaving channel 5190 MHz intact on phy0 - no rule found in band on Country IE
[   29.470900] cfg80211: Leaving channel 5200 MHz intact on phy0 - no rule found in band on Country IE
[   29.470903] cfg80211: Leaving channel 5210 MHz intact on phy0 - no rule found in band on Country IE
[   29.470906] cfg80211: Leaving channel 5220 MHz intact on phy0 - no rule found in band on Country IE
[   29.470910] cfg80211: Leaving channel 5230 MHz intact on phy0 - no rule found in band on Country IE
[   29.470913] cfg80211: Leaving channel 5240 MHz intact on phy0 - no rule found in band on Country IE
[   29.470916] cfg80211: Leaving channel 5260 MHz intact on phy0 - no rule found in band on Country IE
[   29.470919] cfg80211: Leaving channel 5280 MHz intact on phy0 - no rule found in band on Country IE
[   29.470922] cfg80211: Leaving channel 5300 MHz intact on phy0 - no rule found in band on Country IE
[   29.470925] cfg80211: Leaving channel 5320 MHz intact on phy0 - no rule found in band on Country IE
[   29.470928] cfg80211: Leaving channel 5500 MHz intact on phy0 - no rule found in band on Country IE
[   29.470931] cfg80211: Leaving channel 5520 MHz intact on phy0 - no rule found in band on Country IE
[   29.470935] cfg80211: Leaving channel 5540 MHz intact on phy0 - no rule found in band on Country IE
[   29.470938] cfg80211: Leaving channel 5560 MHz intact on phy0 - no rule found in band on Country IE
[   29.470941] cfg80211: Leaving channel 5580 MHz intact on phy0 - no rule found in band on Country IE
[   29.470944] cfg80211: Leaving channel 5600 MHz intact on phy0 - no rule found in band on Country IE
[   29.470947] cfg80211: Leaving channel 5620 MHz intact on phy0 - no rule found in band on Country IE
[   29.470951] cfg80211: Leaving channel 5640 MHz intact on phy0 - no rule found in band on Country IE
[   29.470954] cfg80211: Leaving channel 5660 MHz intact on phy0 - no rule found in band on Country IE
[   29.470957] cfg80211: Leaving channel 5680 MHz intact on phy0 - no rule found in band on Country IE
[   29.470960] cfg80211: Leaving channel 5700 MHz intact on phy0 - no rule found in band on Country IE
[   29.470964] cfg80211: Current regulatory domain updated by AP to: NL
[   29.470966] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   29.470970] 	(2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   31.953709] padlock: VIA PadLock not detected.
[   39.808048] wlan0: no IPv6 routers present
[  716.841079] CE: hpet increasing min_delta_ns to 15000 nsec

```

Here is the the lsmod output

```

04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
	Subsystem: Intel Corporation Device 1001
	Flags: bus master, fast devsel, latency 0, IRQ 30
	Memory at f0200000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [c8] Power Management version 2
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Device Serial Number 88-ec-e2-ff-ff-77-1b-00
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945

```

---

### Post by fearpi on 2010-08-13
I also have a 3945 and have been getting this failure to connect as well. Typical dmesg output:

```
[ 6357.644789] wlan0: deauthenticating from 68:7f:74:2a:f3:4a by local choice (reason=3)
[ 6357.680669] wlan0: direct probe to AP 68:7f:74:2a:f3:4a (try 1)
[ 6357.880072] wlan0: direct probe to AP 68:7f:74:2a:f3:4a (try 2)
[ 6357.884561] wlan0: direct probe responded
[ 6357.884568] wlan0: authenticate with AP 68:7f:74:2a:f3:4a (try 1)
[ 6357.886378] wlan0: authenticated
[ 6357.886413] wlan0: associate with AP 68:7f:74:2a:f3:4a (try 1)
[ 6357.889021] wlan0: RX AssocResp from 68:7f:74:2a:f3:4a (capab=0x411 status=0 aid=1)
[ 6357.889028] wlan0: associated
[ 6403.677063] wlan0: deauthenticating from 68:7f:74:2a:f3:4a by local choice (reason=3)
```

Never had a problem before 10.04; haven't been able to solve it or connect.

---

