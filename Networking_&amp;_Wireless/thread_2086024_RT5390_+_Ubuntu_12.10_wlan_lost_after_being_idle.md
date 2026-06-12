---
title: "RT5390 + Ubuntu 12.10: wlan lost after being idle"
date: 2012-11-19
forum: Networking &amp; Wireless
---

### Post by orlenok41 on 2012-11-19
Hi,

I have a fresh Ubuntu 12.10 on a HP DM1Z laptop with the RT5390 wireless card. I was previously using 11.04 where everything worked fine (except that I had to compile the wireless driver myself)

I am losing wireless network connection completely after the laptop being idle for a while (but not necessarily going to sleep). It is impossible to get it back unless reloading the wireless module (rt2800pci). The dmesg trace below has some cfg80211 messages quoted below when the disconnect happens, I am not 100% sure it is related. Again, not sure if it is related but my router is running tomato USB with the "Regulatory Mode" set to Off for wireless (default setting) 

Any ideas how to fix this?

Many thanks in advance.

> 
[   23.091464] wlan0: associated
[   23.091791] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   48.905709] audit_printk_skb: 48 callbacks suppressed
[   48.905719] type=1701 audit(1353351965.884:28): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2146 comm="chromium-browse" reason="seccomp" sig=0 syscall=20 compat=0 ip=0xb2f43424 code=0x50000
[  985.681485] type=1701 audit(1353352903.759:29): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2729 comm="chromium-browse" reason="seccomp" sig=0 syscall=20 compat=0 ip=0xb2f1d424 code=0x50000
[ 1517.081853] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1517.081872] cfg80211: Restoring regulatory settings
[ 1517.081925] cfg80211: Calling CRDA to update world regulatory domain
[ 1517.098749] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1517.098765] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1517.098772] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1517.098779] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1517.098786] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 1517.098792] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1517.098799] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1517.098805] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1517.098811] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1517.098818] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1517.098824] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1517.098830] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1517.098836] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1517.098842] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1517.098848] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1517.098855] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1517.098860] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1517.098867] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1517.098872] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1517.098879] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1517.098885] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1517.098891] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1517.098897] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 1517.098903] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1517.098909] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 1517.098915] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1517.098921] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 1517.098928] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1517.098936] cfg80211: World regulatory domain updated:
[ 1517.098941] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1517.098948] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1517.098954] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1517.098960] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1517.098966] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1517.098973] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1532.888659] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1909.360631] nfs: server 192.168.1.5 not responding, timed out
[ 2281.746527] nfs: server 192.168.1.5 not responding, timed out
[ 2281.746570] NFS: state manager failed on NFSv4 server 192.168.1.5 with error 5
[ 2462.312658] nfs: server 192.168.1.5 not responding, timed out



---

### Post by orlenok41 on 2012-12-03
If anyone is searching for this, here is the solution: compile and install the official rt5390sta driver from ralink. It works much better than the ubuntu one included by default: I have had 0 connection drops in two days.

---

