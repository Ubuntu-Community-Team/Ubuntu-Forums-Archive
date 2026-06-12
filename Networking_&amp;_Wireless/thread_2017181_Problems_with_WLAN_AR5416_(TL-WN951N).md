---
title: "Problems with WLAN AR5416 (TL-WN951N)"
date: 2012-07-04
forum: Networking &amp; Wireless
---

### Post by kasunt on 2012-07-04
Hi folks,

Im having some trouble getting this card TP-LINK TL-WN951N to work on 11.10. Im actually using XMBCbuntu but I believe this is based on 11.10. Authentication timeout occurs and I have checked and rechecked everything.

On my router I tried using WPA/WPA2 mixed mode as well as strict WPA2 mode. None of these worked.

Anyone got some idea about this ?


```
htpc@kuzyt-htpc:~$ lspci | grep Network
06:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
```

```
htpc@kuzyt-htpc:~$ lsmod | grep ath
ath9k                 112612  0
mac80211              393421  1 ath9k
ath9k_common           13599  1 ath9k
ath9k_hw              293933  2 ath9k,ath9k_common
ath                    19387  2 ath9k,ath9k_hw
cfg80211              172427  3 ath9k,mac80211,ath
```

```
htpc@kuzyt-htpc:~$ dmesg | egrep 'ath|firm'
[    7.250125] ath9k 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    7.708388] ath: EEPROM regdomain: 0x809c
[    7.708395] ath: EEPROM indicates we should expect a country code
[    7.708411] ath: doing EEPROM country->regdmn map search
[    7.708415] ath: country maps to regdmn code: 0x52
[    7.708419] ath: Country alpha2 being used: CN
[    7.708422] ath: Regpair used: 0x52
[    8.104289] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[    8.105365] Registered led device: ath9k-phy0
```

```
htpc@kuzyt-htpc:~$ dmesg | grep wlan0
[    8.215485] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    8.427971] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    8.527505] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

```
htpc@kuzyt-htpc:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr b0:48:7a:e6:47:f3
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```


```
htpc@kuzyt-htpc:~$ sudo wpa_supplicant -i wlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf -D nl80211 -dd
Initializing interface 'wlan0' conf '/etc/wpa_supplicant/wpa_supplicant.conf' driver 'nl80211' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant/wpa_supplicant.conf' -> '/etc/wpa_supplicant/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 3 - start of a new network block
ssid - hexdump_ascii(len=8):
     4b 55 5a 59 54 4e 45 54                           KUZYTNET
scan_ssid=1 (0x1)
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='KUZYTNET'
netlink: Operstate: linkmode=1, operstate=5
Own MAC address: b0:48:7a:e6:47:f3
wpa_driver_nl80211_set_key: ifindex=3 alg=0 addr=0x80e4808 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_nl80211_set_key: ifindex=3 alg=0 addr=0x80e4808 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_nl80211_set_key: ifindex=3 alg=0 addr=0x80e4808 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_nl80211_set_key: ifindex=3 alg=0 addr=0x80e4808 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_nl80211_set_key: ifindex=3 alg=0 addr=0x80e4808 key_idx=4 set_tx=0 seq_len=0 key_len=0
wpa_driver_nl80211_set_key: ifindex=3 alg=0 addr=0x80e4808 key_idx=5 set_tx=0 seq_len=0 key_len=0
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
WPS: UUID based on MAC address - hexdump(len=16): 1f f1 1f 77 cd 34 5a 7c a3 7f 10 76 89 f3 73 58
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: Supplicant port status: Unauthorized
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: Supplicant port status: Unauthorized
EAPOL: Supplicant port status: Unauthorized
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
State: DISCONNECTED -> SCANNING
Scan SSID - hexdump_ascii(len=8):
     4b 55 5a 59 54 4e 45 54                           KUZYTNET
Starting AP scan for wildcard SSID
nl80211: Scan SSID - hexdump_ascii(len=8):
     4b 55 5a 59 54 4e 45 54                           KUZYTNET
nl80211: Scan SSID - hexdump_ascii(len=0): [NULL]
Scan requested (ret=0) - scan timeout 10 seconds
nl80211: Event message available
nl80211: Scan trigger
EAPOL: disable timer tick
EAPOL: Supplicant port status: Unauthorized
nl80211: Event message available
nl80211: New scan results available
Received scan results (9 BSSes)
BSS: Start scan result update 1
BSS: Add new id 0 BSSID 58:6d:8f:26:20:7a SSID 'KUZYTNET'
BSS: Add new id 1 BSSID 78:a0:51:0f:71:53 SSID 'Dirty Mike and the Boys'
BSS: Add new id 2 BSSID 08:76:ff:71:77:38 SSID 'Watchtower'
BSS: Add new id 3 BSSID 00:60:64:67:5c:30 SSID 'Kryptonite'
BSS: Add new id 4 BSSID 00:60:64:71:7a:b4 SSID 'NetComm23'
BSS: Add new id 5 BSSID c4:3d:c7:6a:31:be SSID 'akihirosato'
BSS: Add new id 6 BSSID 00:0f:3d:9c:bf:0c SSID 'DLINK'
BSS: Add new id 7 BSSID 00:18:0a:01:57:72 SSID 'creakernet'
BSS: Add new id 8 BSSID 58:6d:8f:26:20:7c SSID 'KUZYTNET-guest'
New scan results available
WPS: attr type=0x104a len=1
WPS: attr type=0x1044 len=1
WPS: attr type=0x1047 len=16
WPS: attr type=0x103c len=1
WPS: attr type=0x104a len=1
WPS: attr type=0x1044 len=1
WPS: attr type=0x1047 len=16
WPS: attr type=0x103c len=1
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 58:6d:8f:26:20:7a ssid='KUZYTNET' wpa_ie_len=28 rsn_ie_len=24 caps=0x411
   selected based on RSN IE
   selected WPA AP 58:6d:8f:26:20:7a ssid='KUZYTNET'
Automatic auth_alg selection: 0x1
RSN: using IEEE 802.11i/D9.0
WPA: Selected cipher suites: group 8 pairwise 24 key_mgmt 2 proto 2
WPA: set AP WPA IE - hexdump(len=30): dd 1c 00 50 f2 01 01 00 00 50 f2 02 02 00 00 50 f2 04 00 50 f2 02 01 00 00 50 f2 02 0c 00
WPA: set AP RSN IE - hexdump(len=26): 30 18 01 00 00 0f ac 02 02 00 00 0f ac 04 00 0f ac 02 01 00 00 0f ac 02 0c 00
WPA: using GTK TKIP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
FT: Stored MDIE and FTIE from (Re)Association Response - hexdump(len=0):
Cancelling scan request
Trying to authenticate with 58:6d:8f:26:20:7a (SSID='KUZYTNET' freq=2412 MHz)
No keys have been configured - skip key clearing
State: SCANNING -> AUTHENTICATING
EAPOL: External notification - EAP success=0
EAPOL: Supplicant port status: Unauthorized
EAPOL: External notification - EAP fail=0
EAPOL: Supplicant port status: Unauthorized
EAPOL: External notification - portControl=Auto
EAPOL: Supplicant port status: Unauthorized
nl80211: Authenticate (ifindex=3)
  * bssid=58:6d:8f:26:20:7a
  * freq=2412
  * SSID - hexdump_ascii(len=8):
     4b 55 5a 59 54 4e 45 54                           KUZYTNET
  * IEs - hexdump(len=0): [NULL]
  * Auth Type 0
nl80211: Authentication request send successfully
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
nl80211: Event message available
nl80211: MLME event 37; timeout with 58:6d:8f:26:20:7a
SME: Authentication timed out
Setting scan request: 5 sec 0 usec
^CCTRL-EVENT-TERMINATING - signal 2 received
Removing interface wlan0
No keys have been configured - skip key clearing
State: AUTHENTICATING -> DISCONNECTED
wpa_driver_nl80211_set_operstate: operstate 0->0 (DORMANT)
netlink: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: Supplicant port status: Unauthorized
EAPOL: External notification - portValid=0
EAPOL: Supplicant port status: Unauthorized
EAPOL: External notification - EAP success=0
EAPOL: Supplicant port status: Unauthorized
No keys have been configured - skip key clearing
BSS: Remove id 0 BSSID 58:6d:8f:26:20:7a SSID 'KUZYTNET'
BSS: Remove id 1 BSSID 78:a0:51:0f:71:53 SSID 'Dirty Mike and the Boys'
BSS: Remove id 2 BSSID 08:76:ff:71:77:38 SSID 'Watchtower'
BSS: Remove id 3 BSSID 00:60:64:67:5c:30 SSID 'Kryptonite'
BSS: Remove id 4 BSSID 00:60:64:71:7a:b4 SSID 'NetComm23'
BSS: Remove id 5 BSSID c4:3d:c7:6a:31:be SSID 'akihirosato'
BSS: Remove id 6 BSSID 00:0f:3d:9c:bf:0c SSID 'DLINK'
BSS: Remove id 7 BSSID 00:18:0a:01:57:72 SSID 'creakernet'
BSS: Remove id 8 BSSID 58:6d:8f:26:20:7c SSID 'KUZYTNET-guest'
Cancelling scan request
Cancelling authentication timeout
netlink: Operstate: linkmode=0, operstate=6
```

---

### Post by kasunt on 2012-07-05
Installed the latest compact-wireless-3.5 stable drivers but still no luck. Its failing to authenticate.

any ideas from anyone ? atleast on tips on where to look for the problem would help at this stage.

---

### Post by Kirk Schnable on 2012-07-11
First of all, let me congratulate you on a well prepared help request.  It's unfortunate that those tend to be the most ignored sometimes.

Have you been to these threads?

[http://ubuntuforums.org/showthread.php?t=1916598](http://ubuntuforums.org/showthread.php?t=1916598)
[http://askubuntu.com/questions/110949/atheros-ar5008-not-working-properly](http://askubuntu.com/questions/110949/atheros-ar5008-not-working-properly)
[http://askubuntu.com/questions/85973/random-disconnects-with-an-atheros-ar5008](http://askubuntu.com/questions/85973/random-disconnects-with-an-atheros-ar5008)

The short version, it looks like 11.10 might have some driver issues with this card.

You might try looking for the latest version of the drivers, and see if that fixes your issue.  You may want to try a 12.04 live CD and see if the issue is already fixed in a later version of Ubuntu.

I'll subscribe here, and I'd be happy to take a look deeper later when I have more time.

Kirk

---

### Post by kasunt on 2012-07-12
Hey thanks for the info.

Yeah I had gone through various suggestions that others have found to work with different Atheros chipsets. But none of them worked in my case. So I just gave up my precious time trying to fix it. Perhaps it works with certain kernels but having tried the latest drivers im not sure why it was failing. Its definitely the driver as it had worked with windows os's.

So I bought a new wireless card also based on Atheros chipset. This is a TP-WDN4800 with which worked right out of the box. And it had 2.4Ghz and 5Ghz which is ideal for my purpose. No errors or authentication problems either.

---

