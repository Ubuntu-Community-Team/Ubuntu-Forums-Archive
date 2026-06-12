---
title: "wep key ? problem with Network Manager 0.7"
date: 2009-02-14
forum: Networking &amp; Wireless
---

### Post by misha680 on 2009-02-14
Can't seem to connect anymore with a system setting. /var/log/syslog:

```

Feb 13 07:50:10 misha-d630 NetworkManager: <info>  starting... 
Feb 13 07:50:10 misha-d630 NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch 
Feb 13 07:50:10 misha-d630 NetworkManager: <info>  eth0: driver is 'tg3'. 
Feb 13 07:50:10 misha-d630 NetworkManager: <info>  Found new Ethernet device 'eth0'. 
Feb 13 07:50:10 misha-d630 NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_1c_23_2e_2b_51 
Feb 13 07:50:10 misha-d630 NetworkManager: <info>  wlan0: driver is 'iwl3945'. 
Feb 13 07:50:10 misha-d630 NetworkManager: <info>  wlan0: driver supports SSID scans (scan_capa 0x01). 
Feb 13 07:50:10 misha-d630 NetworkManager: <info>  Found new 802.11 WiFi device 'wlan0'. 
Feb 13 07:50:10 misha-d630 NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_1c_bf_7a_00_f3 
Feb 13 07:50:10 misha-d630 NetworkManager: <info>  Trying to start the supplicant... 
Feb 13 07:50:10 misha-d630 NetworkManager: <info>  Trying to start the system settings daemon... 
Feb 13 07:50:10 misha-d630 nm-system-settings:    SCPlugin-Ifupdown: init!
Feb 13 07:50:10 misha-d630 nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Feb 13 07:50:10 misha-d630 nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Feb 13 07:50:10 misha-d630 nm-system-settings:    SCPlugin-Ifupdown: devices added (udi: /org/freedesktop/Hal/devices/net_00_1c_23_2e_2b_51, iface: eth0)
Feb 13 07:50:10 misha-d630 nm-system-settings:    SCPlugin-Ifupdown: devices added (udi: /org/freedesktop/Hal/devices/net_00_1c_bf_7a_00_f3, iface: wlan0)
Feb 13 07:50:10 misha-d630 nm-system-settings:    SCPlugin-Ifupdown: end _init.
Feb 13 07:50:10 misha-d630 nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Feb 13 07:50:10 misha-d630 nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Feb 13 07:50:10 misha-d630 nm-system-settings:    SCPlugin-Ifupdown: (6438080) ... get_connections.
Feb 13 07:50:10 misha-d630 nm-system-settings:    SCPlugin-Ifupdown: (6438080) connections count: 0
Feb 13 07:50:10 misha-d630 NetworkManager: <WARN>  killswitch_getpower_reply(): Error getting killswitch power: Access type not supported. 
Feb 13 07:50:10 misha-d630 NetworkManager: <info>  (wlan0): supplicant manager is now in state 1 (from 0). 
Feb 13 07:50:10 misha-d630 nm-system-settings:    Ifupdown: get unmanaged devices count: 0
Feb 13 07:50:12 misha-d630 anacron[6818]: Anacron 2.3 started on 2009-02-13
Feb 13 07:50:12 misha-d630 anacron[6818]: Normal exit (0 jobs run)
Feb 13 07:50:12 misha-d630 /usr/sbin/cron[6848]: (CRON) INFO (pidfile fd = 3)
Feb 13 07:50:12 misha-d630 /usr/sbin/cron[6849]: (CRON) STARTUP (fork ok)
Feb 13 07:50:12 misha-d630 /usr/sbin/cron[6849]: (CRON) INFO (Running @reboot jobs)
Feb 13 07:50:14 misha-d630 NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Feb 13 07:50:14 misha-d630 NetworkManager: <info>  (eth0): bringing up device. 
Feb 13 07:50:14 misha-d630 vmnetBridge: RTM_NEWLINK: name:eth0 index:2 flags:0x00001043 
Feb 13 07:50:14 misha-d630 kernel: [   52.514975] /dev/vmnet: open called by PID 5543 (vmnet-bridge)
Feb 13 07:50:14 misha-d630 kernel: [   52.514983] /dev/vmnet: hub 0 does not exist, allocating memory.
Feb 13 07:50:14 misha-d630 kernel: [   52.514990] /dev/vmnet: port on hub 0 successfully opened
Feb 13 07:50:14 misha-d630 kernel: [   52.515003] bridge-eth0: up
Feb 13 07:50:14 misha-d630 kernel: [   52.518876] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 13 07:50:14 misha-d630 vmnetBridge: Started bridge eth0 to virtual network 0. 
Feb 13 07:50:14 misha-d630 NetworkManager: <info>  (eth0): preparing device. 
Feb 13 07:50:14 misha-d630 vmnetBridge: RTM_NEWLINK: name:eth0 index:2 flags:0x00001003 
Feb 13 07:50:14 misha-d630 NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Feb 13 07:50:14 misha-d630 kernel: [   52.536549] bridge-eth0: attached
Feb 13 07:50:14 misha-d630 kernel: [   52.536605] bridge-eth0: disabling the bridge
Feb 13 07:50:14 misha-d630 NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Feb 13 07:50:14 misha-d630 NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Feb 13 07:50:14 misha-d630 NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
Feb 13 07:50:14 misha-d630 NetworkManager: <info>  (wlan0): bringing up device. 
Feb 13 07:50:14 misha-d630 kernel: [   52.537193] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Feb 13 07:50:14 misha-d630 kernel: [   52.537321] PM: Writing back config space on device 0000:0c:00.0 at offset 1 (was 100102, writing 100106)
Feb 13 07:50:14 misha-d630 vmnetBridge: Stopped bridge eth0 to virtual network 0. 
Feb 13 07:50:14 misha-d630 kernel: [   52.556099] bridge-eth0: down
Feb 13 07:50:14 misha-d630 kernel: [   52.556109] bridge-eth0: detached
Feb 13 07:50:14 misha-d630 nm-system-settings: Adding default connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_1c_23_2e_2b_51
Feb 13 07:50:14 misha-d630 kernel: [   52.672738] vmnet1: no IPv6 routers present
Feb 13 07:50:14 misha-d630 kernel: [   52.680112] Registered led device: iwl-phy0:radio
Feb 13 07:50:14 misha-d630 kernel: [   52.680127] Registered led device: iwl-phy0:assoc
Feb 13 07:50:14 misha-d630 kernel: [   52.680142] Registered led device: iwl-phy0:RX
Feb 13 07:50:14 misha-d630 kernel: [   52.680155] Registered led device: iwl-phy0:TX
Feb 13 07:50:14 misha-d630 vmnetBridge: RTM_NEWLINK: name:wlan0 index:4 flags:0x00001043 
Feb 13 07:50:14 misha-d630 kernel: [   52.733092] /dev/vmnet: open called by PID 5543 (vmnet-bridge)
Feb 13 07:50:14 misha-d630 kernel: [   52.733101] /dev/vmnet: hub 0 does not exist, allocating memory.
Feb 13 07:50:14 misha-d630 kernel: [   52.733108] /dev/vmnet: port on hub 0 successfully opened
Feb 13 07:50:14 misha-d630 kernel: [   52.733116] bridge-wlan0: is a Wireless Adapter
Feb 13 07:50:14 misha-d630 kernel: [   52.733119] bridge-wlan0: up
Feb 13 07:50:14 misha-d630 vmnetBridge: Started bridge wlan0 to virtual network 0. 
Feb 13 07:50:14 misha-d630 NetworkManager: <info>  (wlan0): preparing device. 
Feb 13 07:50:14 misha-d630 NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
Feb 13 07:50:14 misha-d630 kernel: [   52.736424] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 13 07:50:14 misha-d630 kernel: [   52.736455] bridge-wlan0: attached
Feb 13 07:50:14 misha-d630 NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
Feb 13 07:50:14 misha-d630 NetworkManager: <info>  (eth0): device state change: 2 -> 3 
Feb 13 07:50:14 misha-d630 NetworkManager: <info>  (eth0): carrier now OFF (device state 3) 
Feb 13 07:50:14 misha-d630 NetworkManager: <info>  (eth0): device state change: 3 -> 2 
Feb 13 07:50:14 misha-d630 NetworkManager: <info>  (eth0): deactivating device (reason: 0). 
Feb 13 07:50:14 misha-d630 NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
Feb 13 07:50:14 misha-d630 kernel: [   52.755868] bridge-wlan0: disabling the bridge
Feb 13 07:50:14 misha-d630 vmnetBridge: RTM_NEWLINK: name:wlan0 index:4 flags:0x00001003 
Feb 13 07:50:14 misha-d630 vmnetBridge: Stopped bridge wlan0 to virtual network 0. 
Feb 13 07:50:14 misha-d630 kernel: [   52.780513] bridge-wlan0: down
Feb 13 07:50:14 misha-d630 kernel: [   52.780616] bridge-wlan0: detached
Feb 13 07:50:14 misha-d630 kernel: [   52.916944] NET: Registered protocol family 17
Feb 13 07:50:14 misha-d630 kernel: [   52.956027] vmnet8: no IPv6 routers present
Feb 13 07:50:14 misha-d630 NetworkManager: <info>  (wlan0): supplicant interface state change: 1 -> 2. 
Feb 13 07:50:15 misha-d630 vmnetBridge: RTM_NEWLINK: name:wlan0 index:4 flags:0x00001003 
Feb 13 07:50:15 misha-d630 vmnetBridge: Can't remove interface wlan0 4 (does not exist). 
Feb 13 07:50:17 misha-d630 kernel: [   54.790425] wlan0: Initial auth_alg=0
Feb 13 07:50:17 misha-d630 kernel: [   54.790436] wlan0: direct probe to AP 00:1f:33:d1:b6:c0 try 1
Feb 13 07:50:17 misha-d630 kernel: [   54.793292] wlan0 direct probe responded
Feb 13 07:50:17 misha-d630 kernel: [   54.793300] wlan0: authenticate with AP 00:1f:33:d1:b6:c0
Feb 13 07:50:17 misha-d630 kernel: [   54.795081] wlan0: RX authentication from 00:1f:33:d1:b6:c0 (alg=0 transaction=2 status=0)
Feb 13 07:50:17 misha-d630 kernel: [   54.795088] wlan0: authenticated
Feb 13 07:50:17 misha-d630 kernel: [   54.795092] wlan0: associate with AP 00:1f:33:d1:b6:c0
Feb 13 07:50:17 misha-d630 kernel: [   54.798312] wlan0: RX AssocResp from 00:1f:33:d1:b6:c0 (capab=0x421 status=0 aid=1)
Feb 13 07:50:17 misha-d630 kernel: [   54.798319] wlan0: associated
Feb 13 07:50:17 misha-d630 kernel: [   54.798334] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 txop=0
Feb 13 07:50:17 misha-d630 kernel: [   54.800430] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 txop=0
Feb 13 07:50:17 misha-d630 kernel: [   54.800548] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 txop=94
Feb 13 07:50:17 misha-d630 kernel: [   54.800648] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 txop=47
Feb 13 07:50:17 misha-d630 kernel: [   54.800780] wlan0: CTS protection enabled (BSSID=00:1f:33:d1:b6:c0)
Feb 13 07:50:17 misha-d630 kernel: [   54.800786] wlan0: switched to short barker preamble (BSSID=00:1f:33:d1:b6:c0)
Feb 13 07:50:17 misha-d630 vmnetBridge: RTM_NEWLINK: name:wlan0 index:4 flags:0x00011003 
Feb 13 07:50:17 misha-d630 vmnetBridge: Can't remove interface wlan0 4 (does not exist). 
Feb 13 07:50:17 misha-d630 kernel: [   54.812226] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Feb 13 07:50:17 misha-d630 kernel: [   54.812786] wlan0: disassociate(reason=3)
Feb 13 07:50:17 misha-d630 NetworkManager: <info>  Activation (wlan0) starting connection 'misha' 
Feb 13 07:50:17 misha-d630 NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Feb 13 07:50:17 misha-d630 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Feb 13 07:50:17 misha-d630 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Feb 13 07:50:17 misha-d630 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Feb 13 07:50:17 misha-d630 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Feb 13 07:50:17 misha-d630 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Feb 13 07:50:17 misha-d630 NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Feb 13 07:50:17 misha-d630 NetworkManager: <info>  Activation (wlan0/wireless): access point 'misha' has security, but secrets are required. 
Feb 13 07:50:17 misha-d630 NetworkManager: <info>  (wlan0): device state change: 5 -> 6 
Feb 13 07:50:17 misha-d630 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Feb 13 07:50:17 misha-d630 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Feb 13 07:50:17 misha-d630 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Feb 13 07:50:17 misha-d630 NetworkManager: <info>  (wlan0): device state change: 6 -> 4 
Feb 13 07:50:17 misha-d630 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Feb 13 07:50:17 misha-d630 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Feb 13 07:50:17 misha-d630 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Feb 13 07:50:17 misha-d630 NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Feb 13 07:50:17 misha-d630 NetworkManager: <info>  Activation (wlan0/wireless): connection 'misha' has security, and secrets exist.  No new secrets needed. 
Feb 13 07:50:17 misha-d630 NetworkManager: <info>  Config: added 'ssid' value 'misha' 
Feb 13 07:50:17 misha-d630 NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Feb 13 07:50:17 misha-d630 NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Feb 13 07:50:17 misha-d630 NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Feb 13 07:50:17 misha-d630 NetworkManager: <info>  Config: added 'proto' value 'WPA RSN' 
Feb 13 07:50:17 misha-d630 NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP' 
Feb 13 07:50:17 misha-d630 NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP' 
Feb 13 07:50:17 misha-d630 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Feb 13 07:50:17 misha-d630 NetworkManager: <info>  Config: set interface ap_scan to 1 
Feb 13 07:50:18 misha-d630 vmnetBridge: RTM_NEWLINK: name:wlan0 index:4 flags:0x00001003 
Feb 13 07:50:18 misha-d630 vmnetBridge: Can't remove interface wlan0 4 (does not exist). 
Feb 13 07:50:19 misha-d630 avahi-daemon[5474]: Registering new address record for fe80::21c:bfff:fe7a:f3 on wlan0.*.
Feb 13 07:50:22 misha-d630 NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Feb 13 07:50:24 misha-d630 kernel: [   58.162455] wlan0: RX deauthentication from 00:1f:33:d1:b6:c0 (reason=6)
Feb 13 07:50:24 misha-d630 kernel: [   58.162465] wlan0: deauthenticated
Feb 13 07:50:24 misha-d630 kernel: [   58.162491] wlan0: RX deauthentication from 00:1f:33:d1:b6:c0 (reason=6)
Feb 13 07:50:24 misha-d630 kernel: [   58.162516] wlan0: RX deauthentication from 00:1f:33:d1:b6:c0 (reason=6)
Feb 13 07:50:24 misha-d630 kernel: [   58.162536] wlan0: RX deauthentication from 00:1f:33:d1:b6:c0 (reason=6)
Feb 13 07:50:24 misha-d630 kernel: [   58.162558] wlan0: RX deauthentication from 00:1f:33:d1:b6:c0 (reason=6)
Feb 13 07:50:24 misha-d630 kernel: [   58.162578] wlan0: RX deauthentication from 00:1f:33:d1:b6:c0 (reason=6)
Feb 13 07:50:24 misha-d630 NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Feb 13 07:50:24 misha-d630 kernel: [   58.162598] wlan0: direct probe to AP 00:1f:33:d1:b6:c0 try 1
Feb 13 07:50:24 misha-d630 kernel: [   58.164541] wlan0: RX deauthentication from 00:1f:33:d1:b6:c0 (reason=6)
Feb 13 07:50:24 misha-d630 kernel: [   58.169654] wlan0 direct probe responded
Feb 13 07:50:24 misha-d630 NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 0 
Feb 13 07:50:24 misha-d630 kernel: [   58.169663] wlan0: authenticate with AP 00:1d:60:df:f5:3e
Feb 13 07:50:24 misha-d630 kernel: [   58.172673] wlan0: Initial auth_alg=0
Feb 13 07:50:24 misha-d630 kernel: [   58.172685] wlan0: authenticate with AP 00:1d:60:df:f5:3e
Feb 13 07:50:24 misha-d630 kernel: [   58.172721] wlan0: RX authentication from 00:1d:60:df:f5:3e (alg=0 transaction=2 status=0)
Feb 13 07:50:24 misha-d630 kernel: [   58.172727] wlan0: authenticated
Feb 13 07:50:24 misha-d630 kernel: [   58.172731] wlan0: associate with AP 00:1d:60:df:f5:3e
Feb 13 07:50:24 misha-d630 kernel: [   58.174532] wlan0: authentication frame received from 00:1d:60:df:f5:3e, but not in authenticate state - ignored
Feb 13 07:50:24 misha-d630 kernel: [   58.175487] wlan0: authentication frame received from 00:1d:60:df:f5:3e, but not in authenticate state - ignored
Feb 13 07:50:24 misha-d630 kernel: [   58.177056] wlan0: RX AssocResp from 00:1d:60:df:f5:3e (capab=0x411 status=0 aid=2)
Feb 13 07:50:24 misha-d630 kernel: [   58.177065] wlan0: associated
Feb 13 07:50:24 misha-d630 kernel: [   58.177088] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 txop=0
Feb 13 07:50:24 misha-d630 kernel: [   58.177095] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 txop=0
Feb 13 07:50:24 misha-d630 kernel: [   58.177101] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 txop=94
Feb 13 07:50:24 misha-d630 kernel: [   58.177107] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 txop=47
Feb 13 07:50:24 misha-d630 kernel: [   58.177119] wlan0: switched to short barker preamble (BSSID=00:1d:60:df:f5:3e)
Feb 13 07:50:24 misha-d630 NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 4 
Feb 13 07:50:24 misha-d630 vmnetBridge: RTM_NEWLINK: name:wlan0 index:4 flags:0x00011003 
Feb 13 07:50:24 misha-d630 vmnetBridge: Can't remove interface wlan0 4 (does not exist). 
Feb 13 07:50:25 misha-d630 NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 5 
Feb 13 07:50:26 misha-d630 NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 6 
Feb 13 07:50:26 misha-d630 NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7 
Feb 13 07:50:26 misha-d630 NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'misha'. 
Feb 13 07:50:26 misha-d630 NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Feb 13 07:50:26 misha-d630 NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Feb 13 07:50:26 misha-d630 NetworkManager: <info>  (wlan0): device state change: 5 -> 7 
Feb 13 07:50:26 misha-d630 NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Feb 13 07:50:26 misha-d630 vmnetBridge: RTM_NEWLINK: name:wlan0 index:4 flags:0x00011043 
Feb 13 07:50:26 misha-d630 vmnetBridge: Started bridge wlan0 to virtual network 0. 
Feb 13 07:50:26 misha-d630 kernel: [   58.428705] /dev/vmnet: open called by PID 5543 (vmnet-bridge)
Feb 13 07:50:26 misha-d630 kernel: [   58.428725] /dev/vmnet: hub 0 does not exist, allocating memory.
Feb 13 07:50:26 misha-d630 kernel: [   58.428749] /dev/vmnet: port on hub 0 successfully opened
Feb 13 07:50:26 misha-d630 kernel: [   58.428767] bridge-wlan0: is a Wireless Adapter
Feb 13 07:50:26 misha-d630 kernel: [   58.428777] bridge-wlan0: up
Feb 13 07:50:26 misha-d630 kernel: [   58.428783] bridge-wlan0: attached
Feb 13 07:50:26 misha-d630 NetworkManager: <info>  dhclient started with pid 7329 
Feb 13 07:50:26 misha-d630 NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Feb 13 07:50:26 misha-d630 dhclient: Internet Systems Consortium DHCP Client V3.0.6
Feb 13 07:50:26 misha-d630 dhclient: Copyright 2004-2007 Internet Systems Consortium.
Feb 13 07:50:26 misha-d630 dhclient: All rights reserved.
Feb 13 07:50:26 misha-d630 dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Feb 13 07:50:26 misha-d630 dhclient: 
Feb 13 07:50:26 misha-d630 dhclient: wmaster0: unknown hardware address type 801
Feb 13 07:50:26 misha-d630 dhclient: wmaster0: unknown hardware address type 801
Feb 13 07:50:26 misha-d630 NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit 
Feb 13 07:50:26 misha-d630 dhclient: Listening on LPF/wlan0/00:1c:bf:7a:00:f3
Feb 13 07:50:26 misha-d630 dhclient: Sending on   LPF/wlan0/00:1c:bf:7a:00:f3
Feb 13 07:50:26 misha-d630 dhclient: Sending on   Socket/fallback
Feb 13 07:50:28 misha-d630 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Feb 13 07:50:28 misha-d630 dhclient: DHCPOFFER of 192.168.1.50 from 192.168.1.1
Feb 13 07:50:28 misha-d630 dhclient: DHCPREQUEST of 192.168.1.50 on wlan0 to 255.255.255.255 port 67
Feb 13 07:50:28 misha-d630 dhclient: DHCPACK of 192.168.1.50 from 192.168.1.1
Feb 13 07:50:28 misha-d630 NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> bound 
Feb 13 07:50:28 misha-d630 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
Feb 13 07:50:28 misha-d630 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
Feb 13 07:50:28 misha-d630 dhclient: bound to 192.168.1.50 -- renewal in 20368 seconds.
Feb 13 07:50:28 misha-d630 NetworkManager: <info>    address 192.168.1.50 
Feb 13 07:50:28 misha-d630 NetworkManager: <info>    prefix 24 (255.255.255.0) 
Feb 13 07:50:28 misha-d630 NetworkManager: <info>    gateway 192.168.1.1 
Feb 13 07:50:28 misha-d630 NetworkManager: <info>    hostname 'misha-d630' 
Feb 13 07:50:28 misha-d630 NetworkManager: <info>    nameserver '192.168.1.1' 
Feb 13 07:50:28 misha-d630 NetworkManager: <info>    domain name 'lan' 
Feb 13 07:50:28 misha-d630 NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Feb 13 07:50:28 misha-d630 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
Feb 13 07:50:28 misha-d630 NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Feb 13 07:50:28 misha-d630 avahi-daemon[5474]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.50.
Feb 13 07:50:28 misha-d630 kernel: [   58.591758] wlan0: no IPv6 routers present
Feb 13 07:50:28 misha-d630 avahi-daemon[5474]: New relevant interface wlan0.IPv4 for mDNS.
Feb 13 07:50:28 misha-d630 avahi-daemon[5474]: Registering new address record for 192.168.1.50 on wlan0.IPv4.
Feb 13 07:50:29 misha-d630 NetworkManager: <info>  (wlan0): device state change: 7 -> 8 
Feb 13 07:50:29 misha-d630 NetworkManager: <info>  (wlan0): writing resolv.conf to /sbin/resolvconf 
Feb 13 07:50:30 misha-d630 NetworkManager: <info>  Policy set 'misha' (wlan0) as default for routing and DNS. 
Feb 13 07:50:30 misha-d630 NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Feb 13 07:50:30 misha-d630 NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Feb 13 07:50:30 misha-d630 nm-dispatcher.action: nm_dispatcher_action: Invalid connection: 'NMSettingWirelessSecurity' / 'wep-key0' invalid: 1

```

I think problem is here?
```

Feb 13 07:50:30 misha-d630 nm-dispatcher.action: nm_dispatcher_action: Invalid connection: 'NMSettingWirelessSecurity' / 'wep-key0' invalid: 1

```

Thank you
Misha

p.s. Oh and I'm using nm 0.7 on hardy.

---

### Post by SeanTater on 2009-02-14
I'm not exactly sure what is wrong, but it looks like the wrong wep key was typed in.
Try looking at this: ```
sudo iwlist key
```
Don't post the output, but you should see your network key in there. If not, do this:
```
sudo iwconfig <your network interface> key <uour key in hex>
```
With, of course, the <>'s replaced with their values. If you don't know which interface it is, this command should tell you:
```
iwlist channel 2>&1 | grep channels | cut -d' ' -f 1
```

---

### Post by misha680 on 2009-02-14
> **SeanTater said:**
> I'm not exactly sure what is wrong, but it looks like the wrong wep key was typed in.
Try looking at this: ```
sudo iwlist key
```
Don't post the output, but you should see your network key in there. If not, do this:
```
sudo iwconfig <your network interface> key <uour key in hex>
```
With, of course, the <>'s replaced with their values. If you don't know which interface it is, this command should tell you:
```
iwlist channel 2>&1 | grep channels | cut -d' ' -f 1
```

Hey thanks. Actually that makes me realize something... my network is WPA2 personal not WEP. But the weird thing is the profile used to work before... any ideas?

Also its an iwl3945 card and I am using the linux-backports-modules drivers because the default ones seem to have some probs with wpa supplicant. Not sure if that helps/hurts.

Thanks
Misha

p.s. Notably, my connection doesn't seem to work on my two computers with iwl3945 and iwl4965 right now, but works fine on one with ipw2100. I can check system settings on there later on.

---

