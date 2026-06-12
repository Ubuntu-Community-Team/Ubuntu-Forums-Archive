---
title: "AE1000, must reboot to connect..."
date: 2013-02-23
forum: Networking &amp; Wireless
---

### Post by THXTom on 2013-02-23
Hi All,

Trying out this WiFi adapter. Works fine all day but come back the next day cant connect. Keeps asking for SSID key. I type in but wont connect.

So, reboot and its fine then.

Any way to fix this? running 12.04LTS, 3.2.0-37 generic

l```
susb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 13b1:002f Linksys AE1000 v1 802.11n [Ralink RT3572
```]

```
[   33.215142] cfg80211: 5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   33.215146] cfg80211: Updating information on frequency 5540 MHz for a 20 MHz width channel with regulatory rule:
[   33.215150] cfg80211: 5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   33.215154] cfg80211: Updating information on frequency 5550 MHz for a 20 MHz width channel with regulatory rule:
[   33.215158] cfg80211: 5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   33.215162] cfg80211: Updating information on frequency 5560 MHz for a 20 MHz width channel with regulatory rule:
[   33.215166] cfg80211: 5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   33.215170] cfg80211: Updating information on frequency 5580 MHz for a 20 MHz width channel with regulatory rule:
[   33.215174] cfg80211: 5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   33.215178] cfg80211: Updating information on frequency 5590 MHz for a 20 MHz width channel with regulatory rule:
[   33.215182] cfg80211: 5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   33.215185] cfg80211: Disabling freq 5600 MHz
[   33.215188] cfg80211: Disabling freq 5620 MHz
[   33.215191] cfg80211: Disabling freq 5630 MHz
[   33.215194] cfg80211: Disabling freq 5640 MHz
[   33.215197] cfg80211: Updating information on frequency 5660 MHz for a 20 MHz width channel with regulatory rule:
[   33.215201] cfg80211: 5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   33.215205] cfg80211: Updating information on frequency 5670 MHz for a 20 MHz width channel with regulatory rule:
[   33.215209] cfg80211: 5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   33.215213] cfg80211: Updating information on frequency 5680 MHz for a 20 MHz width channel with regulatory rule:
[   33.215217] cfg80211: 5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   33.215221] cfg80211: Updating information on frequency 5700 MHz for a 20 MHz width channel with regulatory rule:
[   33.215225] cfg80211: 5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   33.215229] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[   33.215233] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   33.215237] cfg80211: Updating information on frequency 5755 MHz for a 20 MHz width channel with regulatory rule:
[   33.215241] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   33.215245] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[   33.215249] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   33.215253] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[   33.215258] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   33.215261] cfg80211: Updating information on frequency 5795 MHz for a 20 MHz width channel with regulatory rule:
[   33.215266] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   33.215269] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[   33.215274] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   33.215277] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[   33.215282] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   33.215285] cfg80211: Disabling freq 5835 MHz
[   33.215287] cfg80211: Disabling freq 5845 MHz
[   33.215290] cfg80211: Disabling freq 5855 MHz
[   33.215293] cfg80211: Disabling freq 5865 MHz
[   33.215304] cfg80211: Regulatory domain changed to country: US
[   33.215307] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   33.215311] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   33.215315] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   33.215319] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   33.215323] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   33.215327] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   33.215331] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   34.584591] wlan1: IPv6 duplicate address fe80::9afc:11ff:fecc:edb8 detected!
[   48.157041] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[ 1414.590920] wlan1: direct probe to 30:85:a9:6a:3b:19 (try 1/3)
[ 1414.591556] wlan1: direct probe responded
[ 1414.604059] wlan1: authenticate with 30:85:a9:6a:3b:19 (try 1)
[ 1414.604554] wlan1: authenticated
[ 1414.687048] wlan1: associate with 30:85:a9:6a:3b:19 (try 1)
[ 1414.687808] wlan1: RX ReassocResp from 30:85:a9:6a:3b:19 (capab=0x11 status=0 aid=2)
[ 1414.687814] wlan1: associated
[ 1414.687819] wlan1: No basic rates in AssocResp. Using min supported rate instead.
[ 1534.814943] wlan1: direct probe to 30:85:a9:6a:3b:18 (try 1/3)
[ 1535.012022] wlan1: direct probe to 30:85:a9:6a:3b:18 (try 2/3)
[ 1535.212030] wlan1: direct probe to 30:85:a9:6a:3b:18 (try 3/3)
[ 1535.288036] ------------[ cut here ]------------
[ 1535.288070] WARNING: at /build/buildd/linux-3.2.0/include/net/mac80211.h:3570 rate_control_send_low+0x24b/0x260 [mac80211]()
[ 1535.288075] Hardware name: Precision WorkStation 380    
[ 1535.288078] Modules linked in: vboxnetadp(O) vboxnetflt(O) vboxdrv(O) dm_crypt rfcomm bnep bluetooth snd_hda_codec_idt arc4 snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi rt2800usb rt2800lib crc_ccitt rt2x00usb rt2x00lib mac80211 snd_rawmidi snd_seq_midi_event snd_seq cfg80211 snd_timer snd_seq_device ppdev psmouse snd serio_raw dcdbas dm_multipath soundcore snd_page_alloc parport_pc mac_hid lp parport binfmt_misc dm_raid45 xor dm_mirror dm_region_hash dm_log aic79xx scsi_transport_spi radeon floppy ttm drm_kms_helper drm i2c_algo_bit tg3
[ 1535.288149] Pid: 46, comm: kworker/u:3 Tainted: G           O 3.2.0-37-generic #58-Ubuntu
[ 1535.288152] Call Trace:
[ 1535.288162]  [<c15611ec>] ? printk+0x2d/0x2f
[ 1535.288171]  [<c104afe2>] warn_slowpath_common+0x72/0xa0
[ 1535.288192]  [<f861818b>] ? rate_control_send_low+0x24b/0x260 [mac80211]
[ 1535.288212]  [<f861818b>] ? rate_control_send_low+0x24b/0x260 [mac80211]
[ 1535.288218]  [<c104b032>] warn_slowpath_null+0x22/0x30
[ 1535.288238]  [<f861818b>] rate_control_send_low+0x24b/0x260 [mac80211]
[ 1535.288264]  [<f86455cd>] minstrel_ht_get_rate+0x2d/0x210 [mac80211]
[ 1535.288273]  [<f81d3c46>] ? rt2x00queue_for_each_entry+0xb6/0x130 [rt2x00lib]
[ 1535.288295]  [<f861864e>] rate_control_get_rate+0x9e/0x1a0 [mac80211]
[ 1535.288317]  [<f86214b0>] ieee80211_tx_h_rate_ctrl+0x160/0x480 [mac80211]
[ 1535.288325]  [<c129a8c8>] ? cpumask_next_and+0x28/0x40
[ 1535.288331]  [<c103ed0e>] ? find_busiest_group+0x14e/0xb10
[ 1535.288354]  [<f86232b7>] invoke_tx_handlers+0x197/0x230 [mac80211]
[ 1535.288376]  [<f862347b>] ieee80211_tx+0x4b/0xb0 [mac80211]
[ 1535.288398]  [<f862357a>] ieee80211_xmit+0x9a/0xf0 [mac80211]
[ 1535.288420]  [<f862433b>] ieee80211_tx_skb+0x4b/0x60 [mac80211]
[ 1535.288443]  [<f86278c0>] ieee80211_send_probe_req+0x50/0x70 [mac80211]
[ 1535.288462]  [<f860ff12>] ieee80211_mgd_probe_ap_send+0xe2/0x100 [mac80211]
[ 1535.288482]  [<f86128d4>] ieee80211_sta_work+0x94/0x190 [mac80211]
[ 1535.288488]  [<c1001ce7>] ? __switch_to+0x97/0x1f0
[ 1535.288493]  [<c1034bf5>] ? pick_next_entity+0x65/0xc0
[ 1535.288500]  [<c1027568>] ? default_spin_lock_flags+0x8/0x10
[ 1535.288506]  [<c157641d>] ? _raw_spin_lock_irqsave+0x2d/0x40
[ 1535.288526]  [<f8616388>] ieee80211_iface_work+0x278/0x310 [mac80211]
[ 1535.288533]  [<c1065111>] process_one_work+0x101/0x3a0
[ 1535.288539]  [<c1576a49>] ? apic_timer_interrupt+0x31/0x38
[ 1535.288559]  [<f8616110>] ? ieee80211_teardown_sdata+0xc0/0xc0 [mac80211]
[ 1535.288566]  [<c1065be4>] worker_thread+0x124/0x2d0
[ 1535.288571]  [<c1065ac0>] ? manage_workers.isra.29+0x110/0x110
[ 1535.288577]  [<c1069a3d>] kthread+0x6d/0x80
[ 1535.288582]  [<c10699d0>] ? flush_kthread_worker+0x80/0x80
[ 1535.288588]  [<c157dafe>] kernel_thread_helper+0x6/0x10
[ 1535.288592] ---[ end trace d13c21139bdf11b0 ]---
[ 1535.412027] wlan1: direct probe to 30:85:a9:6a:3b:18 timed out
[ 1545.725698] wlan1: deauthenticating from 30:85:a9:6a:3b:19 by local choice (reason=2)
[ 1545.756465] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1545.756474] cfg80211: Restoring regulatory settings
[ 1545.756482] cfg80211: Calling CRDA to update world regulatory domain
[ 1545.760444] wlan1: authenticate with 30:85:a9:6a:3b:19 (try 1)
[ 1545.761514] wlan1: authenticated
[ 1545.780194] wlan1: associate with 30:85:a9:6a:3b:19 (try 1)
[ 1545.780956] wlan1: RX ReassocResp from 30:85:a9:6a:3b:19 (capab=0x11 status=0 aid=2)
[ 1545.780961] wlan1: associated
[ 1545.780967] wlan1: No basic rates in AssocResp. Using min supported rate instead.
[ 1545.816518] cfg80211: Pending regulatory request, waiting for it to be processed...
[ 1545.945045] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.945052] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.945056] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.945061] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.945064] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.945069] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.945072] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.945077] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.945080] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.945084] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.945088] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.945092] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.945096] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.945100] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.945104] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.945108] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.945111] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.945116] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.945119] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.945124] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.945127] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.945131] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.945135] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.945139] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1545.945143] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.945147] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1545.945151] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.945155] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1545.945159] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.945163] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.945167] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.945171] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.945175] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.945179] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.945183] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.945187] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.945191] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.945195] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.945199] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.945203] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.945206] cfg80211: Disabling freq 5260 MHz
[ 1545.945209] cfg80211: Disabling freq 5270 MHz
[ 1545.945212] cfg80211: Disabling freq 5280 MHz
[ 1545.945215] cfg80211: Disabling freq 5300 MHz
[ 1545.945217] cfg80211: Disabling freq 5310 MHz
[ 1545.945220] cfg80211: Disabling freq 5320 MHz
[ 1545.945223] cfg80211: Disabling freq 5500 MHz
[ 1545.945226] cfg80211: Disabling freq 5510 MHz
[ 1545.945229] cfg80211: Disabling freq 5520 MHz
[ 1545.945231] cfg80211: Disabling freq 5540 MHz
[ 1545.945234] cfg80211: Disabling freq 5550 MHz
[ 1545.945237] cfg80211: Disabling freq 5560 MHz
[ 1545.945240] cfg80211: Disabling freq 5580 MHz
[ 1545.945243] cfg80211: Disabling freq 5590 MHz
[ 1545.945245] cfg80211: Disabling freq 5600 MHz
[ 1545.945248] cfg80211: Disabling freq 5620 MHz
[ 1545.945251] cfg80211: Disabling freq 5630 MHz
[ 1545.945254] cfg80211: Disabling freq 5640 MHz
[ 1545.945257] cfg80211: Disabling freq 5660 MHz
[ 1545.945259] cfg80211: Disabling freq 5670 MHz
[ 1545.945262] cfg80211: Disabling freq 5680 MHz
[ 1545.945265] cfg80211: Disabling freq 5700 MHz
[ 1545.945268] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.945272] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.945276] cfg80211: Updating information on frequency 5755 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.945280] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.945284] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.945288] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.945292] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.945296] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.945300] cfg80211: Updating information on frequency 5795 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.945304] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.945308] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.945312] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.945316] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.945320] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.945323] cfg80211: Disabling freq 5835 MHz
[ 1545.945326] cfg80211: Disabling freq 5845 MHz
[ 1545.945329] cfg80211: Disabling freq 5855 MHz
[ 1545.945332] cfg80211: Disabling freq 5865 MHz
[ 1545.945339] cfg80211: World regulatory domain updated:
[ 1545.945342] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1545.945346] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.945350] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1545.945354] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1545.945358] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.945362] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.945379] cfg80211: Calling CRDA for country: US
[ 1545.957279] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957287] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1545.957291] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957295] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1545.957299] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957303] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1545.957306] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957311] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1545.957314] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957318] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1545.957322] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957326] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1545.957330] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957334] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1545.957337] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957342] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1545.957345] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957349] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1545.957353] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957357] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1545.957361] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957365] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1545.957368] cfg80211: Disabling freq 2467 MHz
[ 1545.957371] cfg80211: Disabling freq 2472 MHz
[ 1545.957374] cfg80211: Disabling freq 2484 MHz
[ 1545.957377] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957381] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[ 1545.957385] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957389] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[ 1545.957393] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957397] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[ 1545.957400] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957405] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[ 1545.957408] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957412] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[ 1545.957416] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957420] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[ 1545.957424] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957428] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.957431] cfg80211: Updating information on frequency 5270 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957436] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.957439] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957443] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.957447] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957451] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.957455] cfg80211: Updating information on frequency 5310 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957459] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.957462] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957467] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.957470] cfg80211: Updating information on frequency 5500 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957474] cfg80211: 5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.957478] cfg80211: Updating information on frequency 5510 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957482] cfg80211: 5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.957486] cfg80211: Updating information on frequency 5520 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957490] cfg80211: 5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.957493] cfg80211: Updating information on frequency 5540 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957498] cfg80211: 5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.957501] cfg80211: Updating information on frequency 5550 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957505] cfg80211: 5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.957509] cfg80211: Updating information on frequency 5560 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957513] cfg80211: 5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.957517] cfg80211: Updating information on frequency 5580 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957521] cfg80211: 5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.957524] cfg80211: Updating information on frequency 5590 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957529] cfg80211: 5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.957532] cfg80211: Disabling freq 5600 MHz
[ 1545.957535] cfg80211: Disabling freq 5620 MHz
[ 1545.957537] cfg80211: Disabling freq 5630 MHz
[ 1545.957540] cfg80211: Disabling freq 5640 MHz
[ 1545.957543] cfg80211: Updating information on frequency 5660 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957547] cfg80211: 5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.957551] cfg80211: Updating information on frequency 5670 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957555] cfg80211: 5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.957559] cfg80211: Updating information on frequency 5680 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957563] cfg80211: 5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.957566] cfg80211: Updating information on frequency 5700 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957571] cfg80211: 5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.957574] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957578] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[ 1545.957582] cfg80211: Updating information on frequency 5755 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957586] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[ 1545.957590] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957594] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[ 1545.957597] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957602] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[ 1545.957605] cfg80211: Updating information on frequency 5795 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957609] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[ 1545.957613] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957617] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[ 1545.957621] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[ 1545.957625] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[ 1545.957628] cfg80211: Disabling freq 5835 MHz
[ 1545.957631] cfg80211: Disabling freq 5845 MHz
[ 1545.957633] cfg80211: Disabling freq 5855 MHz
[ 1545.957636] cfg80211: Disabling freq 5865 MHz
[ 1545.957647] cfg80211: Regulatory domain changed to country: US
[ 1545.957650] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1545.957654] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1545.957658] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[ 1545.957662] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.957666] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.957670] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1545.957673] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[ 1648.433981] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
thomas@thomas-desktop:~$ 


```

Or would this help:

  	 	 	 	 	 	 		 		 		 			 				1
 			 			 				sudo apt-get 				install build-essential 				linux-headers-generic
 			 		 	 
 [Download]("http://blog.up-link.ro/files/2010_0915_RT3572_Linux_STA_v2.4.0.2.zip") the linux driver and extract the files:
 

  	 		 		 		 			 				1
 			 			 				wget 				[http://blog.up-link.ro/files/2010_0915_RT3572_Linux_STA_v2.4.0.2.zip](http://blog.up-link.ro/files/2010_0915_RT3572_Linux_STA_v2.4.0.2.zip)
 			 		 	 	 		 		 		 			 				2
 			 			 				

unzip 				2010_0915_RT3572_Linux_STA_v2.4.0.2.zip
 				
				
 				
				
 			 		 	 
 Now we're ready to build and install the driver:  	 		 		 		 			 				1
 			 			 				cd 				2010_0915_RT3572_Linux_STA_v2.4.0.2/
 			 		 	 	 		 		 		 			 				2
 			 			 				make
 			 		 	 	 		 		 		 			 				3
 			 			 				sudo make 				install
 			 		 	 	 		 		 		 			 				4
 			 			 				sudo modprobe 				rt3572sta
 			 		 	 
 

  


Thanks, in advance T

---

