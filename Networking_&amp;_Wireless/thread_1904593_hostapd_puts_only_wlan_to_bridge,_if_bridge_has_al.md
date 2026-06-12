---
title: "hostapd puts only wlan to bridge, if bridge has already a ethX"
date: 2012-01-05
forum: Networking &amp; Wireless
---

### Post by jogl on 2012-01-05
Hello everyone,

I'm configuring my new homerouter (ubuntu 11.10 x64). I have a working lan + wlan bridge for LAN:
```
...
#### Bridge for LAN

auto br-lan
iface br-lan inet static
        address 10.111.1.1
        netmask 255.255.255.0
        broadcast 10.111.1.255
        bridge_ports eth1 wlan0
        bridge_fd 0
        bridge_stp no
...
``` For WLAN I'm using Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) with ath9k and hostapd (just simple - this works)

Okay, now I want to configure a wlan for guests. I extend my config in /etc/network/interfaces:```
#### Bridge for GUESTS

auto br-guests
iface br-guests inet static
        bridge_ports wlan1
        address 10.111.2.1
        netmask 255.255.255.0
        broadcast 10.111.2.255
        network 10.111.2.0
```My hostapd-config looks like:```
ctrl_interface=/var/run/hostapd-phy0
driver=nl80211
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
hw_mode=g
channel=1

country_code=AT


logger_syslog=127
logger_syslog_level=2
logger_stdout=127
logger_stdout_level=2
ieee80211n=1
ht_capab=[HT20][SHORT-GI-40][DSSS_CCK-40]
ieee80211d=1

interface=wlan0
ctrl_interface=/var/run/hostapd-phy0
wpa_passphrase=passwort
auth_algs=1
wpa=2
wpa_pairwise=CCMP
ssid=Vorhautkrampf beta 2.0
bridge=br-lan
wmm_enabled=1
bssid=e0:b9:a5:42:a5:aa
ignore_broadcast_ssid=0



bss=wlan1
ctrl_interface=/var/run/hostapd-phy0
wpa_passphrase=passwort
auth_algs=1
wpa=2
wpa_pairwise=CCMP
ssid=FM4 Gaestezimmer
bridge=br-guests
wmm_enabled=1
bssid=e0:b9:a5:42:a5:ab
ignore_broadcast_ssid=0
```As I know, bridge interfaces could not add wlan0 or wlan1 on startup. Hostapd has to add wlan0 & wlan1 to the bridge interfaces therefor.

The funny (or bad) thing is, that the br-guests starts (if I check with "brctl show") but after hostapd is also loaded, only wlan0 is added to bridge br-lan. At this point I have to manually adding wlan1 to bridge br-guests.
[U][B]
First test:[/B][/U]> For troubleshooting I have made a temporary test: After adding another physical nic (eth2) to bridge br-guests, hostapd adds wlan1 to this bridge and all works fine. But I must use eth2 for another net (dmz).:(
[U][B]
Temporary workaround:[/B][/U]> Adding in /etc/rc.local "brctl addif br-guests wlan1".
I don't know, if this is a good solution while searching for a persistant solution.Is it not possible to add only a wlan-interface to an bridge without other bridge_ports?
Is this a bug in ubuntu? (maybe anyone can also test it?)
Should I have to configure this by another way?

Thanks in advance, maybe anyone has a tip for me?

cheers,
JoGl

---

