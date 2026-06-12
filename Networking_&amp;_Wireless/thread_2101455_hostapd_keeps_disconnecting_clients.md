---
title: "hostapd keeps disconnecting clients"
date: 2013-01-04
forum: Networking &amp; Wireless
---

### Post by Gibbon9 on 2013-01-04
Hello,

I have recently build my first server. Decided to put  ubuntu server as operating system and everything works out pretty well  except one thing. I've decided to use the server as router too (since my  current router sometimes drops) but hostapd disconnects wifi clients  right after successful authentication. I'm trying to resolve this issue  for about a week and I'm really out of ideas. :(

Thanks in advance for any insight. Gibbon

This is log i get after running **hostapd -d /etc/hostapd/hostapd.conf** and connecting client (NB with ubuntu)
```
random: Got 4/4 bytes from /dev/random
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
nl80211: if_removed already cleared - ignore event
nl80211: Add ifindex 5 for bridge br0
nl80211: Add own interface ifindex 5
VLAN: vlan_newlink(wlan0)
mgmt::auth
authentication: STA=00:13:e8:96:ff:7f auth_alg=0 auth_transaction=1 status_code=0 wep=0
  New STA
wlan0: STA 00:13:e8:96:ff:7f IEEE 802.11: authentication OK (open system)
wlan0: STA 00:13:e8:96:ff:7f MLME: MLME-AUTHENTICATE.indication(00:13:e8:96:ff:7f, OPEN_SYSTEM)
wlan0: STA 00:13:e8:96:ff:7f MLME: MLME-DELETEKEYS.request(00:13:e8:96:ff:7f)
authentication reply: STA=00:13:e8:96:ff:7f auth_alg=0 auth_transaction=2 resp=0 (IE len=0)
mgmt::auth cb
wlan0: STA 00:13:e8:96:ff:7f IEEE 802.11: authenticated
mgmt::assoc_req
association request: STA=00:13:e8:96:ff:7f capab_info=0x431 listen_interval=10
  new AID 1
wlan0: STA 00:13:e8:96:ff:7f IEEE 802.11: association OK (aid 1)
mgmt::assoc_resp cb
wlan0: STA 00:13:e8:96:ff:7f IEEE 802.11: associated (aid 1)
wlan0: STA 00:13:e8:96:ff:7f MLME: MLME-ASSOCIATE.indication(00:13:e8:96:ff:7f)
wlan0: STA 00:13:e8:96:ff:7f MLME: MLME-DELETEKEYS.request(00:13:e8:96:ff:7f)
wpa_driver_nl80211_set_key: ifindex=4 alg=0 addr=0x15a2800 key_idx=0 set_tx=1 seq_len=0 key_len=0
   addr=00:13:e8:96:ff:7f
wlan0: STA 00:13:e8:96:ff:7f WPA: event 1 notification
wpa_driver_nl80211_set_key: ifindex=4 alg=0 addr=0x15a2800 key_idx=0 set_tx=1 seq_len=0 key_len=0
   addr=00:13:e8:96:ff:7f
IEEE 802.1X: Ignore STA - 802.1X not enabled or forced for WPS
wlan0: STA 00:13:e8:96:ff:7f WPA: start authentication
WPA: 00:13:e8:96:ff:7f WPA_PTK entering state INITIALIZE
wpa_driver_nl80211_set_key: ifindex=4 alg=0 addr=0x15a2800 key_idx=0 set_tx=1 seq_len=0 key_len=0
   addr=00:13:e8:96:ff:7f
wlan0: STA 00:13:e8:96:ff:7f IEEE 802.1X: unauthorizing port
WPA: 00:13:e8:96:ff:7f WPA_PTK_GROUP entering state IDLE
WPA: 00:13:e8:96:ff:7f WPA_PTK entering state AUTHENTICATION
WPA: 00:13:e8:96:ff:7f WPA_PTK entering state AUTHENTICATION2
WPA: Re-initialize GMK/Counter on first station
GMK - hexdump(len=32): [REMOVED]
Key Counter - hexdump(len=32): [REMOVED]
GTK - hexdump(len=16): [REMOVED]
wpa_driver_nl80211_set_key: ifindex=4 alg=3 addr=0x491502 key_idx=1 set_tx=1 seq_len=0 key_len=16
   broadcast key
WPA:  Assign ANonce - hexdump(len=32): cc 50 85 ee ed d2 4f 35 be d5 1a df 6e  cc 89 a0 80 04 a6 13 2a 6d 10 85 28 e4 88 a4 28 d2 8a 8f
WPA: 00:13:e8:96:ff:7f WPA_PTK entering state INITPSK
WPA: 00:13:e8:96:ff:7f WPA_PTK entering state PTKSTART
wlan0: STA 00:13:e8:96:ff:7f WPA: sending 1/4 msg of 4-Way Handshake
WPA: Send EAPOL(version=2 secure=0 mic=0 ack=1 install=0 pairwise=8 kde_len=0 keyidx=0 encr=0)
WPA: Use EAPOL-Key timeout of 100 ms (retry counter 1)
nl80211: Event message available
nl80211: New station 00:13:e8:96:ff:7f
IEEE 802.1X: 00:13:e8:96:ff:7f TX status - version=2 type=3 length=95 - ack=1
WPA: EAPOL-Key TX status for STA 00:13:e8:96:ff:7f ack=1
WPA: Increase initial EAPOL-Key 1/4 timeout by 1000 ms because of acknowledged frame
IEEE 802.1X: 121 bytes from 00:13:e8:96:ff:7f
   IEEE 802.1X: version=1 type=3 length=117
WPA: Received EAPOL-Key from 00:13:e8:96:ff:7f key_info=0x10a type=2 key_data_length=22
WPA:  Received Key Nonce - hexdump(len=32): c6 2d d6 45 9e 11 be 74 a2 e7 c7  68 1b bd 81 ed a0 4e bd 6c b7 5f 0a 4f 91 23 bd 02 b8 a6 60 0a
WPA: Received Replay Counter - hexdump(len=8): 00 00 00 00 00 00 00 01
wlan0: STA 00:13:e8:96:ff:7f WPA: received EAPOL-Key frame (2/4 Pairwise)
WPA: 00:13:e8:96:ff:7f WPA_PTK entering state PTKCALCNEGOTIATING
WPA: PTK derivation - A1=84:a6:c8:21:de:e6 A2=00:13:e8:96:ff:7f
WPA: Nonce1 - hexdump(len=32): cc 50 85 ee ed d2 4f 35 be d5 1a df 6e cc 89 a0 80 04 a6 13 2a 6d 10 85 28 e4 88 a4 28 d2 8a 8f
WPA: Nonce2 - hexdump(len=32): c6 2d d6 45 9e 11 be 74 a2 e7 c7 68 1b bd 81 ed a0 4e bd 6c b7 5f 0a 4f 91 23 bd 02 b8 a6 60 0a
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=48): [REMOVED]
WPA: 00:13:e8:96:ff:7f WPA_PTK entering state PTKCALCNEGOTIATING2
WPA: 00:13:e8:96:ff:7f WPA_PTK entering state PTKINITNEGOTIATING
wlan0: STA 00:13:e8:96:ff:7f WPA: sending 3/4 msg of 4-Way Handshake
WPA: Send EAPOL(version=2 secure=1 mic=1 ack=1 install=1 pairwise=8 kde_len=46 keyidx=1 encr=1)
Plaintext EAPOL-Key Key Data - hexdump(len=56): [REMOVED]
WPA: Use EAPOL-Key timeout of 100 ms (retry counter 1)
IEEE 802.1X: 00:13:e8:96:ff:7f TX status - version=2 type=3 length=151 - ack=1
WPA: EAPOL-Key TX status for STA 00:13:e8:96:ff:7f ack=1
IEEE 802.1X: 99 bytes from 00:13:e8:96:ff:7f
   IEEE 802.1X: version=1 type=3 length=95
WPA: Received EAPOL-Key from 00:13:e8:96:ff:7f key_info=0x30a type=2 key_data_length=0
WPA:  Received Key Nonce - hexdump(len=32): 00 00 00 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: Received Replay Counter - hexdump(len=8): 00 00 00 00 00 00 00 02
wlan0: STA 00:13:e8:96:ff:7f WPA: received EAPOL-Key frame (4/4 Pairwise)
WPA: 00:13:e8:96:ff:7f WPA_PTK entering state PTKINITDONE
wpa_driver_nl80211_set_key: ifindex=4 alg=3 addr=0x15a2800 key_idx=0 set_tx=1 seq_len=0 key_len=16
   addr=00:13:e8:96:ff:7f
wlan0: AP-STA-CONNECTED 00:13:e8:96:ff:7f
wlan0: STA 00:13:e8:96:ff:7f IEEE 802.1X: authorizing port
wlan0: STA 00:13:e8:96:ff:7f RADIUS: starting accounting session 50E73F09-00000000
wlan0: STA 00:13:e8:96:ff:7f WPA: pairwise key handshake completed (RSN)
wlan0: mgmt::deauth
wlan0: deauthentication: STA=00:13:e8:96:ff:7f reason_code=3
wlan0: AP-STA-DISCONNECTED 00:13:e8:96:ff:7f
wlan0: STA 00:13:e8:96:ff:7f WPA: event 3 notification
wpa_driver_nl80211_set_key: ifindex=4 alg=0 addr=0x15a2800 key_idx=0 set_tx=1 seq_len=0 key_len=0
   addr=00:13:e8:96:ff:7f
WPA: 00:13:e8:96:ff:7f WPA_PTK entering state DISCONNECTED
WPA: 00:13:e8:96:ff:7f WPA_PTK entering state INITIALIZE
wpa_driver_nl80211_set_key: ifindex=4 alg=0 addr=0x15a2800 key_idx=0 set_tx=1 seq_len=0 key_len=0
   addr=00:13:e8:96:ff:7f
wlan0: STA 00:13:e8:96:ff:7f IEEE 802.1X: unauthorizing port
wlan0: STA 00:13:e8:96:ff:7f IEEE 802.11: deauthenticated
wlan0: STA 00:13:e8:96:ff:7f MLME: MLME-DEAUTHENTICATE.indication(00:13:e8:96:ff:7f, 3)
wlan0: STA 00:13:e8:96:ff:7f MLME: MLME-DELETEKEYS.request(00:13:e8:96:ff:7f)
wpa_driver_nl80211_set_key: ifindex=4 alg=0 addr=0x15a2800 key_idx=0 set_tx=1 seq_len=0 key_len=0
   addr=00:13:e8:96:ff:7f
nl80211: Event message available
nl80211: Delete station 00:13:e8:96:ff:7f
```
My server contains 3 network adapters,  p4p1 (ethernet, outer), p5p1 (ethernet, inner), wlan0 (wifi, inner).

**hw specs (p5p1 and wlan0 are bridged by br0):**
_p4p1_
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
    Subsystem: Giga-byte Technology GA-EP45-DS5/GA-EG45M-DS2H Motherboard
    Kernel driver in use: r8169
    Kernel modules: r8169

_p5p1_
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
    Subsystem: Giga-byte Technology GA-EP45-DS5/GA-EG45M-DS2H Motherboard
    Kernel driver in use: r8169
    Kernel modules: r8169

_wlan0_
Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

**configs**
_/etc/network/interfaces_
```

auto lo
iface lo inet loopback

auto p4p1
iface p4p1 inet dhcp
  pre-up iptables-restore < /etc/iptables.config

auto p5p1
iface p5p1 inet manual

auto wlan0
iface wlan0 inet manual
  wireless-mode master

auto br0
iface br0 inet static
  address 192.168.2.1
  netmask 255.255.255.0
  network 192.168.2.0
  broadcast 192.168.2.255
  bridge-ports p5p1 wlan0
```_/etc/default/isc-dhcp-server_
```
INTERFACES="br0"
```_/etc/dhcp/dhcpd.conf_
```
ddns-update-style none;

option domain-name "example.org";
option domain-name-servers ns1.example.org, ns2.example.org;

default-lease-time 600;
max-lease-time 7200;

authoritative;

log-facility local7;

subnet 192.168.2.0 netmask 255.255.255.0 {
  range 192.168.2.100 192.168.2.200;
  option domain-name-servers 192.168.1.1;
  option subnet-mask 255.255.255.0;
  option broadcast-address 192.168.2.255;
  option routers 192.168.2.1;
}
```_/etc/default/hostapd_
```
DAEMON_CONF="/etc/hostapd/hostapd.conf"
```_/etc/hostapd/hostapd.conf_
```
interface=wlan0
bridge=br0
driver=nl80211

ssid=testWIFIg
hw_mode=g
channel=1

macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wpa=2
wpa_passphrase=wifipass
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP
```

---

### Post by jimmikaelkael on 2013-04-10
Hi,

Did you solved your problem ?

It seems I have the same problem with Ubuntu 12.04 and realtek devices, I suspect it could be hardware related.

---

