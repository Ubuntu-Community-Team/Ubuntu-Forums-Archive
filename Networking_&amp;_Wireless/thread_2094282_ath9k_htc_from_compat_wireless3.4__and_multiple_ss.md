---
title: "ath9k_htc from compat wireless3.4  and multiple ssid not working"
date: 2012-12-13
forum: Networking &amp; Wireless
---

### Post by mehta_4v on 2012-12-13
Hi all,

I am using ubuntu 10.04.  I have one USB adapter from Alfa which is AWUS036NHA having the  atheros chipset ar9271. I want to make it an AP with multiple ssid on my x86. SO I downloaded the compat wireless 3.4 which ahs the ath9k_htc and also the multiple virtual interface support. But when I run the hostapd with conf file having  multiple ssid configuration I can see the ssid on the client side but I  am not able to connect to the AP. This happens for the single ssid as  well when I use the compat wireless drivers. It also happens on the x86.  Following is some info:

```

lsmod 
Module                  Size  Used by    Not tainted 
ath9k 76274 0 - Live 0xbf118000 
ath9k_htc 51796 0 - Live 0xbf103000 
ath9k_common 1805 2 ath9k,ath9k_htc, Live 0xbf0fd000 
ath9k_hw 339707 3 ath9k,ath9k_htc,ath9k_common, Live 0xbf099000 
ath 14336 4 ath9k,ath9k_htc,ath9k_common,ath9k_hw, Live 0xbf08f000 
mac80211 226938 2 ath9k,ath9k_htc, Live 0xbf043000 
cfg80211 160567 4 ath9k,ath9k_htc,ath,mac80211, Live 0xbf00a000 
compat 8493 6 ath9k,ath9k_htc,ath9k_common,ath9k_hw,mac80211,cfg80211,  Live 0xbf000000 

```

```

The hostapd log :: 

./hostapd_with_hostap minimalistic.conf -B -dd 
###########In main 

###########argc = 4, optind = 3 

###########interfaces.count = 1 

###########In hostapd_global_init 

random: Trying to read entropy from /dev/random 
Configuration file: minimalistic.conf 
########In hostapd_config_read 

########conf->driver = wpa_drivers[0] = nl80211 

########wpa_drivers[0] = nl80211 

########bss->ssid.ssid = ssid1 

########hostapd_config_bss 

########conf->bss->iface = wlan4, conf->num_bss = 1 

########bss->ssid.ssid = ssid2 

##########hostapd_driver_init 

OOOOOOOOOOOO#########1, err = 1 

OOOOOOOOOOOO#########inside nl_get_multicast_id, send_)and_recv returns  0, res.id = 2 

OOOOOOOOOOOO#########1, err = 1 

OOOOOOOOOOOO#########inside nl_get_multicast_id, send_)and_recv returns  0, res.id = 4 

OOOOOOOOOOOO#########1, err = 1 

OOOOOOOOOOOO#########inside nl_get_multicast_id, send_)and_recv returns  0, res.id = 3 

nl80211: interface wlan4 in phy phy1 
rfkill: Cannot open RFKILL control device 
nl80211: RFKILL status not available 
OOOOOOOOOOOO#########below Here 2 

OOOOOOOOOOOO#########inside wpa_driver_nl80211_finish_drv_init 

OOOOOOOOOOOO#########wpa_driver_nl80211_capa 

OOOOOOOOOOOO#########Here 1 

OOOOOOOOOOOO#########inside wpa_driver_nl80211_get_info 

OOOOOOOOOOOO#########Charvi 1 

OOOOOOOOOOOO#########Charvi 4, drv->first_bss.ifindex = 6 

OOOOOOOOOOOO#########1, err = 1 

OOOOOOOOOOOO#########inside wiphy_info_handler 

OOOOOOOOOOOO#########Here 2 

OOOOOOOOOOOO#########Here 3 

OOOOOOOOOOOO#########Here 4 

nl80211: Using driver-based off-channel TX 
OOOOOOOOOOOO#########Here 5 

OOOOOOOOOOOO#########Here 6 

OOOOOOOOOOOO#########linux_get_ifhwaddr 

OOOOOOOOOOOO#########nl80211_register_action_frames 

OOOOOOOOOOOO#########eloop_register_timeout, send_rfkill_event = 0 

OOOOOOOOOOOO#########below Here 3 

OOOOOOOOOOOO#########below Here 4 

nl80211: Add own interface ifindex 6 
nl80211: New interface mon.wlan4 created: ifindex=7 
nl80211: Add own interface ifindex 7 
#######setup_interface 

#######hostapd_validate_bssid_configuration 

BSS count 2, BSSID mask ff:ff:ff:ff:ff:fe (1 bits) 
OOOOOOOOOOOO#########1, err = 1 

OOOOOOOOOOOO#########1, err = 1 

nl80211: Regulatory information - country=00 
nl80211: 2402-2472 @ 40 MHz 
nl80211: 2457-2482 @ 20 MHz 
nl80211: 2474-2494 @ 20 MHz 
nl80211: 5170-5250 @ 40 MHz 
nl80211: 5735-5835 @ 40 MHz 
nl80211: Added 802.11b mode based on 802.11g information 
Allowed channel: mode=1 chan=1 freq=2412 MHz max_tx_power=20 dBm 
Allowed channel: mode=1 chan=2 freq=2417 MHz max_tx_power=20 dBm 
Allowed channel: mode=1 chan=3 freq=2422 MHz max_tx_power=20 dBm 
Allowed channel: mode=1 chan=4 freq=2427 MHz max_tx_power=20 dBm 
Allowed channel: mode=1 chan=5 freq=2432 MHz max_tx_power=20 dBm 
Allowed channel: mode=1 chan=6 freq=2437 MHz max_tx_power=20 dBm 
Allowed channel: mode=1 chan=7 freq=2442 MHz max_tx_power=20 dBm 
Allowed channel: mode=1 chan=8 freq=2447 MHz max_tx_power=20 dBm 
Allowed channel: mode=1 chan=9 freq=2452 MHz max_tx_power=20 dBm 
Allowed channel: mode=1 chan=10 freq=2457 MHz max_tx_power=20 dBm 
Allowed channel: mode=1 chan=11 freq=2462 MHz max_tx_power=20 dBm 
Allowed channel: mode=0 chan=1 freq=2412 MHz max_tx_power=20 dBm 
Allowed channel: mode=0 chan=2 freq=2417 MHz max_tx_power=20 dBm 
Allowed channel: mode=0 chan=3 freq=2422 MHz max_tx_power=20 dBm 
Allowed channel: mode=0 chan=4 freq=2427 MHz max_tx_power=20 dBm 
Allowed channel: mode=0 chan=5 freq=2432 MHz max_tx_power=20 dBm 
Allowed channel: mode=0 chan=6 freq=2437 MHz max_tx_power=20 dBm 
Allowed channel: mode=0 chan=7 freq=2442 MHz max_tx_power=20 dBm 
Allowed channel: mode=0 chan=8 freq=2447 MHz max_tx_power=20 dBm 
Allowed channel: mode=0 chan=9 freq=2452 MHz max_tx_power=20 dBm 
Allowed channel: mode=0 chan=10 freq=2457 MHz max_tx_power=20 dBm 
Allowed channel: mode=0 chan=11 freq=2462 MHz max_tx_power=20 dBm 
#######hostapd_setup_interface_complete 

Completing interface initialization 
Mode: IEEE 802.11g  Channel: 1  Frequency: 2412 MHz 
RATE[0] rate=10 flags=0x1 
RATE[1] rate=20 flags=0x1 
RATE[2] rate=55 flags=0x1 
RATE[3] rate=110 flags=0x1 
RATE[4] rate=60 flags=0x0 
RATE[5] rate=90 flags=0x0 
RATE[6] rate=120 flags=0x0 
RATE[7] rate=180 flags=0x0 
RATE[8] rate=240 flags=0x0 
RATE[9] rate=360 flags=0x0 
RATE[10] rate=480 flags=0x0 
RATE[11] rate=540 flags=0x0 
#######hostapd_setup_bss 

Flushing old station entries 
Deauthenticate all stations 
wpa_driver_nl80211_set_key: ifindex=6 alg=0 addr=(nil) key_idx=0  set_tx=0 seq_len=0 key_len=0 
OOOOOOOOOOOO#########inside error_handler, err->error = -2 

wpa_driver_nl80211_set_key: ifindex=6 alg=0 addr=(nil) key_idx=1  set_tx=0 seq_len=0 key_len=0 
OOOOOOOOOOOO#########inside error_handler, err->error = -2 

wpa_driver_nl80211_set_key: ifindex=6 alg=0 addr=(nil) key_idx=2  set_tx=0 seq_len=0 key_len=0 
OOOOOOOOOOOO#########inside error_handler, err->error = -2 

wpa_driver_nl80211_set_key: ifindex=6 alg=0 addr=(nil) key_idx=3  set_tx=0 seq_len=0 key_len=0 
OOOOOOOOOOOO#########inside error_handler, err->error = -2 

Using interface wlan4 with hwaddr 02:c0:ca:6c:a4:60 and ssid 'ssid1' 
nl80211: Set beacon (beacon_set=0) 
wpa_driver_nl80211_set_operstate: operstate 0->1 (UP) 
netlink: Operstate: linkmode=-1, operstate=6 
#######hostapd_setup_bss 

#######hapd->iface->bss[0]->own_addr = ÀÊl¤` 

$$$$$$$$$$$$$$$$$$My Print$$$$$$$$$$$$$$$$$ 
######################4v: wpa_driver_nl80211_if_add to add wlan4_1 

nl80211: New interface wlan4_1 created: ifindex=8 
nl80211: Add own interface ifindex 8 
Flushing old station entries 
Deauthenticate all stations 
wpa_driver_nl80211_set_key: ifindex=8 alg=0 addr=(nil) key_idx=0  set_tx=0 seq_len=0 key_len=0 
OOOOOOOOOOOO#########inside error_handler, err->error = -2 

wpa_driver_nl80211_set_key: ifindex=8 alg=0 addr=(nil) key_idx=1  set_tx=0 seq_len=0 key_len=0 
OOOOOOOOOOOO#########inside error_handler, err->error = -2 

wpa_driver_nl80211_set_key: ifindex=8 alg=0 addr=(nil) key_idx=2  set_tx=0 seq_len=0 key_len=0 
OOOOOOOOOOOO#########inside error_handler, err->error = -2 

wpa_driver_nl80211_set_key: ifindex=8 alg=0 addr=(nil) key_idx=3  set_tx=0 seq_len=0 key_len=0 
OOOOOOOOOOOO#########inside error_handler, err->error = -2 

Using interface wlan4_1 with hwaddr 02:c0:ca:6c:a4:61 and ssid 'ssid2' 
nl80211: Set beacon (beacon_set=0) 
wpa_driver_nl80211_set_operstate: operstate 1->1 (UP) 
netlink: Operstate: linkmode=-1, operstate=6 
wlan4: Setup of interface done. 


Added some prints of my own. 

```

```

Then the hostapd.conf file: 

interface=wlan4 
driver=nl80211 
ssid=ssid1 
channel=1 
hw_mode=g 

bssid=02:C0:CA:6C:A4:60 
bss=wlan4_1 
ssid=ssid2 

```

```

After running the hostapd i get this: 
wlan4     IEEE 802.11bgn  Mode:Master  Frequency:2.412 GHz Tx-Power=20 dBm 
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 

mon.wlan4  IEEE 802.11bgn  Mode:Monitor  Frequency:2.412 GHz Tx-Power=20 dBm 
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 

wlan4_1   IEEE 802.11bgn  Mode:Master  Tx-Power=20 dBm 
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 


```

Then I run dhcpd on the two interfaces. 
But when I try to connect to the AP from my cell I cant get it to connect. 
It just shows saved.

Anybody any idea ??

---

