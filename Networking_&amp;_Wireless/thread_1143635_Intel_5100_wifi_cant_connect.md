---
title: "Intel 5100 wifi cant connect"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by Peteriz on 2009-04-30
I have a Dell E6400 laptop with an Intel 5100 wireless card. I tried all the suggestions i could find in the forums but none worked, I can see my protected WLAN but no matter what i do the connection doesnt go through.
I tried 9.04, 8.10 and 9.04 x64..
some info:
lshw -C netowork : 
```
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:21:70:d5:f6:86
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 duplex=full firmware=1.7-7 ip=192.168.2.100 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 00
       serial: 00:22:fb:17:ad:00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 72:18:0f:0a:8d:1c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```here is the output from  the syslog:
```
Apr 30 11:11:33 peter-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto skynet' 
Apr 30 11:11:33 peter-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Apr 30 11:11:33 peter-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 30 11:11:33 peter-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Apr 30 11:11:33 peter-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Apr 30 11:11:33 peter-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Apr 30 11:11:33 peter-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Apr 30 11:11:33 peter-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Apr 30 11:11:33 peter-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto skynet' has security, but secrets are required. 
Apr 30 11:11:33 peter-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 
Apr 30 11:11:33 peter-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Apr 30 11:11:36 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 1 -> 2 
Apr 30 11:11:44 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 1 
Apr 30 11:11:45 peter-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 30 11:11:45 peter-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Apr 30 11:11:45 peter-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 
Apr 30 11:11:45 peter-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Apr 30 11:11:45 peter-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Apr 30 11:11:45 peter-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Apr 30 11:11:45 peter-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Apr 30 11:11:45 peter-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto skynet' has security, and secrets exist.  No new secrets needed. 
Apr 30 11:11:45 peter-laptop NetworkManager: <info>  Config: added 'ssid' value 'skynet' 
Apr 30 11:11:45 peter-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Apr 30 11:11:45 peter-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Apr 30 11:11:45 peter-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Apr 30 11:11:45 peter-laptop NetworkManager: <info>  Config: added 'proto' value 'WPA RSN' 
Apr 30 11:11:45 peter-laptop NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP' 
Apr 30 11:11:45 peter-laptop NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP' 
Apr 30 11:11:45 peter-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Apr 30 11:11:45 peter-laptop NetworkManager: <info>  Config: set interface ap_scan to 1 
Apr 30 11:11:45 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 1 -> 2 
Apr 30 11:11:48 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Apr 30 11:11:48 peter-laptop kernel: [   95.092035] wlan0: authenticate with AP f7ac9684
Apr 30 11:11:48 peter-laptop kernel: [   95.093948] wlan0: authenticated
Apr 30 11:11:48 peter-laptop kernel: [   95.093957] wlan0: associate with AP f7ac9684
Apr 30 11:11:48 peter-laptop kernel: [   95.096854] wlan0: RX AssocResp from f5bbc016 (capab=0x431 status=0 aid=1)
Apr 30 11:11:48 peter-laptop kernel: [   95.096866] wlan0: associated
Apr 30 11:11:48 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 4 
Apr 30 11:11:48 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 5 
Apr 30 11:11:49 peter-laptop kernel: [   95.586765] padlock: VIA PadLock not detected.
Apr 30 11:11:49 peter-laptop modprobe: WARNING: Error inserting padlock_aes (/lib/modules/2.6.27-11-generic/kernel/drivers/crypto/padlock-aes.ko): No such device 
Apr 30 11:11:49 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 6 
Apr 30 11:11:49 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7 
Apr 30 11:11:49 peter-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'skynet'. 
Apr 30 11:11:49 peter-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr 30 11:11:49 peter-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Apr 30 11:11:49 peter-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 
Apr 30 11:11:49 peter-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Apr 30 11:11:49 peter-laptop NetworkManager: <info>  dhclient started with pid 6183 
Apr 30 11:11:49 peter-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Apr 30 11:11:49 peter-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Apr 30 11:11:49 peter-laptop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Apr 30 11:11:49 peter-laptop dhclient: All rights reserved.
Apr 30 11:11:49 peter-laptop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Apr 30 11:11:49 peter-laptop dhclient: 
Apr 30 11:11:49 peter-laptop NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit 
Apr 30 11:11:49 peter-laptop dhclient: Listening on LPF/wlan0/00:22:fb:17:ad:00
Apr 30 11:11:49 peter-laptop dhclient: Sending on   LPF/wlan0/00:22:fb:17:ad:00
Apr 30 11:11:49 peter-laptop dhclient: Sending on   Socket/fallback
Apr 30 11:11:52 peter-laptop kernel: [   98.928701] wlan0: deauthenticated (Reason: 1)
Apr 30 11:11:52 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 0 
Apr 30 11:11:52 peter-laptop kernel: [   98.932111] mac80211-phy0: failed to remove key (0, f742c604) from hardware (-22)
Apr 30 11:11:52 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Apr 30 11:11:53 peter-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Apr 30 11:11:53 peter-laptop kernel: [   99.928099] wlan0: direct probe to AP f7ac9684 try 1
Apr 30 11:11:53 peter-laptop kernel: [   99.931080] wlan0 direct probe responded
Apr 30 11:11:53 peter-laptop kernel: [   99.931090] wlan0: authenticate with AP f7ac9684
Apr 30 11:11:53 peter-laptop kernel: [   99.933081] wlan0: authenticated
Apr 30 11:11:53 peter-laptop kernel: [   99.933091] wlan0: associate with AP f7ac9684
Apr 30 11:11:53 peter-laptop kernel: [   99.935873] wlan0: RX ReassocResp from f541c016 (capab=0x431 status=0 aid=1)
Apr 30 11:11:53 peter-laptop kernel: [   99.935883] wlan0: associated
Apr 30 11:11:53 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 4 
Apr 30 11:11:53 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 5 
Apr 30 11:11:53 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 6 
Apr 30 11:11:53 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7 
Apr 30 11:11:57 peter-laptop kernel: [  103.762191] wlan0: deauthenticated (Reason: 1)
Apr 30 11:11:57 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 0 
Apr 30 11:11:57 peter-laptop kernel: [  103.764258] mac80211-phy0: failed to remove key (0, f48ae204) from hardware (-22)
Apr 30 11:11:57 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Apr 30 11:11:58 peter-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Apr 30 11:11:58 peter-laptop kernel: [  104.760091] wlan0: direct probe to AP f7ac9684 try 1
Apr 30 11:11:58 peter-laptop kernel: [  104.763152] wlan0 direct probe responded
Apr 30 11:11:58 peter-laptop kernel: [  104.763164] wlan0: authenticate with AP f7ac9684
Apr 30 11:11:58 peter-laptop kernel: [  104.765083] wlan0: authenticated
Apr 30 11:11:58 peter-laptop kernel: [  104.765092] wlan0: associate with AP f7ac9684
Apr 30 11:11:58 peter-laptop kernel: [  104.767791] wlan0: RX ReassocResp from f569c016 (capab=0x431 status=0 aid=1)
Apr 30 11:11:58 peter-laptop kernel: [  104.767803] wlan0: associated
Apr 30 11:11:58 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 4 
Apr 30 11:11:58 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 5 
Apr 30 11:11:58 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 6 
Apr 30 11:11:58 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7 
Apr 30 11:12:01 peter-laptop kernel: [  108.426874] type=1503 audit(1241079121.898:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6225/net/" pid=6225 profile="/usr/sbin/cupsd"
Apr 30 11:12:02 peter-laptop kernel: [  108.541295] NET: Registered protocol family 10
Apr 30 11:12:02 peter-laptop kernel: [  108.542815] lo: Disabled Privacy Extensions
Apr 30 11:12:02 peter-laptop kernel: [  108.544468] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 30 11:12:02 peter-laptop kernel: [  108.547313] type=1503 audit(1241079122.018:6): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=6225 profile="/usr/sbin/cupsd"
Apr 30 11:12:02 peter-laptop kernel: [  108.554038] type=1503 audit(1241079122.026:7): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=6225 profile="/usr/sbin/cupsd"
Apr 30 11:12:02 peter-laptop kernel: [  108.556402] type=1503 audit(1241079122.030:8): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=6225 profile="/usr/sbin/cupsd"
Apr 30 11:12:02 peter-laptop kernel: [  108.558714] type=1503 audit(1241079122.030:9): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=6225 profile="/usr/sbin/cupsd"
Apr 30 11:12:02 peter-laptop kernel: [  108.560958] type=1503 audit(1241079122.034:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6225 profile="/usr/sbin/cupsd"
Apr 30 11:12:02 peter-laptop kernel: [  108.563648] type=1503 audit(1241079122.034:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6225 profile="/usr/sbin/cupsd"
Apr 30 11:12:02 peter-laptop kernel: [  108.566625] type=1503 audit(1241079122.038:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6225 profile="/usr/sbin/cupsd"
Apr 30 11:12:02 peter-laptop kernel: [  108.568943] type=1503 audit(1241079122.042:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=6225 profile="/usr/sbin/cupsd"
Apr 30 11:12:02 peter-laptop kernel: [  108.569095] type=1503 audit(1241079122.042:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/6225/net/dev" pid=6225 profile="/usr/sbin/cupsd"
Apr 30 11:12:02 peter-laptop kernel: [  108.607297] wlan0: deauthenticated (Reason: 1)
Apr 30 11:12:02 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 0 
Apr 30 11:12:02 peter-laptop kernel: [  108.608130] mac80211-phy0: failed to remove key (0, f6753e04) from hardware (-22)
Apr 30 11:12:02 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Apr 30 11:12:03 peter-laptop kernel: [  109.604134] wlan0: direct probe to AP f7ac9684 try 1
Apr 30 11:12:03 peter-laptop kernel: [  109.607107] wlan0 direct probe responded
Apr 30 11:12:03 peter-laptop kernel: [  109.607118] wlan0: authenticate with AP f7ac9684
Apr 30 11:12:03 peter-laptop kernel: [  109.608975] wlan0: authenticated
Apr 30 11:12:03 peter-laptop kernel: [  109.608984] wlan0: associate with AP f7ac9684
Apr 30 11:12:03 peter-laptop kernel: [  109.611762] wlan0: RX ReassocResp from f4974016 (capab=0x431 status=0 aid=1)
Apr 30 11:12:03 peter-laptop kernel: [  109.611772] wlan0: associated
Apr 30 11:12:03 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 4 
Apr 30 11:12:03 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 5 
Apr 30 11:12:03 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 6 
Apr 30 11:12:03 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7 
Apr 30 11:12:03 peter-laptop avahi-daemon[5083]: Registering new address record for fe80::222:fbff:fe17:ad00 on wlan0.*.
Apr 30 11:12:06 peter-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Apr 30 11:12:06 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 0 
Apr 30 11:12:06 peter-laptop kernel: [  113.441070] wlan0: deauthenticated (Reason: 1)
Apr 30 11:12:06 peter-laptop kernel: [  113.444124] mac80211-phy0: failed to remove key (0, f541ca04) from hardware (-22)
Apr 30 11:12:07 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Apr 30 11:12:07 peter-laptop kernel: [  114.440269] wlan0: direct probe to AP f7ac9684 try 1
Apr 30 11:12:07 peter-laptop kernel: [  114.443272] wlan0 direct probe responded
Apr 30 11:12:07 peter-laptop kernel: [  114.443285] wlan0: authenticate with AP f7ac9684
Apr 30 11:12:07 peter-laptop kernel: [  114.445071] wlan0: authenticated
Apr 30 11:12:07 peter-laptop kernel: [  114.445081] wlan0: associate with AP f7ac9684
Apr 30 11:12:07 peter-laptop kernel: [  114.447744] wlan0: RX ReassocResp from f4b28016 (capab=0x431 status=0 aid=1)
Apr 30 11:12:07 peter-laptop kernel: [  114.447755] wlan0: associated
Apr 30 11:12:07 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 4 
Apr 30 11:12:08 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 5 
Apr 30 11:12:08 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 6 
Apr 30 11:12:08 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7 
Apr 30 11:12:11 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 0 
Apr 30 11:12:11 peter-laptop kernel: [  118.274778] wlan0: deauthenticated (Reason: 1)
Apr 30 11:12:11 peter-laptop kernel: [  118.277117] mac80211-phy0: failed to remove key (0, f541e604) from hardware (-22)
Apr 30 11:12:11 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Apr 30 11:12:12 peter-laptop kernel: [  119.272142] wlan0: direct probe to AP f7ac9684 try 1
Apr 30 11:12:12 peter-laptop kernel: [  119.275125] wlan0 direct probe responded
Apr 30 11:12:12 peter-laptop kernel: [  119.275137] wlan0: authenticate with AP f7ac9684
Apr 30 11:12:12 peter-laptop kernel: [  119.277026] wlan0: authenticated
Apr 30 11:12:12 peter-laptop kernel: [  119.277035] wlan0: associate with AP f7ac9684
Apr 30 11:12:12 peter-laptop kernel: [  119.279679] wlan0: RX ReassocResp from f5bdc016 (capab=0x431 status=0 aid=1)
Apr 30 11:12:12 peter-laptop kernel: [  119.279689] wlan0: associated
Apr 30 11:12:12 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 4 
Apr 30 11:12:12 peter-laptop kernel: [  119.424095] wlan0: no IPv6 routers present
Apr 30 11:12:13 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 5 
Apr 30 11:12:13 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 6 
Apr 30 11:12:13 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7 
Apr 30 11:12:14 peter-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Apr 30 11:12:16 peter-laptop kernel: [  123.108401] wlan0: deauthenticated (Reason: 1)
Apr 30 11:12:16 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 0 
Apr 30 11:12:16 peter-laptop kernel: [  123.117125] mac80211-phy0: failed to remove key (0, f48ad204) from hardware (-22)
Apr 30 11:12:16 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Apr 30 11:12:17 peter-laptop kernel: [  124.109051] wlan0: direct probe to AP f7ac9684 try 1
Apr 30 11:12:17 peter-laptop kernel: [  124.111986] wlan0 direct probe responded
Apr 30 11:12:17 peter-laptop kernel: [  124.111992] wlan0: authenticate with AP f7ac9684
Apr 30 11:12:17 peter-laptop kernel: [  124.113896] wlan0: authenticated
Apr 30 11:12:17 peter-laptop kernel: [  124.113902] wlan0: associate with AP f7ac9684
Apr 30 11:12:17 peter-laptop kernel: [  124.116542] wlan0: RX ReassocResp from f5f10016 (capab=0x431 status=0 aid=1)
Apr 30 11:12:17 peter-laptop kernel: [  124.116548] wlan0: associated
Apr 30 11:12:17 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 4 
Apr 30 11:12:17 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 5 
Apr 30 11:12:17 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 6 
Apr 30 11:12:17 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7 
Apr 30 11:12:21 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 0 
Apr 30 11:12:21 peter-laptop kernel: [  127.942335] wlan0: deauthenticated (Reason: 1)
Apr 30 11:12:21 peter-laptop kernel: [  127.948120] mac80211-phy0: failed to remove key (0, f48ada04) from hardware (-22)
Apr 30 11:12:21 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Apr 30 11:12:22 peter-laptop kernel: [  128.940057] wlan0: direct probe to AP f7ac9684 try 1
Apr 30 11:12:22 peter-laptop kernel: [  128.942988] wlan0 direct probe responded
Apr 30 11:12:22 peter-laptop kernel: [  128.942992] wlan0: authenticate with AP f7ac9684
Apr 30 11:12:22 peter-laptop kernel: [  128.944721] wlan0: authenticated
Apr 30 11:12:22 peter-laptop kernel: [  128.944725] wlan0: associate with AP f7ac9684
Apr 30 11:12:22 peter-laptop kernel: [  128.949834] wlan0: RX ReassocResp from f49d0016 (capab=0x431 status=0 aid=1)
Apr 30 11:12:22 peter-laptop kernel: [  128.949839] wlan0: associated
Apr 30 11:12:22 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 4 
Apr 30 11:12:22 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 5 
Apr 30 11:12:22 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 6 
Apr 30 11:12:22 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7 
Apr 30 11:12:26 peter-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Apr 30 11:12:26 peter-laptop kernel: [  132.776032] wlan0: deauthenticated (Reason: 1)
Apr 30 11:12:26 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 0 
Apr 30 11:12:26 peter-laptop kernel: [  132.780113] mac80211-phy0: failed to remove key (0, f48aca04) from hardware (-22)
Apr 30 11:12:26 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Apr 30 11:12:27 peter-laptop kernel: [  133.776288] wlan0: direct probe to AP f7ac9684 try 1
Apr 30 11:12:27 peter-laptop kernel: [  133.779262] wlan0 direct probe responded
Apr 30 11:12:27 peter-laptop kernel: [  133.779274] wlan0: authenticate with AP f7ac9684
Apr 30 11:12:27 peter-laptop kernel: [  133.781210] wlan0: authenticated
Apr 30 11:12:27 peter-laptop kernel: [  133.781220] wlan0: associate with AP f7ac9684
Apr 30 11:12:27 peter-laptop kernel: [  133.784024] wlan0: RX ReassocResp from f5f94016 (capab=0x431 status=0 aid=1)
Apr 30 11:12:27 peter-laptop kernel: [  133.784036] wlan0: associated
Apr 30 11:12:27 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 4 
Apr 30 11:12:27 peter-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 5 
Apr 30 11:12:34 peter-laptop NetworkManager: <info>  Device 'wlan0' DHCP transaction took too long (>45s), stopping it. 
Apr 30 11:12:34 peter-laptop NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 6183 
Apr 30 11:12:34 peter-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Apr 30 11:12:34 peter-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) started... 
Apr 30 11:12:34 peter-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 9 
Apr 30 11:12:34 peter-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (skynet) 
Apr 30 11:12:34 peter-laptop NetworkManager: <info>  Marking connection 'Auto skynet' invalid. 
Apr 30 11:12:34 peter-laptop NetworkManager: <info>  Activation (wlan0) failed. 
Apr 30 11:12:34 peter-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) complete. 
Apr 30 11:12:34 peter-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 
Apr 30 11:12:34 peter-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 
Apr 30 11:12:34 peter-laptop kernel: [  140.848966] wlan0: disassociating by local choice (reason=3)
```

---

### Post by LittleAmok on 2009-05-01
Hi,

It seems that 5100 cards are rather buggy with 11n-mode.

You can always try to fetch more recent modules on : 

[http://linuxwireless.org/en/users/Download]("http://linuxwireless.org/en/users/Download")


Besides,you can always load the modules without 11n-mode

```
sudo modprobe iwlagn 11n_disable=1 11n_disable50=1
```


You can always see the troubleshooting of the driver at :

[http://www.intellinuxwireless.org/]("http://www.intellinuxwireless.org/")


Good luck

---

