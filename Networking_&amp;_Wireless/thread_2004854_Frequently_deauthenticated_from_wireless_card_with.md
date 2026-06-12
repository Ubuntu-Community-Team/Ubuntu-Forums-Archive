---
title: "Frequently deauthenticated from wireless card with reason 7"
date: 2012-06-16
forum: Networking &amp; Wireless
---

### Post by charlie cat on 2012-06-16
Hello,
Recently I noticed that my Internet connection was working very slowly, with high packet loss rates.  The problem is localized to my computer, as other computers connect through the same wireless router with no problems.
The cause seems to be that, about once per minute, the firmware deauthenticates itself from the wireless card, "restore[s] regulatory settings", and then reauthenticates.
Specifically, the following message appears in /var/logs/kern.log about once per minute:
```
Jun 16 14:49:00 my-desktop kernel: [ 1567.388067] wlan0: deauthenticated from [MAC ADDRESS REMOVED] (Reason: 7)
Jun 16 14:49:00 my-desktop kernel: [ 1567.388507] wlan0: moving STA [MAC ADDRESS REMOVED] to state 2
Jun 16 14:49:00 my-desktop kernel: [ 1567.388515] wlan0: moving STA [MAC ADDRESS REMOVED] to state 1
Jun 16 14:49:00 my-desktop kernel: [ 1567.388520] wlan0: moving STA [MAC ADDRESS REMOVED] to state 0
Jun 16 14:49:00 my-desktop kernel: [ 1567.404950] cfg80211: All devices are disconnected, going to restore regulatory settings
Jun 16 14:49:00 my-desktop kernel: [ 1567.404963] cfg80211: Restoring regulatory settings
Jun 16 14:49:00 my-desktop kernel: [ 1567.404973] cfg80211: Calling CRDA to update world regulatory domain
Jun 16 14:49:00 my-desktop kernel: [ 1567.424815] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Jun 16 14:49:00 my-desktop kernel: [ 1567.424825] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 16 14:49:00 my-desktop kernel: [ 1567.424832] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Jun 16 14:49:00 my-desktop kernel: [ 1567.424839] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 16 14:49:00 my-desktop kernel: [ 1567.424846] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Jun 16 14:49:00 my-desktop kernel: [ 1567.424854] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 16 14:49:00 my-desktop kernel: [ 1567.424860] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Jun 16 14:49:00 my-desktop kernel: [ 1567.424867] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 16 14:49:00 my-desktop kernel: [ 1567.424872] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Jun 16 14:49:00 my-desktop kernel: [ 1567.424879] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 16 14:49:00 my-desktop kernel: [ 1567.424885] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Jun 16 14:49:00 my-desktop kernel: [ 1567.424892] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 16 14:49:00 my-desktop kernel: [ 1567.424898] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Jun 16 14:49:00 my-desktop kernel: [ 1567.424905] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 16 14:49:00 my-desktop kernel: [ 1567.424911] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Jun 16 14:49:00 my-desktop kernel: [ 1567.424917] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 16 14:49:00 my-desktop kernel: [ 1567.424923] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Jun 16 14:49:00 my-desktop kernel: [ 1567.424930] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 16 14:49:00 my-desktop kernel: [ 1567.424936] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Jun 16 14:49:00 my-desktop kernel: [ 1567.424944] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 16 14:49:00 my-desktop kernel: [ 1567.424951] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Jun 16 14:49:00 my-desktop kernel: [ 1567.424958] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 16 14:49:00 my-desktop kernel: [ 1567.424965] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Jun 16 14:49:00 my-desktop kernel: [ 1567.424971] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 16 14:49:00 my-desktop kernel: [ 1567.424977] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Jun 16 14:49:00 my-desktop kernel: [ 1567.424983] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 16 14:49:00 my-desktop kernel: [ 1567.424989] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
Jun 16 14:49:00 my-desktop kernel: [ 1567.424996] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 16 14:49:00 my-desktop kernel: [ 1567.425004] cfg80211: World regulatory domain updated:
Jun 16 14:49:00 my-desktop kernel: [ 1567.425009] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun 16 14:49:00 my-desktop kernel: [ 1567.425016] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 16 14:49:00 my-desktop kernel: [ 1567.425022] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 16 14:49:00 my-desktop kernel: [ 1567.425028] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 16 14:49:00 my-desktop kernel: [ 1567.425034] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 16 14:49:00 my-desktop kernel: [ 1567.425040] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 16 14:49:01 my-desktop kernel: [ 1568.668669] wlan0: authenticate with [MAC ADDRESS REMOVED] (try 1)
Jun 16 14:49:01 my-desktop kernel: [ 1568.670210] wlan0: authenticated
Jun 16 14:49:01 my-desktop kernel: [ 1568.671243] wlan0: associate with [MAC ADDRESS REMOVED] (try 1)
Jun 16 14:49:01 my-desktop kernel: [ 1568.673351] wlan0: RX ReassocResp from [MAC ADDRESS REMOVED] (capab=0x401 status=0 aid=6)
Jun 16 14:49:01 my-desktop kernel: [ 1568.673359] wlan0: associated
Jun 16 14:49:01 my-desktop kernel: [ 1568.673367] wlan0: moving STA [MAC ADDRESS REMOVED] to state 1
Jun 16 14:49:01 my-desktop kernel: [ 1568.673373] wlan0: moving STA [MAC ADDRESS REMOVED] to state 2
Jun 16 14:49:01 my-desktop kernel: [ 1568.675284] wlan0: moving STA [MAC ADDRESS REMOVED] to state 3

```My wireless card (as described by lshw):
 ```
 *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:02:09.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:21 memory:f7efe000-f7efffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: [REMOVED]
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.2.0-25-generic firmware=410.2160 ip=[REMOVED] link=yes multicast=yes wireless=IEEE 802.11bg

```I tried the advice at [http://askubuntu.com/questions/54153/my-wifi-gets-deauthenticated-every-few-minutes-or-seconds-reason-7](http://askubuntu.com/questions/54153/my-wifi-gets-deauthenticated-every-few-minutes-or-seconds-reason-7) to no avail.

All help is appreciated.

---

### Post by charlie cat on 2012-06-17
Silly me!
I was able to fix both problems (slow Internet + strange logs) just by fiddling with the antenna on my wireless card.

---

