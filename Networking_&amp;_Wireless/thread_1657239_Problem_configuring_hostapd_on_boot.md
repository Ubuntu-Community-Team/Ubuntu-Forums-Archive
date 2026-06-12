---
title: "Problem configuring hostapd on boot"
date: 2011-01-01
forum: Networking &amp; Wireless
---

### Post by someh4x0r on 2011-01-01
EDIT2: Solved. Moving the hostapd line from wlan0 to br0 in /etc/network/interfaces seems to fix it.

I am trying to set up a wireless access point with an ath5k card. It works correctly, but, if I reboot, hostapd will treat every single attempt to connect as if it had a wrong passphrase (it will give the "deauthenticated due to local deauth request" error). If I kill hostapd and run it again with the EXACT SAME command line, it works properly. My (unconfirmed) hypothesis is some type of timing/race condition problem. Can anybody help?

EDIT: Seems related to [http://ubuntuforums.org/showthread.php?t=1598164](http://ubuntuforums.org/showthread.php?t=1598164).

Hardware:
```

05:00.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

```/etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto tap0
iface tap0 inet manual
        pre-up openvpn --mktun --dev tap0

auto wlan0
iface wlan0 inet manual
        pre-up iw dev wlan0 set type __ap
        hostapd /etc/hostapd/hostapd.conf

auto br0
iface br0 inet static
        address 10.42.0.1
        network 10.42.0.0
        netmask 255.255.255.0
        broadcast 10.42.0.255
        bridge_ports wlan0 tap0
        bridge_fd 0

```/etc/hostapd/hostapd.conf
```

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

ssid=test
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

#ieee80211n=1
#ht_capab=[HT40-][SHORT-GI-20][SHORT-GI-40]

wpa=2
wpa_passphrase=secret passphrase
wpa_key_mgmt=WPA-PSK
rsn_pairwise=CCMP

```

---

