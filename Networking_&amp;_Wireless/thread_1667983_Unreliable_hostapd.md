---
title: "Unreliable hostapd"
date: 2011-01-15
forum: Networking &amp; Wireless
---

### Post by someh4x0r on 2011-01-15
Edit: New kernel of 2.6.35-25 broke everything, but installing linux-backports-modules-wireless-maverick-generic-pae seems to have fixed everything.

I have hostapd version 1:0.7.3-1 from Debian experimental and have an ath9k card. I am running Ubuntu Server 10.10. I have two virtual access points configured. Occasionally, clients will no longer be able to access each other, but they all can access the access point. No packets can be seen at all on wlan0/br0. Accessing across the two networks does work. Setting nohwcrypt=1 seems to fix the issue, but I am not sure about this and doing so reduces the speed. Does anybody know what the real problem is? syslog does not seem to show anything.

```

02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

``````

interface=wlan0
bridge=br0
driver=nl80211

logger_syslog=-1
logger_syslog_level=2
logger_stdout=-1
logger_stdout_level=2

dump_file=/tmp/hostapd.dump

ctrl_interface=/var/run/hostapd

ctrl_interface_group=0

ssid=name1
country_code=US
hw_mode=g
channel=1
beacon_int=100
dtim_period=2
max_num_sta=255
rts_threshold=2347
fragm_threshold=2346

macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0

wmm_enabled=1
wmm_ac_bk_cwmin=4
wmm_ac_bk_cwmax=10
wmm_ac_bk_aifs=7
wmm_ac_bk_txop_limit=0
wmm_ac_bk_acm=0
wmm_ac_be_aifs=3
wmm_ac_be_cwmin=4
wmm_ac_be_cwmax=10
wmm_ac_be_txop_limit=0
wmm_ac_be_acm=0
wmm_ac_vi_aifs=2
wmm_ac_vi_cwmin=3
wmm_ac_vi_cwmax=4
wmm_ac_vi_txop_limit=94
wmm_ac_vi_acm=0
wmm_ac_vo_aifs=2
wmm_ac_vo_cwmin=2
wmm_ac_vo_cwmax=3
wmm_ac_vo_txop_limit=47
wmm_ac_vo_acm=0

tx_queue_data3_aifs=7
tx_queue_data3_cwmin=15
tx_queue_data3_cwmax=1023
tx_queue_data3_burst=0

tx_queue_data2_aifs=3
tx_queue_data2_cwmin=15
tx_queue_data2_cwmax=63
tx_queue_data2_burst=0

tx_queue_data1_aifs=1
tx_queue_data1_cwmin=7
tx_queue_data1_cwmax=15
tx_queue_data1_burst=3.0

tx_queue_data0_aifs=1
tx_queue_data0_cwmin=3
tx_queue_data0_cwmax=7
tx_queue_data0_burst=1.5

tx_queue_after_beacon_aifs=2
tx_queue_after_beacon_cwmin=15
tx_queue_after_beacon_cwmax=1023
tx_queue_after_beacon_burst=0

tx_queue_beacon_aifs=2
tx_queue_beacon_cwmin=3
tx_queue_beacon_cwmax=7
tx_queue_beacon_burst=1.5

wme_enabled=1
ieee80211n=1
ht_capab=[HT40+][SHORT-GI-21][SHORT-GI-40][TX-STBC][RX-STBC1][DSSS_CCK-40]

wpa=2
wpa_passphrase=key1
wpa_key_mgmt=WPA-PSK
rsn_pairwise=CCMP
#ieee80211w=1

#ap_isolate=0

bss=wlan0_0
ssid=name2
bssid=00:22:43:19:35:13

macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0

wpa=3
wpa_passphrase=key2
wpa_pairwise=TKIP CCMP
rsn_pairwise=CCMP
#ieee80211w=1

wmm_enabled=1
wmm_ac_bk_cwmin=4
wmm_ac_bk_cwmax=10
wmm_ac_bk_aifs=7
wmm_ac_bk_txop_limit=0
wmm_ac_bk_acm=0
wmm_ac_be_aifs=3
wmm_ac_be_cwmin=4
wmm_ac_be_cwmax=10
wmm_ac_be_txop_limit=0
wmm_ac_be_acm=0
wmm_ac_vi_aifs=2
wmm_ac_vi_cwmin=3
wmm_ac_vi_cwmax=4
wmm_ac_vi_txop_limit=94
wmm_ac_vi_acm=0
wmm_ac_vo_aifs=2
wmm_ac_vo_cwmin=2
wmm_ac_vo_cwmax=3
wmm_ac_vo_txop_limit=47
wmm_ac_vo_acm=0

tx_queue_data3_aifs=7
tx_queue_data3_cwmin=15
tx_queue_data3_cwmax=1023
tx_queue_data3_burst=0

tx_queue_data2_aifs=3
tx_queue_data2_cwmin=15
tx_queue_data2_cwmax=63
tx_queue_data2_burst=0

tx_queue_data1_aifs=1
tx_queue_data1_cwmin=7
tx_queue_data1_cwmax=15
tx_queue_data1_burst=3.0

tx_queue_data0_aifs=1
tx_queue_data0_cwmin=3
tx_queue_data0_cwmax=7
tx_queue_data0_burst=1.5

tx_queue_after_beacon_aifs=2
tx_queue_after_beacon_cwmin=15
tx_queue_after_beacon_cwmax=1023
tx_queue_after_beacon_burst=0

tx_queue_beacon_aifs=2
tx_queue_beacon_cwmin=3
tx_queue_beacon_cwmax=7
tx_queue_beacon_burst=1.5

#ap_isolate=0

```

---

