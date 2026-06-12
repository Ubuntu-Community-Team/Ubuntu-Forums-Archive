---
title: "iwl4965: Microcode SW error detected. Restarting 0x2000000"
date: 2009-10-07
forum: Networking &amp; Wireless
---

### Post by DantePasquale on 2009-10-07
Hi Everyone,

I've been experiencing the problem on my laptop (jetbook with intel motherboard and pretty standard stuff on it). I'm running 9.04 64 bit and didn't have this problem on 8.10 64 bit.

I see many, many posts and bug entries for this problem, but I'm experiencing it anytime I get busy networking. I don't see any solutions per se, but one looked promising with new microcode and drivers from Intel at [http://http://intellinuxwireless.org/?n=downloads&f=ucodes_4965&p=iwlwifi]("http://http://intellinuxwireless.org/?n=downloads&f=ucodes_4965&p=iwlwifi") but I have no idea if this is the correct thing to do in my case. I'm experienced with drivers, etc, but I've found them hard to maintain when deviating from the standard distribution (most recently HP HBA and Network Drivers v. RedHat bundled drivers for the same hardware).

I'm open to advise on this issue.

Here's my log entry, it's rather lengthy this time as the wireless really puked and I had to reboot. Oh, I'm also using wicd and usually a disconnect/reconnect re-establishes my connection but this time it didn't.

```
Oct  7 21:36:22 dexter kernel: [92729.031201] iwlagn: Microcode SW error detected.  Restarting 0x2000000.
Oct  7 21:36:25 dexter kernel: [92732.392370] iwlagn: Can't stop Rx DMA.
Oct  7 21:36:25 dexter kernel: [92732.392734] iwlagn: MAC is in deep sleep!
Oct  7 21:36:25 dexter kernel: [92732.636129] Registered led device: iwl-phy0:radio
Oct  7 21:36:25 dexter kernel: [92732.636170] Registered led device: iwl-phy0:assoc
Oct  7 21:36:25 dexter kernel: [92732.636206] Registered led device: iwl-phy0:RX
Oct  7 21:36:25 dexter kernel: [92732.636242] Registered led device: iwl-phy0:TX
Oct  7 21:39:02 dexter /USR/SBIN/CRON[14587]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Oct  7 21:40:01 dexter /USR/SBIN/CRON[14804]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Oct  7 21:40:14 dexter kernel: [92961.639871] wlan0: deauthenticated
Oct  7 21:40:15 dexter kernel: [92961.648197] mac80211-phy0: failed to remove key (0, 00:1b:2f:6c:11:c0) from hardware (-22)
Oct  7 21:40:15 dexter kernel: [92962.636214] wlan0: direct probe to AP 00:1b:2f:6c:11:c0 try 1
Oct  7 21:40:15 dexter kernel: [92962.638933] wlan0 direct probe responded
Oct  7 21:40:15 dexter kernel: [92962.638944] wlan0: authenticate with AP 00:1b:2f:6c:11:c0
Oct  7 21:40:15 dexter kernel: [92962.640854] wlan0: authenticated
Oct  7 21:40:15 dexter kernel: [92962.640863] wlan0: associate with AP 00:1b:2f:6c:11:c0
Oct  7 21:40:15 dexter kernel: [92962.643507] wlan0: RX ReassocResp from 00:1b:2f:6c:11:c0 (capab=0x431 status=0 aid=4)
Oct  7 21:40:15 dexter kernel: [92962.643513] wlan0: associated
Oct  7 21:40:15 dexter kernel: [92962.669294] phy0: failed to restore operational channel after scan
dante@dexter:~$ tail -f /var/log/syslog
Oct  7 21:40:14 dexter kernel: [92961.639871] wlan0: deauthenticated
Oct  7 21:40:15 dexter kernel: [92961.648197] mac80211-phy0: failed to remove key (0, 00:1b:2f:6c:11:c0) from hardware (-22)
Oct  7 21:40:15 dexter kernel: [92962.636214] wlan0: direct probe to AP 00:1b:2f:6c:11:c0 try 1
Oct  7 21:40:15 dexter kernel: [92962.638933] wlan0 direct probe responded
Oct  7 21:40:15 dexter kernel: [92962.638944] wlan0: authenticate with AP 00:1b:2f:6c:11:c0
Oct  7 21:40:15 dexter kernel: [92962.640854] wlan0: authenticated
Oct  7 21:40:15 dexter kernel: [92962.640863] wlan0: associate with AP 00:1b:2f:6c:11:c0
Oct  7 21:40:15 dexter kernel: [92962.643507] wlan0: RX ReassocResp from 00:1b:2f:6c:11:c0 (capab=0x431 status=0 aid=4)
Oct  7 21:40:15 dexter kernel: [92962.643513] wlan0: associated
Oct  7 21:40:15 dexter kernel: [92962.669294] phy0: failed to restore operational channel after scan
Oct  7 21:41:13 dexter dhclient: Internet Systems Consortium DHCP Client V3.1.1
Oct  7 21:41:13 dexter dhclient: Copyright 2004-2008 Internet Systems Consortium.
Oct  7 21:41:13 dexter dhclient: All rights reserved.
Oct  7 21:41:13 dexter dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Oct  7 21:41:13 dexter dhclient: 
Oct  7 21:41:13 dexter dhclient: wmaster0: unknown hardware address type 801
Oct  7 21:41:13 dexter dhclient: wmaster0: unknown hardware address type 801
Oct  7 21:41:13 dexter dhclient: Bind socket to interface: No such device
Oct  7 21:41:13 dexter avahi-daemon[3172]: Withdrawing address record for 74.1.46.173 on wlan0.
Oct  7 21:41:14 dexter avahi-daemon[3172]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 74.1.46.173.
Oct  7 21:41:14 dexter kernel: [93021.014536] iwlagn: MAC is in deep sleep!
Oct  7 21:41:14 dexter avahi-daemon[3172]: Interface wlan0.IPv4 no longer relevant for mDNS.
Oct  7 21:41:14 dexter avahi-daemon[3172]: Withdrawing address record for fe80::213:e8ff:fef2:904d on wlan0.
Oct  7 21:41:14 dexter kernel: [93021.238013] Registered led device: iwl-phy0:radio
Oct  7 21:41:14 dexter kernel: [93021.238073] Registered led device: iwl-phy0:assoc
Oct  7 21:41:14 dexter kernel: [93021.238110] Registered led device: iwl-phy0:RX
Oct  7 21:41:14 dexter kernel: [93021.238146] Registered led device: iwl-phy0:TX
Oct  7 21:41:14 dexter kernel: [93021.276530] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct  7 21:41:19 dexter kernel: [93026.486426] iwlagn: MAC is in deep sleep!
Oct  7 21:41:19 dexter dhclient: Internet Systems Consortium DHCP Client V3.1.1
Oct  7 21:41:19 dexter dhclient: Copyright 2004-2008 Internet Systems Consortium.
Oct  7 21:41:19 dexter dhclient: All rights reserved.
Oct  7 21:41:19 dexter dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Oct  7 21:41:19 dexter dhclient: 
Oct  7 21:41:19 dexter dhclient: wmaster0: unknown hardware address type 801
Oct  7 21:41:19 dexter dhclient: wmaster0: unknown hardware address type 801
Oct  7 21:41:19 dexter dhclient: Bind socket to interface: No such device
Oct  7 21:41:19 dexter dhclient: Internet Systems Consortium DHCP Client V3.1.1
Oct  7 21:41:19 dexter dhclient: Copyright 2004-2008 Internet Systems Consortium.
Oct  7 21:41:19 dexter dhclient: All rights reserved.
Oct  7 21:41:19 dexter dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Oct  7 21:41:19 dexter dhclient: 
Oct  7 21:41:19 dexter dhclient: wmaster0: unknown hardware address type 801
Oct  7 21:41:19 dexter dhclient: wmaster0: unknown hardware address type 801
Oct  7 21:41:19 dexter dhclient: Bind socket to interface: No such device
Oct  7 21:41:20 dexter kernel: [93026.980076] Registered led device: iwl-phy0:radio
Oct  7 21:41:20 dexter kernel: [93026.980609] Registered led device: iwl-phy0:assoc
Oct  7 21:41:20 dexter kernel: [93026.981882] Registered led device: iwl-phy0:RX
Oct  7 21:41:20 dexter kernel: [93026.981934] Registered led device: iwl-phy0:TX
Oct  7 21:41:20 dexter kernel: [93027.015124] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct  7 21:41:20 dexter kernel: [93027.618332] wlan0: deauthenticating by local choice (reason=3)
Oct  7 21:41:21 dexter kernel: [93027.979339] iwlagn: MAC is in deep sleep!
Oct  7 21:41:21 dexter kernel: [93028.897685] Registered led device: iwl-phy0:radio
Oct  7 21:41:21 dexter kernel: [93028.897728] Registered led device: iwl-phy0:assoc
Oct  7 21:41:21 dexter kernel: [93028.897766] Registered led device: iwl-phy0:RX
Oct  7 21:41:21 dexter kernel: [93028.897803] Registered led device: iwl-phy0:TX
Oct  7 21:41:21 dexter kernel: [93028.939734] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct  7 21:41:23 dexter kernel: [93030.117931] wlan0: authenticate with AP 00:1b:2f:6c:11:c0
Oct  7 21:41:23 dexter kernel: [93030.117968] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Oct  7 21:41:23 dexter kernel: [93030.120865] wlan0: authenticated
Oct  7 21:41:23 dexter kernel: [93030.120876] wlan0: associate with AP 00:1b:2f:6c:11:c0
Oct  7 21:41:23 dexter kernel: [93030.120883] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
Oct  7 21:41:23 dexter kernel: [93030.139492] wlan0: authenticate with AP 00:1b:2f:6c:11:c0
Oct  7 21:41:23 dexter kernel: [93030.148043] wlan0: authenticate with AP 00:1b:2f:6c:11:c0
Oct  7 21:41:23 dexter kernel: [93030.148080] wlan0: authenticated
Oct  7 21:41:23 dexter kernel: [93030.148086] wlan0: associate with AP 00:1b:2f:6c:11:c0
Oct  7 21:41:23 dexter kernel: [93030.152414] wlan0: RX AssocResp from 00:1b:2f:6c:11:c0 (capab=0x431 status=0 aid=4)
Oct  7 21:41:23 dexter kernel: [93030.152419] wlan0: associated
Oct  7 21:41:23 dexter kernel: [93030.180857] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct  7 21:41:23 dexter avahi-daemon[3172]: Joining mDNS multicast group on interface wlan0.IPv4 with address 74.1.46.173.
Oct  7 21:41:23 dexter avahi-daemon[3172]: New relevant interface wlan0.IPv4 for mDNS.
Oct  7 21:41:23 dexter avahi-daemon[3172]: Registering new address record for 74.1.46.173 on wlan0.IPv4.
Oct  7 21:41:23 dexter avahi-daemon[3172]: Withdrawing address record for 74.1.46.173 on wlan0.
Oct  7 21:41:23 dexter avahi-daemon[3172]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 74.1.46.173.
Oct  7 21:41:23 dexter avahi-daemon[3172]: Interface wlan0.IPv4 no longer relevant for mDNS.
Oct  7 21:41:23 dexter avahi-daemon[3172]: Joining mDNS multicast group on interface wlan0.IPv4 with address 74.1.46.173.
Oct  7 21:41:23 dexter avahi-daemon[3172]: New relevant interface wlan0.IPv4 for mDNS.
Oct  7 21:41:23 dexter avahi-daemon[3172]: Registering new address record for 74.1.46.173 on wlan0.IPv4.
Oct  7 21:41:24 dexter avahi-daemon[3172]: Registering new address record for fe80::213:e8ff:fef2:904d on wlan0.*.
Oct  7 21:41:33 dexter kernel: [93040.568093] wlan0: no IPv6 routers present
Oct  7 21:41:56 dexter kernel: [93062.713628] iwlagn: Microcode SW error detected.  Restarting 0x2000000.
Oct  7 21:41:57 dexter kernel: [93064.113975] iwlagn: Can't stop Rx DMA.
Oct  7 21:41:57 dexter kernel: [93064.114267] iwlagn: MAC is in deep sleep!
Oct  7 21:42:01 dexter kernel: [93068.176253] wlan0: No ProbeResp from current AP 00:1b:2f:6c:11:c0 - assume out of range
Oct  7 21:42:01 dexter kernel: [93068.188854] mac80211-phy0: failed to remove key (0, 00:1b:2f:6c:11:c0) from hardware (-22)
Oct  7 21:42:08 dexter kernel: [93075.317795] iwlagn/1: page allocation failure. order:4, mode:0x40d0
Oct  7 21:42:08 dexter kernel: [93075.317803] Pid: 1624, comm: iwlagn/1 Not tainted 2.6.28-15-generic #52-Ubuntu
Oct  7 21:42:08 dexter kernel: [93075.317808] Call Trace:
Oct  7 21:42:08 dexter kernel: [93075.317822]  [<ffffffff802b6e1e>] __alloc_pages_internal+0x3ee/0x500
Oct  7 21:42:08 dexter kernel: [93075.317856]  [<ffffffffa0187437>] ? iwl_tx_queue_init+0x57/0x180 [iwlcore]
Oct  7 21:42:08 dexter kernel: [93075.317865]  [<ffffffff802b6fae>] __get_free_pages+0x1e/0x60
Oct  7 21:42:08 dexter kernel: [93075.317883]  [<ffffffffa0185819>] iwl_tx_queue_alloc+0x39/0x1a0 [iwlcore]
Oct  7 21:42:08 dexter kernel: [93075.317901]  [<ffffffffa01874a8>] iwl_tx_queue_init+0xc8/0x180 [iwlcore]
Oct  7 21:42:08 dexter kernel: [93075.317919]  [<ffffffffa0187879>] iwl_txq_ctx_reset+0x189/0x1e0 [iwlcore]
Oct  7 21:42:08 dexter kernel: [93075.317939]  [<ffffffffa0180f5b>] iwl_hw_nic_init+0xfb/0x160 [iwlcore]
Oct  7 21:42:08 dexter kernel: [93075.317956]  [<ffffffffa01a13fb>] __iwl4965_up+0xbb/0x2f0 [iwlagn]
Oct  7 21:42:08 dexter kernel: [93075.317971]  [<ffffffffa01a1630>] ? iwl4965_bg_up+0x0/0x60 [iwlagn]
Oct  7 21:42:08 dexter kernel: [93075.317985]  [<ffffffffa01a1669>] iwl4965_bg_up+0x39/0x60 [iwlagn]
Oct  7 21:42:08 dexter kernel: [93075.317993]  [<ffffffff802644aa>] run_workqueue+0xba/0x190
Oct  7 21:42:08 dexter kernel: [93075.318000]  [<ffffffff80264787>] worker_thread+0xa7/0x120
Oct  7 21:42:08 dexter kernel: [93075.318007]  [<ffffffff80268ae0>] ? autoremove_wake_function+0x0/0x40
Oct  7 21:42:08 dexter kernel: [93075.318014]  [<ffffffff802646e0>] ? worker_thread+0x0/0x120
Oct  7 21:42:08 dexter kernel: [93075.318021]  [<ffffffff80268679>] kthread+0x49/0x90
Oct  7 21:42:08 dexter kernel: [93075.318028]  [<ffffffff80213979>] child_rip+0xa/0x11
Oct  7 21:42:08 dexter kernel: [93075.318035]  [<ffffffff80268630>] ? kthread+0x0/0x90
Oct  7 21:42:08 dexter kernel: [93075.318041]  [<ffffffff8021396f>] ? child_rip+0x0/0x11
Oct  7 21:42:08 dexter kernel: [93075.318045] Mem-Info:
Oct  7 21:42:08 dexter kernel: [93075.318048] DMA per-cpu:
Oct  7 21:42:08 dexter kernel: [93075.318053] CPU    0: hi:    0, btch:   1 usd:   0
Oct  7 21:42:08 dexter kernel: [93075.318057] CPU    1: hi:    0, btch:   1 usd:   0
Oct  7 21:42:08 dexter kernel: [93075.318060] DMA32 per-cpu:
Oct  7 21:42:08 dexter kernel: [93075.318064] CPU    0: hi:  186, btch:  31 usd:   0
Oct  7 21:42:08 dexter kernel: [93075.318068] CPU    1: hi:  186, btch:  31 usd:   0
Oct  7 21:42:08 dexter kernel: [93075.318075] Active_anon:96388 active_file:5539 inactive_anon:99715
Oct  7 21:42:08 dexter kernel: [93075.318077]  inactive_file:14413 unevictable:1069 dirty:104 writeback:10 unstable:0
Oct  7 21:42:08 dexter kernel: [93075.318080]  free:4121 slab:11550 mapped:13043 pagetables:6395 bounce:0
Oct  7 21:42:08 dexter kernel: [93075.318088] DMA free:3948kB min:20kB low:24kB high:28kB active_anon:816kB inactive_anon:988kB active_file:760kB inactive_file:72kB unevictable:0kB present:5548kB pages_scanned:0 all_unreclaimable? no
Oct  7 21:42:08 dexter kernel: [93075.318095] lowmem_reserve[]: 0 985 985 985
Oct  7 21:42:08 dexter kernel: [93075.318108] DMA32 free:12536kB min:4004kB low:5004kB high:6004kB active_anon:384736kB inactive_anon:397872kB active_file:21396kB inactive_file:57580kB unevictable:4276kB present:1008800kB pages_scanned:0 all_unreclaimable? no
Oct  7 21:42:08 dexter kernel: [93075.318115] lowmem_reserve[]: 0 0 0 0
Oct  7 21:42:08 dexter kernel: [93075.318123] DMA: 5*4kB 1*8kB 1*16kB 0*32kB 1*64kB 0*128kB 1*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 3948kB
Oct  7 21:42:08 dexter kernel: [93075.318144] DMA32: 2668*4kB 162*8kB 11*16kB 1*32kB 1*64kB 3*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 12624kB
Oct  7 21:42:08 dexter kernel: [93075.318164] 151684 total pagecache pages
Oct  7 21:42:08 dexter kernel: [93075.318168] 116013 pages in swap cache
Oct  7 21:42:08 dexter kernel: [93075.318172] Swap cache stats: add 761155, delete 645142, find 7015126/7140762
Oct  7 21:42:08 dexter kernel: [93075.318176] Free swap  = 3107316kB
Oct  7 21:42:08 dexter kernel: [93075.318179] Total swap = 4000176kB
Oct  7 21:42:08 dexter kernel: [93075.328165] 259792 pages RAM
Oct  7 21:42:08 dexter kernel: [93075.328170] 9012 pages reserved
Oct  7 21:42:08 dexter kernel: [93075.328173] 162470 pages shared
Oct  7 21:42:08 dexter kernel: [93075.328177] 116983 pages non-shared
Oct  7 21:42:08 dexter kernel: [93075.328182] iwlagn: kmalloc for auxiliary BD structures failed
Oct  7 21:42:08 dexter kernel: [93075.328271] iwlagn: Tx 13 queue init failed
Oct  7 21:42:08 dexter kernel: [93075.329269] iwlagn: Unable to init nic
Oct  7 21:42:17 dexter dhclient: Internet Systems Consortium DHCP Client V3.1.1
Oct  7 21:42:17 dexter dhclient: Copyright 2004-2008 Internet Systems Consortium.
Oct  7 21:42:17 dexter dhclient: All rights reserved.
Oct  7 21:42:17 dexter dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Oct  7 21:42:17 dexter dhclient: 
Oct  7 21:42:17 dexter dhclient: wmaster0: unknown hardware address type 801
Oct  7 21:42:17 dexter avahi-daemon[3172]: Interface wlan0.IPv4 no longer relevant for mDNS.
Oct  7 21:42:17 dexter avahi-daemon[3172]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 74.1.46.173.
Oct  7 21:42:17 dexter avahi-daemon[3172]: Withdrawing address record for fe80::213:e8ff:fef2:904d on wlan0.
Oct  7 21:42:17 dexter avahi-daemon[3172]: Withdrawing address record for 74.1.46.173 on wlan0.
Oct  7 21:42:17 dexter dhclient: wmaster0: unknown hardware address type 801
Oct  7 21:42:17 dexter dhclient: Bind socket to interface: No such device
Oct  7 21:42:17 dexter dhclient: Internet Systems Consortium DHCP Client V3.1.1
Oct  7 21:42:17 dexter dhclient: Copyright 2004-2008 Internet Systems Consortium.
Oct  7 21:42:17 dexter dhclient: All rights reserved.
Oct  7 21:42:17 dexter dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Oct  7 21:42:17 dexter dhclient: 
Oct  7 21:42:17 dexter dhclient: wmaster0: unknown hardware address type 801
Oct  7 21:42:17 dexter dhclient: wmaster0: unknown hardware address type 801
Oct  7 21:42:17 dexter dhclient: Bind socket to interface: No such device
Oct  7 21:42:30 dexter kernel: [93097.675336] ifconfig: page allocation failure. order:4, mode:0x40d0
Oct  7 21:42:30 dexter kernel: [93097.675345] Pid: 15388, comm: ifconfig Not tainted 2.6.28-15-generic #52-Ubuntu
Oct  7 21:42:30 dexter kernel: [93097.675350] Call Trace:
Oct  7 21:42:30 dexter kernel: [93097.675365]  [<ffffffff802b6e1e>] __alloc_pages_internal+0x3ee/0x500
Oct  7 21:42:30 dexter kernel: [93097.675399]  [<ffffffffa0187437>] ? iwl_tx_queue_init+0x57/0x180 [iwlcore]
Oct  7 21:42:30 dexter kernel: [93097.675408]  [<ffffffff802b6fae>] __get_free_pages+0x1e/0x60
Oct  7 21:42:30 dexter kernel: [93097.675426]  [<ffffffffa0185819>] iwl_tx_queue_alloc+0x39/0x1a0 [iwlcore]
Oct  7 21:42:30 dexter kernel: [93097.675444]  [<ffffffffa01874a8>] iwl_tx_queue_init+0xc8/0x180 [iwlcore]
Oct  7 21:42:30 dexter kernel: [93097.675463]  [<ffffffffa0187879>] iwl_txq_ctx_reset+0x189/0x1e0 [iwlcore]
Oct  7 21:42:30 dexter kernel: [93097.675482]  [<ffffffffa0180f5b>] iwl_hw_nic_init+0xfb/0x160 [iwlcore]
Oct  7 21:42:30 dexter kernel: [93097.675500]  [<ffffffffa01a13fb>] __iwl4965_up+0xbb/0x2f0 [iwlagn]
Oct  7 21:42:30 dexter kernel: [93097.675514]  [<ffffffffa01a19bf>] iwl4965_mac_start+0x6f/0x220 [iwlagn]
Oct  7 21:42:30 dexter kernel: [93097.675524]  [<ffffffff80603903>] ? arp_ifdown+0x13/0x20
Oct  7 21:42:30 dexter kernel: [93097.675531]  [<ffffffff8060ee47>] ? fib_disable_ip+0x37/0x40
Oct  7 21:42:30 dexter kernel: [93097.675539]  [<ffffffff8022f669>] ? default_spin_lock_flags+0x9/0x10
Oct  7 21:42:30 dexter kernel: [93097.675571]  [<ffffffffa01364da>] ieee80211_open+0x2fa/0x860 [mac80211]
Oct  7 21:42:30 dexter kernel: [93097.675581]  [<ffffffff8026dbd3>] ? __blocking_notifier_call_chain+0x63/0x80
Oct  7 21:42:30 dexter kernel: [93097.675589]  [<ffffffff805b3e3a>] dev_open+0xaa/0xf0
Oct  7 21:42:30 dexter kernel: [93097.675595]  [<ffffffff805b3506>] dev_change_flags+0x96/0x1e0
Oct  7 21:42:30 dexter kernel: [93097.675603]  [<ffffffff8060856c>] devinet_ioctl+0x62c/0x6b0
Oct  7 21:42:30 dexter kernel: [93097.675610]  [<ffffffff806092d4>] inet_ioctl+0x94/0xc0
Oct  7 21:42:30 dexter kernel: [93097.675618]  [<ffffffff805a1f86>] sock_ioctl+0x66/0x270
Oct  7 21:42:30 dexter kernel: [93097.675626]  [<ffffffff802f65e1>] vfs_ioctl+0x31/0xa0
Oct  7 21:42:30 dexter kernel: [93097.675633]  [<ffffffff802f6995>] do_vfs_ioctl+0x75/0x230
Oct  7 21:42:30 dexter kernel: [93097.675640]  [<ffffffff802f6be9>] sys_ioctl+0x99/0xa0
Oct  7 21:42:30 dexter kernel: [93097.675647]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
Oct  7 21:42:30 dexter kernel: [93097.675652] Mem-Info:
Oct  7 21:42:30 dexter kernel: [93097.675656] DMA per-cpu:
Oct  7 21:42:30 dexter kernel: [93097.675660] CPU    0: hi:    0, btch:   1 usd:   0
Oct  7 21:42:30 dexter kernel: [93097.675664] CPU    1: hi:    0, btch:   1 usd:   0
Oct  7 21:42:30 dexter kernel: [93097.675668] DMA32 per-cpu:
Oct  7 21:42:30 dexter kernel: [93097.675671] CPU    0: hi:  186, btch:  31 usd:   0
Oct  7 21:42:30 dexter kernel: [93097.675675] CPU    1: hi:  186, btch:  31 usd:   0
Oct  7 21:42:30 dexter kernel: [93097.675682] Active_anon:98348 active_file:6498 inactive_anon:99096
Oct  7 21:42:30 dexter kernel: [93097.675685]  inactive_file:13142 unevictable:1069 dirty:0 writeback:16 unstable:0
Oct  7 21:42:30 dexter kernel: [93097.675687]  free:3512 slab:11286 mapped:13051 pagetables:6390 bounce:0
Oct  7 21:42:30 dexter kernel: [93097.675695] DMA free:3948kB min:20kB low:24kB high:28kB active_anon:816kB inactive_anon:988kB active_file:760kB inactive_file:72kB unevictable:0kB present:5548kB pages_scanned:0 all_unreclaimable? no
Oct  7 21:42:30 dexter kernel: [93097.675702] lowmem_reserve[]: 0 985 985 985
Oct  7 21:42:30 dexter kernel: [93097.675715] DMA32 free:10100kB min:4004kB low:5004kB high:6004kB active_anon:392576kB inactive_anon:395396kB active_file:25232kB inactive_file:52496kB unevictable:4276kB present:1008800kB pages_scanned:0 all_unreclaimable? no
Oct  7 21:42:30 dexter kernel: [93097.675722] lowmem_reserve[]: 0 0 0 0
Oct  7 21:42:30 dexter kernel: [93097.675731] DMA: 5*4kB 1*8kB 1*16kB 0*32kB 1*64kB 0*128kB 1*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 3948kB
Oct  7 21:42:30 dexter kernel: [93097.675752] DMA32: 2019*4kB 14*8kB 41*16kB 8*32kB 6*64kB 5*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 10124kB
Oct  7 21:42:30 dexter kernel: [93097.675772] 152972 total pagecache pages
Oct  7 21:42:30 dexter kernel: [93097.675776] 117629 pages in swap cache
Oct  7 21:42:30 dexter kernel: [93097.675780] Swap cache stats: add 767068, delete 649439, find 7017764/7144906
Oct  7 21:42:30 dexter kernel: [93097.675784] Free swap  = 3106124kB
Oct  7 21:42:30 dexter kernel: [93097.675787] Total swap = 4000176kB
Oct  7 21:42:30 dexter kernel: [93097.686008] 259792 pages RAM
Oct  7 21:42:30 dexter kernel: [93097.686013] 9012 pages reserved
Oct  7 21:42:30 dexter kernel: [93097.686016] 163695 pages shared
Oct  7 21:42:30 dexter kernel: [93097.686019] 116549 pages non-shared
Oct  7 21:42:30 dexter kernel: [93097.686023] iwlagn: kmalloc for auxiliary BD structures failed
Oct  7 21:42:30 dexter kernel: [93097.686114] iwlagn: Tx 6 queue init failed
Oct  7 21:42:30 dexter kernel: [93097.686562] iwlagn: Unable to init nic
Oct  7 21:43:01 dexter kernel: [93128.518119] ------------[ cut here ]------------
Oct  7 21:43:01 dexter kernel: [93128.518127] WARNING: at /build/buildd/linux-2.6.28/drivers/net/wireless/iwlwifi/iwl-tx.c:1204 iwl_tx_cmd_complete+0x13c/0x140 [iwlcore]()
Oct  7 21:43:01 dexter kernel: [93128.518133] wrong command queue 0, command id 0x6F
Oct  7 21:43:01 dexter kernel: [93128.518136] Modules linked in: aes_x86_64 aes_generic i915 drm binfmt_misc ppdev bridge stp bnep input_polldev coretemp sbp2 lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss arc4 snd_seq_midi snd_rawmidi ecb snd_seq_midi_event snd_seq snd_timer snd_seq_device iwlagn iwlcore led_class psmouse mac80211 video snd soundcore ricoh_mmc compal_laptop sdhci_pci sdhci iTCO_wdt output intel_agp cfg80211 serio_raw snd_page_alloc pcspkr iTCO_vendor_support joydev usbhid ohci1394 ieee1394 tg3 fbcon tileblit font bitblit softcursor
Oct  7 21:43:01 dexter kernel: [93128.518227] Pid: 0, comm: swapper Not tainted 2.6.28-15-generic #52-Ubuntu
Oct  7 21:43:01 dexter kernel: [93128.518231] Call Trace:
Oct  7 21:43:01 dexter kernel: [93128.518235]  <IRQ>  [<ffffffff80250ad7>] warn_slowpath+0xb7/0xf0
Oct  7 21:43:01 dexter kernel: [93128.518257]  [<ffffffff80417b6a>] ? __next_cpu+0x1a/0x30
Oct  7 21:43:01 dexter kernel: [93128.518266]  [<ffffffff80242502>] ? enqueue_entity+0x122/0x2b0
Oct  7 21:43:01 dexter kernel: [93128.518275]  [<ffffffff80270bb9>] ? getnstimeofday+0x59/0xe0
Oct  7 21:43:01 dexter kernel: [93128.518282]  [<ffffffff8026c819>] ? ktime_get_ts+0x59/0x60
Oct  7 21:43:01 dexter kernel: [93128.518289]  [<ffffffff8041c9f8>] ? rb_insert_color+0x98/0x140
Oct  7 21:43:01 dexter kernel: [93128.518309]  [<ffffffffa018654c>] iwl_tx_cmd_complete+0x13c/0x140 [iwlcore]
Oct  7 21:43:01 dexter kernel: [93128.518327]  [<ffffffffa019e382>] iwl_rx_handle+0xf2/0x2d0 [iwlagn]
Oct  7 21:43:01 dexter kernel: [93128.518334]  [<ffffffff8023e6d0>] ? enqueue_task+0x50/0x60
Oct  7 21:43:01 dexter kernel: [93128.518349]  [<ffffffffa01a058e>] iwl4965_irq_tasklet+0x22e/0x360 [iwlagn]
Oct  7 21:43:01 dexter kernel: [93128.518357]  [<ffffffff80256536>] tasklet_action+0x86/0x110
Oct  7 21:43:01 dexter kernel: [93128.518363]  [<ffffffff80256c4c>] __do_softirq+0x9c/0x170
Oct  7 21:43:01 dexter kernel: [93128.518371]  [<ffffffff80213d8c>] call_softirq+0x1c/0x30
Oct  7 21:43:01 dexter kernel: [93128.518377]  [<ffffffff80214ffd>] do_softirq+0x5d/0xa0
Oct  7 21:43:01 dexter kernel: [93128.518383]  [<ffffffff802569cd>] irq_exit+0x8d/0xa0
Oct  7 21:43:01 dexter kernel: [93128.518389]  [<ffffffff802152c5>] do_IRQ+0xc5/0x110
Oct  7 21:43:01 dexter kernel: [93128.518396]  [<ffffffff80212bf3>] ret_from_intr+0x0/0x29
Oct  7 21:43:01 dexter kernel: [93128.518399]  <EOI>  [<ffffffff80475a09>] ? acpi_idle_enter_bm+0x28a/0x2da
Oct  7 21:43:01 dexter kernel: [93128.518412]  [<ffffffff80475a01>] ? acpi_idle_enter_bm+0x282/0x2da
Oct  7 21:43:01 dexter kernel: [93128.518422]  [<ffffffff8058a8b5>] ? cpuidle_idle_call+0xa5/0x100
Oct  7 21:43:01 dexter kernel: [93128.518430]  [<ffffffff80210e85>] ? cpu_idle+0x65/0xc0
Oct  7 21:43:01 dexter kernel: [93128.518438]  [<ffffffff80696333>] ? start_secondary+0x9e/0xcb
Oct  7 21:43:01 dexter kernel: [93128.518443] ---[ end trace c2955ccf9c21184b ]---
Oct  7 21:43:05 dexter kernel: [93132.344166] iwlagn: START_ALIVE timeout after 4000ms.
Oct  7 21:43:15 dexter kernel: [93142.193176] iwlagn: START_ALIVE timeout after 4000ms.
Oct  7 21:44:01 dexter kernel: [93188.284142] iwlagn: START_ALIVE timeout after 4000ms.
Oct  7 21:44:05 dexter kernel: [93192.808079] iwlagn: START_ALIVE timeout after 4000ms.

```

---

### Post by DantePasquale on 2009-10-31
I ended up downloading the latest driver from here:

[http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-4965-ucode-228.61.2.24.tgz]("http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-4965-ucode-228.61.2.24.tgz")

Then unzip the file and copy into /lib/firmware (backup the installed version so that you have it in case this causes problems). Rebooted and thus far, with pounding the network with downloads and uploads I haven't seen the firmware issue with the 4695 firmware.

---

