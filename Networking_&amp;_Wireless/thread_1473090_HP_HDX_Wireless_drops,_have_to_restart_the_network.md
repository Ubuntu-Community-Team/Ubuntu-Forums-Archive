---
title: "HP HDX Wireless drops, have to restart the network manager"
date: 2010-05-04
forum: Networking &amp; Wireless
---

### Post by cyrilg on 2010-05-04
Hi all,

I've been quite happy with Ubuntu 9.10 on my HP HDX-16 for the last months. However, something started happening about a month ago or so. While I am using the internet all of a sudden my connection drops. The network manager shows as if its trying to reconnect, but is never able to do so on its own. For a while I had to restart the laptop, until I found that restarting the network manager did the trick. However this is getting very annoying. One particular thing that I found is that this happens most often while speaking with people on Skype, in fact almost every call over 10-20 minutes eventually makes my network drop, and I have to restart networking and re dial my call.

Here is some system info:

```
wlan0     IEEE 802.11abgn  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:4D:57:21:92   
          Bit Rate=18 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  Noise level=-84 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]

```

```
*-network               
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 00
       serial: 00:22:fa:42:2f:be
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.2 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:32 memory:dc000000-dc001fff

```


and then from syslog whenever this happens I get this transcript:

```
May  4 14:19:22 orangetree wpa_supplicant[1066]: CTRL-EVENT-SCAN-RESULTS 
May  4 14:19:28 orangetree wpa_supplicant[1066]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
May  4 14:19:28 orangetree kernel: [20042.471299] wlan0: no probe response from AP 00:18:4d:57:21:92 - disassociating
May  4 14:19:28 orangetree NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
May  4 14:19:28 orangetree NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
May  4 14:19:29 orangetree kernel: [20043.070051] iwlagn 0000:02:00.0: Error sending REPLY_RXON: time out after 500ms.
May  4 14:19:29 orangetree kernel: [20043.070062] iwlagn 0000:02:00.0: Error setting new RXON (-110)
May  4 14:19:29 orangetree wpa_supplicant[1066]: CTRL-EVENT-SCAN-RESULTS 
May  4 14:19:29 orangetree kernel: [20043.571321] iwlagn 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 500ms.
May  4 14:19:30 orangetree kernel: [20044.071307] iwlagn 0000:02:00.0: Error sending REPLY_RXON: time out after 500ms.
May  4 14:19:30 orangetree kernel: [20044.071318] iwlagn 0000:02:00.0: Error setting new RXON (-110)
May  4 14:19:30 orangetree kernel: [20044.571303] iwlagn 0000:02:00.0: Error sending REPLY_RXON: time out after 500ms.
May  4 14:19:30 orangetree kernel: [20044.571314] iwlagn 0000:02:00.0: Error setting new RXON (-110)
May  4 14:19:35 orangetree kernel: [20049.070047] iwlagn 0000:02:00.0: Error sending REPLY_RXON: time out after 500ms.
May  4 14:19:35 orangetree kernel: [20049.070059] iwlagn 0000:02:00.0: Error setting new RXON (-110)
May  4 14:19:35 orangetree wpa_supplicant[1066]: CTRL-EVENT-SCAN-RESULTS 
May  4 14:19:35 orangetree kernel: [20049.576161] iwlagn 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 500ms.
May  4 14:19:36 orangetree kernel: [20050.071305] iwlagn 0000:02:00.0: Error sending REPLY_RXON: time out after 500ms.
May  4 14:19:36 orangetree kernel: [20050.071317] iwlagn 0000:02:00.0: Error setting new RXON (-110)
May  4 14:19:36 orangetree kernel: [20050.571345] iwlagn 0000:02:00.0: Error sending REPLY_RXON: time out after 500ms.
May  4 14:19:36 orangetree kernel: [20050.571356] iwlagn 0000:02:00.0: Error setting new RXON (-110)
May  4 14:19:41 orangetree kernel: [20055.070090] iwlagn 0000:02:00.0: Error sending REPLY_RXON: time out after 500ms.
May  4 14:19:41 orangetree kernel: [20055.070102] iwlagn 0000:02:00.0: Error setting new RXON (-110)
May  4 14:19:41 orangetree kernel: [20055.570119] iwlagn 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 500ms.
May  4 14:19:41 orangetree wpa_supplicant[1066]: CTRL-EVENT-SCAN-RESULTS 
May  4 14:19:42 orangetree kernel: [20056.071312] iwlagn 0000:02:00.0: Error sending REPLY_RXON: time out after 500ms.
May  4 14:19:42 orangetree kernel: [20056.071323] iwlagn 0000:02:00.0: Error setting new RXON (-110)
May  4 14:19:42 orangetree kernel: [20056.571310] iwlagn 0000:02:00.0: Error sending REPLY_RXON: time out after 500ms.
May  4 14:19:42 orangetree kernel: [20056.571321] iwlagn 0000:02:00.0: Error setting new RXON (-110)
May  4 14:19:44 orangetree NetworkManager: <info>  (wlan0): device state change: 8 -> 3 (reason 11)
May  4 14:19:44 orangetree NetworkManager: <info>  (wlan0): deactivating device (reason: 11).
May  4 14:19:44 orangetree NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 7031
May  4 14:19:44 orangetree NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
May  4 14:19:44 orangetree NetworkManager: <info>  Activation (wlan0) starting connection 'Auto NETGEAR'
May  4 14:19:44 orangetree NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
May  4 14:19:44 orangetree NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May  4 14:19:44 orangetree NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May  4 14:19:44 orangetree NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May  4 14:19:44 orangetree NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May  4 14:19:44 orangetree NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May  4 14:19:44 orangetree NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
May  4 14:19:44 orangetree NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto NETGEAR' has security, and secrets exist.  No new secrets needed.
May  4 14:19:44 orangetree avahi-daemon[908]: Withdrawing address record for 192.168.1.2 on wlan0.
May  4 14:19:44 orangetree avahi-daemon[908]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.2.
May  4 14:19:44 orangetree avahi-daemon[908]: Interface wlan0.IPv4 no longer relevant for mDNS.
May  4 14:19:44 orangetree NetworkManager: <info>  Config: added 'ssid' value 'NETGEAR'
May  4 14:19:44 orangetree NetworkManager: <info>  Config: added 'scan_ssid' value '1'
May  4 14:19:44 orangetree NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
May  4 14:19:44 orangetree NetworkManager: <info>  Config: added 'psk' value '<omitted>'
May  4 14:19:44 orangetree NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May  4 14:19:44 orangetree NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May  4 14:19:44 orangetree NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May  4 14:19:44 orangetree NetworkManager: <info>  Config: set interface ap_scan to 1
May  4 14:19:44 orangetree NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
May  4 14:19:46 orangetree NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
May  4 14:19:47 orangetree kernel: [20061.070744] iwlagn 0000:02:00.0: Error sending REPLY_RXON: time out after 500ms.
May  4 14:19:47 orangetree kernel: [20061.070755] iwlagn 0000:02:00.0: Error setting new RXON (-110)
May  4 14:19:47 orangetree wpa_supplicant[1066]: CTRL-EVENT-SCAN-RESULTS 
May  4 14:19:47 orangetree kernel: [20061.571346] iwlagn 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 500ms.
May  4 14:19:48 orangetree kernel: [20062.071350] iwlagn 0000:02:00.0: Error sending REPLY_RXON: time out after 500ms.
May  4 14:19:48 orangetree kernel: [20062.071361] iwlagn 0000:02:00.0: Error setting new RXON (-110)
May  4 14:19:48 orangetree kernel: [20062.571310] iwlagn 0000:02:00.0: Error sending REPLY_RXON: time out after 500ms.
May  4 14:19:48 orangetree kernel: [20062.571321] iwlagn 0000:02:00.0: Error setting new RXON (-110)
May  4 14:19:53 orangetree kernel: [20067.071315] iwlagn 0000:02:00.0: Error sending REPLY_RXON: time out after 500ms.
May  4 14:19:53 orangetree kernel: [20067.071326] iwlagn 0000:02:00.0: Error setting new RXON (-110)
May  4 14:19:53 orangetree sudo: pam_sm_authenticate: Called
May  4 14:19:53 orangetree sudo: pam_sm_authenticate: username = [tech]
May  4 14:19:53 orangetree NetworkManager: <WARN>  nm_signal_handler(): Caught signal 15, shutting down normally.
May  4 14:19:53 orangetree NetworkManager: <info>  (wlan0): deactivating device (reason: 36).
May  4 14:19:53 orangetree NetworkManager: <info>  (wlan0): taking down device.
May  4 14:19:53 orangetree kernel: [20067.571551] iwlagn 0000:02:00.0: Error sending REPLY_SCAN_CMD: time out after 500ms.
May  4 14:19:53 orangetree kernel: [20067.571608] iwlagn 0000:02:00.0: No space for Tx
May  4 14:19:53 orangetree kernel: [20067.571615] iwlagn 0000:02:00.0: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
May  4 14:19:54 orangetree kernel: [20068.120974] iwlagn 0000:02:00.0: Error sending REPLY_RXON: time out after 500ms.
May  4 14:19:54 orangetree kernel: [20068.120985] iwlagn 0000:02:00.0: Error setting new RXON (-110)
May  4 14:19:54 orangetree NetworkManager: <info>  exiting (success)
May  4 14:19:54 orangetree avahi-daemon[908]: Withdrawing address record for fe80::222:faff:fe42:2fbe on wlan0.
May  4 14:19:54 orangetree NetworkManager: <info>  starting...
May  4 14:19:54 orangetree NetworkManager: <info>  modem-manager is now available
May  4 14:19:54 orangetree NetworkManager:    SCPlugin-Ifupdown: init!
May  4 14:19:54 orangetree NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
May  4 14:19:54 orangetree NetworkManager:    SCPluginIfupdown: guessed connection type (wlan0) = 802-3-ethernet
May  4 14:19:54 orangetree NetworkManager:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:wlan0, type:802-3-ethernet, id:Ifupdown (wlan0), uuid: 5391eba4-6426-faca-338e-5828034ff9d1
May  4 14:19:54 orangetree NetworkManager:    SCPlugin-Ifupdown: addresses count: 1
May  4 14:19:54 orangetree NetworkManager:    SCPlugin-Ifupdown: No dns-nameserver configured in /etc/network/interfaces
May  4 14:19:54 orangetree NetworkManager:    SCPlugin-Ifupdown: autoconnect
May  4 14:19:54 orangetree NetworkManager:    SCPluginIfupdown: management mode: managed
May  4 14:19:54 orangetree NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0, iface: wlan0)
May  4 14:19:54 orangetree NetworkManager:    SCPluginIfupdown: locking wired connection setting
May  4 14:19:54 orangetree NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wmaster0, iface: wmaster0)
May  4 14:19:54 orangetree NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wmaster0, iface: wmaster0): no ifupdown configuration found.
May  4 14:19:54 orangetree NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0, iface: eth0)
May  4 14:19:54 orangetree NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
May  4 14:19:54 orangetree NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
May  4 14:19:54 orangetree NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
May  4 14:19:54 orangetree NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/pan0, iface: pan0)
May  4 14:19:54 orangetree NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/pan0, iface: pan0): no ifupdown configuration found.
May  4 14:19:54 orangetree NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0)
May  4 14:19:54 orangetree NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0): no ifupdown configuration found.
May  4 14:19:54 orangetree NetworkManager:    SCPlugin-Ifupdown: end _init.
May  4 14:19:54 orangetree NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
May  4 14:19:54 orangetree NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
May  4 14:19:54 orangetree NetworkManager: <info>  Found radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/ieee80211/phy0/rfkill1) (driver <unknown>)
May  4 14:19:54 orangetree NetworkManager: <info>  Wireless now enabled by radio killswitch
May  4 14:19:54 orangetree NetworkManager:    SCPlugin-Ifupdown: (19915872) ... get_connections.
May  4 14:19:54 orangetree NetworkManager:    SCPlugin-Ifupdown: (19915872) connections count: 1
May  4 14:19:54 orangetree NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).
May  4 14:19:54 orangetree NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'iwlagn')
May  4 14:19:54 orangetree NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
May  4 14:19:54 orangetree NetworkManager: <info>  (wlan0): now managed
May  4 14:19:54 orangetree NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
May  4 14:19:54 orangetree NetworkManager: <info>  (wlan0): bringing up device.
May  4 14:19:54 orangetree kernel: [20068.444875] Registered led device: iwl-phy0::radio
May  4 14:19:54 orangetree kernel: [20068.444922] Registered led device: iwl-phy0::assoc
May  4 14:19:54 orangetree kernel: [20068.444963] Registered led device: iwl-phy0::RX
May  4 14:19:54 orangetree kernel: [20068.445002] Registered led device: iwl-phy0::TX
May  4 14:19:54 orangetree NetworkManager: <info>  (wlan0): preparing device.
May  4 14:19:54 orangetree NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
May  4 14:19:54 orangetree NetworkManager: <info>  (eth0): carrier is OFF
May  4 14:19:54 orangetree kernel: [20068.513343] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  4 14:19:54 orangetree NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
May  4 14:19:54 orangetree NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
May  4 14:19:54 orangetree NetworkManager: <info>  (eth0): now managed
May  4 14:19:54 orangetree NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
May  4 14:19:54 orangetree NetworkManager: <info>  (eth0): preparing device.
May  4 14:19:54 orangetree NetworkManager: <info>  (eth0): deactivating device (reason: 2).
May  4 14:19:54 orangetree NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0
May  4 14:19:54 orangetree NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/pan0: couldn't determine device driver; ignoring...
May  4 14:19:54 orangetree NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/vboxnet0: couldn't determine device driver; ignoring...
May  4 14:19:54 orangetree NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
May  4 14:19:54 orangetree NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
May  4 14:19:54 orangetree wpa_supplicant[1066]: Failed to initiate AP scan.
May  4 14:19:56 orangetree NetworkManager: <WARN>  nm_signal_handler(): Caught signal 15, shutting down normally.
May  4 14:19:56 orangetree NetworkManager: <info>  (wlan0): taking down device.
May  4 14:19:56 orangetree kernel: [20070.311465] wlan0: deauthenticating by local choice (reason=3)
May  4 14:19:56 orangetree NetworkManager: <info>  exiting (success)
May  4 14:19:56 orangetree NetworkManager: <info>  starting...
May  4 14:19:56 orangetree NetworkManager: <info>  modem-manager is now available
May  4 14:19:56 orangetree NetworkManager:    SCPlugin-Ifupdown: init!
May  4 14:19:56 orangetree NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
May  4 14:19:56 orangetree NetworkManager:    SCPluginIfupdown: guessed connection type (wlan0) = 802-3-ethernet
May  4 14:19:56 orangetree NetworkManager:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:wlan0, type:802-3-ethernet, id:Ifupdown (wlan0), uuid: 5391eba4-6426-faca-338e-5828034ff9d1
May  4 14:19:56 orangetree NetworkManager:    SCPlugin-Ifupdown: addresses count: 1
May  4 14:19:56 orangetree NetworkManager:    SCPlugin-Ifupdown: No dns-nameserver configured in /etc/network/interfaces
May  4 14:19:56 orangetree NetworkManager:    SCPlugin-Ifupdown: autoconnect
May  4 14:19:56 orangetree NetworkManager:    SCPluginIfupdown: management mode: managed
May  4 14:19:56 orangetree NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0, iface: wlan0)
May  4 14:19:56 orangetree NetworkManager:    SCPluginIfupdown: locking wired connection setting
May  4 14:19:56 orangetree NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wmaster0, iface: wmaster0)
May  4 14:19:56 orangetree NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wmaster0, iface: wmaster0): no ifupdown configuration found.
May  4 14:19:56 orangetree NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0, iface: eth0)
May  4 14:19:56 orangetree NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
May  4 14:19:56 orangetree NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
May  4 14:19:56 orangetree NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
May  4 14:19:56 orangetree NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/pan0, iface: pan0)
May  4 14:19:56 orangetree NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/pan0, iface: pan0): no ifupdown configuration found.
May  4 14:19:56 orangetree NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0)
May  4 14:19:56 orangetree NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0): no ifupdown configuration found.
May  4 14:19:56 orangetree NetworkManager:    SCPlugin-Ifupdown: end _init.
May  4 14:19:56 orangetree NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
May  4 14:19:56 orangetree NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
May  4 14:19:56 orangetree NetworkManager: <info>  Found radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/ieee80211/phy0/rfkill1) (driver <unknown>)
May  4 14:19:56 orangetree NetworkManager: <info>  Wireless now enabled by radio killswitch
May  4 14:19:56 orangetree NetworkManager:    SCPlugin-Ifupdown: (8442976) ... get_connections.
May  4 14:19:56 orangetree NetworkManager:    SCPlugin-Ifupdown: (8442976) connections count: 1
May  4 14:19:56 orangetree NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).
May  4 14:19:56 orangetree NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'iwlagn')
May  4 14:19:56 orangetree NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
May  4 14:19:56 orangetree NetworkManager: <info>  (wlan0): now managed
May  4 14:19:56 orangetree NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
May  4 14:19:56 orangetree NetworkManager: <info>  (wlan0): bringing up device.
May  4 14:19:57 orangetree kernel: [20070.736271] Registered led device: iwl-phy0::radio
May  4 14:19:57 orangetree kernel: [20070.736288] Registered led device: iwl-phy0::assoc
May  4 14:19:57 orangetree kernel: [20070.736302] Registered led device: iwl-phy0::RX
May  4 14:19:57 orangetree kernel: [20070.736317] Registered led device: iwl-phy0::TX
May  4 14:19:57 orangetree NetworkManager: <info>  (wlan0): preparing device.
May  4 14:19:57 orangetree NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
May  4 14:19:57 orangetree NetworkManager: <info>  (eth0): carrier is OFF
May  4 14:19:57 orangetree NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
May  4 14:19:57 orangetree NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
May  4 14:19:57 orangetree NetworkManager: <info>  (eth0): now managed
May  4 14:19:57 orangetree NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
May  4 14:19:57 orangetree NetworkManager: <info>  (eth0): preparing device.
May  4 14:19:57 orangetree NetworkManager: <info>  (eth0): deactivating device (reason: 2).
May  4 14:19:57 orangetree NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0
May  4 14:19:57 orangetree NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/pan0: couldn't determine device driver; ignoring...
May  4 14:19:57 orangetree NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/vboxnet0: couldn't determine device driver; ignoring...
May  4 14:19:57 orangetree kernel: [20070.780764] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  4 14:19:57 orangetree NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
May  4 14:19:57 orangetree NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
May  4 14:19:57 orangetree wpa_supplicant[1066]: CTRL-EVENT-SCAN-RESULTS 
May  4 14:19:57 orangetree wpa_supplicant[1066]: Failed to initiate AP scan.
May  4 14:19:57 orangetree NetworkManager: <info>  Activation (wlan0) starting connection 'Auto NETGEAR'
May  4 14:19:57 orangetree NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
May  4 14:19:57 orangetree NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May  4 14:19:57 orangetree NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May  4 14:19:57 orangetree NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May  4 14:19:57 orangetree NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May  4 14:19:57 orangetree NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May  4 14:19:57 orangetree NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
May  4 14:19:57 orangetree NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto NETGEAR' has security, and secrets exist.  No new secrets needed.
May  4 14:19:57 orangetree NetworkManager: <info>  Config: added 'ssid' value 'NETGEAR'
May  4 14:19:57 orangetree NetworkManager: <info>  Config: added 'scan_ssid' value '1'
May  4 14:19:57 orangetree NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
May  4 14:19:57 orangetree NetworkManager: <info>  Config: added 'psk' value '<omitted>'
May  4 14:19:57 orangetree NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May  4 14:19:57 orangetree NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May  4 14:19:57 orangetree NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May  4 14:19:57 orangetree NetworkManager: <info>  Config: set interface ap_scan to 1
May  4 14:19:57 orangetree NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
May  4 14:20:02 orangetree wpa_supplicant[1066]: CTRL-EVENT-SCAN-RESULTS 
May  4 14:20:02 orangetree wpa_supplicant[1066]: Trying to associate with 00:18:4d:57:21:92 (SSID='NETGEAR' freq=2462 MHz)
May  4 14:20:02 orangetree wpa_supplicant[1066]: Association request to the driver failed
May  4 14:20:02 orangetree NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> associating
May  4 14:20:03 orangetree kernel: [20077.127223] wlan0: authenticate with AP 00:18:4d:57:21:92
May  4 14:20:03 orangetree kernel: [20077.129059] wlan0: authenticated
May  4 14:20:03 orangetree kernel: [20077.129065] wlan0: associate with AP 00:18:4d:57:21:92
May  4 14:20:03 orangetree wpa_supplicant[1066]: Associated with 00:18:4d:57:21:92
May  4 14:20:03 orangetree NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
May  4 14:20:03 orangetree NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
May  4 14:20:03 orangetree kernel: [20077.131798] wlan0: RX AssocResp from 00:18:4d:57:21:92 (capab=0x411 status=0 aid=1)
May  4 14:20:03 orangetree kernel: [20077.131805] wlan0: associated
May  4 14:20:03 orangetree kernel: [20077.134123] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
May  4 14:20:03 orangetree NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
May  4 14:20:03 orangetree wpa_supplicant[1066]: WPA: Key negotiation completed with 00:18:4d:57:21:92 [PTK=TKIP GTK=TKIP]
May  4 14:20:03 orangetree wpa_supplicant[1066]: CTRL-EVENT-CONNECTED - Connection to 00:18:4d:57:21:92 completed (auth) [id=0 id_str=]
May  4 14:20:03 orangetree NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
May  4 14:20:03 orangetree NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'NETGEAR'.
May  4 14:20:03 orangetree NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
May  4 14:20:03 orangetree NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
May  4 14:20:03 orangetree NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
May  4 14:20:03 orangetree NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
May  4 14:20:03 orangetree dhclient: Internet Systems Consortium DHCP Client V3.1.2
May  4 14:20:03 orangetree dhclient: Copyright 2004-2008 Internet Systems Consortium.
May  4 14:20:03 orangetree dhclient: All rights reserved.
May  4 14:20:03 orangetree dhclient: For info, please visit http://www.isc.org/sw/dhcp/
May  4 14:20:03 orangetree dhclient: 
May  4 14:20:03 orangetree NetworkManager: <info>  dhclient started with pid 7338
May  4 14:20:03 orangetree NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
May  4 14:20:03 orangetree NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
May  4 14:20:03 orangetree NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
May  4 14:20:03 orangetree NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
May  4 14:20:03 orangetree NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit
May  4 14:20:03 orangetree dhclient: Listening on LPF/wlan0/00:22:fa:42:2f:be
May  4 14:20:03 orangetree dhclient: Sending on   LPF/wlan0/00:22:fa:42:2f:be
May  4 14:20:03 orangetree dhclient: Sending on   Socket/fallback
May  4 14:20:05 orangetree avahi-daemon[908]: Registering new address record for fe80::222:faff:fe42:2fbe on wlan0.*.
May  4 14:20:06 orangetree dhclient: DHCPREQUEST of 192.168.1.2 on wlan0 to 255.255.255.255 port 67
May  4 14:20:07 orangetree dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
May  4 14:20:07 orangetree dhclient: bound to 192.168.1.2 -- renewal in 34606 seconds.
May  4 14:20:07 orangetree NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> reboot
May  4 14:20:07 orangetree NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
May  4 14:20:07 orangetree NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
May  4 14:20:07 orangetree NetworkManager: <info>    address 192.168.1.2
May  4 14:20:07 orangetree NetworkManager: <info>    prefix 24 (255.255.255.0)
May  4 14:20:07 orangetree NetworkManager: <info>    gateway 192.168.1.1
May  4 14:20:07 orangetree NetworkManager: <info>    nameserver '192.168.1.1'
May  4 14:20:07 orangetree NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
May  4 14:20:07 orangetree NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
May  4 14:20:07 orangetree NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
May  4 14:20:07 orangetree avahi-daemon[908]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.2.
May  4 14:20:07 orangetree avahi-daemon[908]: New relevant interface wlan0.IPv4 for mDNS.
May  4 14:20:07 orangetree avahi-daemon[908]: Registering new address record for 192.168.1.2 on wlan0.IPv4.
May  4 14:20:08 orangetree NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
May  4 14:20:08 orangetree NetworkManager: <info>  Policy set 'Auto NETGEAR' (wlan0) as default for routing and DNS.
May  4 14:20:08 orangetree NetworkManager: <info>  Activation (wlan0) successful, device activated.
May  4 14:20:08 orangetree NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
May  4 14:20:09 orangetree ntpdate[7394]: adjust time server 91.189.94.4 offset -0.008530 sec
May  4 14:20:14 orangetree kernel: [20088.061270] wlan0: no IPv6 routers present
May  4 14:20:27 orangetree wpa_supplicant[1066]: CTRL-EVENT-SCAN-RESULTS 
```



any help that some expert could provide would be greatly appreciated!

-Cyril

---

