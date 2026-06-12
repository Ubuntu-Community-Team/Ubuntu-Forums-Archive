---
title: "Atheros Communications Inc. Device 0036 (rev 01)"
date: 2012-12-09
forum: Networking &amp; Wireless
---

### Post by VargheseKRenny on 2012-12-09
Hi,
     I have installed ubuntu 12.04 but my wifi is not working and lan is working fine.
 

Output of command :** dmesg | grep ath9k**

```

[   11.354637] ath9k 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.354651] ath9k 0000:07:00.0: setting latency timer to 64
[   11.357559] ath9k 0000:07:00.0: Failed to initialize device
[   11.357621] ath9k 0000:07:00.0: PCI INT A disabled
[   11.357625] ath9k: probe of 0000:07:00.0 failed with error -95

```

i tried installing wireless compact driver for ath9k as mentioned in 
*[http://ubuntuforums.org/showthread.php?t=2035902&page=3](http://ubuntuforums.org/showthread.php?t=2035902&page=3)*

Output of command : **dmesg | grep -e ath -e 80211**

```

[   11.061304] cfg80211: Calling CRDA to update world regulatory domain
[   11.166226] b43: disagrees about version of symbol ieee80211_get_response_rate
[   11.166230] b43: Unknown symbol ieee80211_get_response_rate (err -22)
[   11.166276] b43: disagrees about version of symbol ieee80211_free_hw
[   11.166277] b43: Unknown symbol ieee80211_free_hw (err -22)
[   11.166285] b43: disagrees about version of symbol ieee80211_alloc_hw
[   11.166287] b43: Unknown symbol ieee80211_alloc_hw (err -22)
[   11.166295] b43: disagrees about version of symbol ieee80211_register_hw
[   11.166296] b43: Unknown symbol ieee80211_register_hw (err -22)
[   11.166304] b43: disagrees about version of symbol __ieee80211_get_radio_led_name
[   11.166306] b43: Unknown symbol __ieee80211_get_radio_led_name (err -22)
[   11.166309] b43: disagrees about version of symbol ieee80211_generic_frame_duration
[   11.166311] b43: Unknown symbol ieee80211_generic_frame_duration (err -22)
[   11.166316] b43: disagrees about version of symbol ieee80211_wake_queue
[   11.166318] b43: Unknown symbol ieee80211_wake_queue (err -22)
[   11.166328] b43: disagrees about version of symbol __ieee80211_get_tx_led_name
[   11.166330] b43: Unknown symbol __ieee80211_get_tx_led_name (err -22)
[   11.166363] b43: disagrees about version of symbol __ieee80211_get_rx_led_name
[   11.166365] b43: Unknown symbol __ieee80211_get_rx_led_name (err -22)
[   11.166380] b43: disagrees about version of symbol ieee80211_queue_delayed_work
[   11.166381] b43: Unknown symbol ieee80211_queue_delayed_work (err -22)
[   11.166386] b43: disagrees about version of symbol ieee80211_ctstoself_get
[   11.166388] b43: Unknown symbol ieee80211_ctstoself_get (err -22)
[   11.166399] b43: disagrees about version of symbol ieee80211_rx
[   11.166401] b43: Unknown symbol ieee80211_rx (err -22)
[   11.166411] b43: disagrees about version of symbol ieee80211_wake_queues
[   11.166412] b43: Unknown symbol ieee80211_wake_queues (err -22)
[   11.166427] b43: disagrees about version of symbol ieee80211_tx_status
[   11.166429] b43: Unknown symbol ieee80211_tx_status (err -22)
[   11.166432] b43: disagrees about version of symbol ieee80211_stop_queue
[   11.166434] b43: Unknown symbol ieee80211_stop_queue (err -22)
[   11.166444] b43: disagrees about version of symbol __ieee80211_get_assoc_led_name
[   11.166446] b43: Unknown symbol __ieee80211_get_assoc_led_name (err -22)
[   11.166461] b43: disagrees about version of symbol ieee80211_unregister_hw
[   11.166463] b43: Unknown symbol ieee80211_unregister_hw (err -22)
[   11.166467] b43: disagrees about version of symbol ieee80211_beacon_get_tim
[   11.166469] b43: Unknown symbol ieee80211_beacon_get_tim (err -22)
[   11.166477] b43: disagrees about version of symbol ieee80211_rts_get
[   11.166478] b43: Unknown symbol ieee80211_rts_get (err -22)
[   11.166485] b43: disagrees about version of symbol ieee80211_queue_work
[   11.166487] b43: Unknown symbol ieee80211_queue_work (err -22)
[   11.354637] ath9k 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.354651] ath9k 0000:07:00.0: setting latency timer to 64
[   11.357553] ath: phy0: Mac Chip Rev 0x2c0.0 is not supported by this driver
[   11.357556] ath: phy0: Unable to initialize hardware; initialization status: -95
[   11.357559] ath9k 0000:07:00.0: Failed to initialize device
[   11.357621] ath9k 0000:07:00.0: PCI INT A disabled
[   11.357625] ath9k: probe of 0000:07:00.0 failed with error -95
[   11.493376] cfg80211: World regulatory domain updated:
[   11.493379] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.493381] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.493384] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.493385] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.493387] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.493389] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.465645] type=1400 audit(1355076347.560:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=912 comm="apparmor_parser"
[   13.466164] type=1400 audit(1355076347.560:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=912 comm="apparmor_parser"
[   50.174716] type=1400 audit(1355076384.326:24): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=1992 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0

```

My  network controller is 

*Network controller: Atheros Communications Inc. Device 0036 (rev 01)*

Please help me in making wifi working

Thanks
varghese

---

