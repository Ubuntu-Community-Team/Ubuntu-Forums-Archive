---
title: "iwl3945 unstable, drops connection continuously"
date: 2010-08-20
forum: Networking &amp; Wireless
---

### Post by luksi1 on 2010-08-20
I've been searching in vain for a solution to this problem, as well as  troubleshooting, for weeks now. My wireless connection goes up and down  about every 30 seconds. I have used wicd and Network Manager as well as  invoking it directly from the command line with wpa_supplicant, all in  vain.

It does not seem that I have a DHCP problem, like others on  the forums have complained about. I get a DHCP address from my wireless  router without any problems.

Additionally, I have a stationary  Ubuntu box in another room using a usb wireless stick to connect to this  router without any problems.

The only difference I can see is  the driver. The stationary box is using a Realtek wireless driver and my  laptop is using iwl3945.

Router: 

Jensen AirLink 59300

PC Hardware:

Dell Latitude D620

Lshw output for wireless card:

```
      
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: wlan0
                version: 02
                serial: 00:1c:bf:32:75:6c
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 ip=192.168.0.100 latency=0 multicast=yes wireless=IEEE 802.11abg
                resources: irq:28 memory:efdff000-efdfffff
```Daemon log:

```
Aug 20 13:25:44 luke-laptop ntpdate[32549]: no servers can be used, exiting
Aug 20 13:26:00 luke-laptop dhclient: DHCPREQUEST of 217.208.111.65 on eth0 to 213.67.15.242 port 67
Aug 20 13:26:03 luke-laptop avahi-daemon[30320]: Interface wlan0.IPv4 no longer relevant for mDNS.
Aug  20 13:26:03 luke-laptop avahi-daemon[30320]: Leaving mDNS multicast  group on interface wlan0.IPv4 with address 192.168.0.100.
Aug 20 13:26:03 luke-laptop dhclient: receive_packet failed on wlan0: Network is down
Aug 20 13:26:03 luke-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Aug  20 13:26:03 luke-laptop NetworkManager:    SCPlugin-Ifupdown: devices  removed (path:  /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/wlan0, iface:  wlan0)
Aug 20 13:26:03 luke-laptop NetworkManager: <info>  (wlan0): now unmanaged
Aug 20 13:26:03 luke-laptop NetworkManager: <info>  (wlan0): device state change: 8 -> 1 (reason 36)
Aug 20 13:26:03 luke-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 36).
Aug 20 13:26:03 luke-laptop avahi-daemon[30320]: Withdrawing address record for fe80::21c:bfff:fe32:756c on wlan0.
Aug 20 13:26:03 luke-laptop avahi-daemon[30320]: Withdrawing address record for 192.168.0.100 on wlan0.
Aug 20 13:26:03 luke-laptop wpa_supplicant[865]: Failed to initialize the driver after interface was added.
Aug 20 13:26:03 luke-laptop wpa_supplicant[865]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Aug 20 13:26:03 luke-laptop NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 32460
Aug 20 13:26:03 luke-laptop NetworkManager: <info>  Policy set 'Ifupdown (eth0)' (eth0) as default for routing and DNS.
Aug 20 13:26:03 luke-laptop NetworkManager: <info>  (wlan0): cleaning up...
Aug 20 13:26:03 luke-laptop wpa_supplicant[865]: Failed to disable WPA in the driver.
Aug  20 13:26:03 luke-laptop nm-dispatcher.action: Error in get_property:  Method "Get" with signature "ss" on interface  "org.freedesktop.DBus.Properties" doesn't exist#012
Aug 20 13:26:03  luke-laptop NetworkManager: <info>  Radio killswitch  /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/ieee80211/phy0/rfkill158  disappeared
Aug 20 13:26:04 luke-laptop NetworkManager:  <info>  Found wlan radio killswitch rfkill159 (at  /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/ieee80211/phy0/rfkill159)  (driver <unknown>)
Aug 20 13:26:04 luke-laptop  NetworkManager:    SCPlugin-Ifupdown: devices added (path:  /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/wlan0, iface:  wlan0)
Aug 20 13:26:04 luke-laptop NetworkManager:     SCPlugin-Ifupdown: device added (path:  /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/wlan0, iface:  wlan0): no ifupdown configuration found.
Aug 20 13:26:04 luke-laptop NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).
Aug 20 13:26:04 luke-laptop NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'iwl3945')
Aug 20 13:26:04 luke-laptop NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/157
Aug 20 13:26:04 luke-laptop NetworkManager: <info>  (wlan0): now managed
Aug 20 13:26:04 luke-laptop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Aug 20 13:26:04 luke-laptop NetworkManager: <info>  (wlan0): bringing up device.
Aug 20 13:26:04 luke-laptop NetworkManager: <info>  (wlan0): preparing device.
Aug 20 13:26:04 luke-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Aug 20 13:26:04 luke-laptop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Aug 20 13:26:04 luke-laptop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
Aug 20 13:26:04 luke-laptop wpa_supplicant[865]: Failed to initiate AP scan.
Aug 20 13:26:06 luke-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto D.Zoolander'
Aug 20 13:26:06 luke-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Aug 20 13:26:06 luke-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 20 13:26:06 luke-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 20 13:26:06 luke-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 20 13:26:06 luke-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 20 13:26:06 luke-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 20 13:26:06 luke-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Aug  20 13:26:06 luke-laptop NetworkManager: <info>  Activation  (wlan0/wireless): connection 'Auto D.Zoolander' has security, and  secrets exist.  No new secrets needed.
Aug 20 13:26:06 luke-laptop NetworkManager: <info>  Config: added 'ssid' value 'D.Zoolander'
Aug 20 13:26:06 luke-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Aug 20 13:26:06 luke-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Aug 20 13:26:06 luke-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Aug  20 13:26:06 luke-laptop NetworkManager:  nm_setting_802_1x_get_pkcs11_engine_path: assertion  `NM_IS_SETTING_802_1X (setting)' failed
Aug 20 13:26:06 luke-laptop  NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion  `NM_IS_SETTING_802_1X (setting)' failed
Aug 20 13:26:06 luke-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 20 13:26:06 luke-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Aug 20 13:26:06 luke-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Aug 20 13:26:11 luke-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Aug 20 13:26:13 luke-laptop dhclient: DHCPREQUEST of 217.208.111.65 on eth0 to 213.67.15.242 port 67
Aug 20 13:26:14 luke-laptop wpa_supplicant[865]: Trying to associate with 00:1f:1f:6d:0d:0c (SSID='D.Zoolander' freq=2412 MHz)
Aug 20 13:26:14 luke-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Aug 20 13:26:14 luke-laptop wpa_supplicant[865]: Associated with 00:1f:1f:6d:0d:0c
Aug 20 13:26:14 luke-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Aug  20 13:26:15 luke-laptop NetworkManager: <info>  (wlan0):  supplicant connection state:  associated -> 4-way handshake
Aug 20 13:26:15 luke-laptop wpa_supplicant[865]: WPA: Key negotiation completed with 00:1f:1f:6d:0d:0c [PTK=CCMP GTK=TKIP]
Aug  20 13:26:15 luke-laptop wpa_supplicant[865]: CTRL-EVENT-CONNECTED -  Connection to 00:1f:1f:6d:0d:0c completed (auth) [id=0 id_str=]
Aug  20 13:26:15 luke-laptop NetworkManager: <info>  (wlan0):  supplicant connection state:  4-way handshake -> group handshake
Aug 20 13:26:15 luke-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Aug  20 13:26:15 luke-laptop NetworkManager: <info>  Activation  (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected  to wireless network 'D.Zoolander'.
Aug 20 13:26:15 luke-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 20 13:26:15 luke-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Aug 20 13:26:15 luke-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Aug 20 13:26:15 luke-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Aug 20 13:26:15 luke-laptop NetworkManager: <info>  dhclient started with pid 32686
Aug 20 13:26:15 luke-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Aug 20 13:26:15 luke-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Aug 20 13:26:15 luke-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Aug 20 13:26:15 luke-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Aug 20 13:26:15 luke-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Aug 20 13:26:15 luke-laptop dhclient: Copyright 2004-2009 Internet Systems Consortium.
Aug 20 13:26:15 luke-laptop dhclient: All rights reserved.
Aug 20 13:26:15 luke-laptop dhclient: For info, please visit https://www.isc.org/software/dhcp/
Aug 20 13:26:15 luke-laptop dhclient: 
Aug 20 13:26:15 luke-laptop NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Aug 20 13:26:15 luke-laptop dhclient: Listening on LPF/wlan0/00:1c:bf:32:75:6c
Aug 20 13:26:15 luke-laptop dhclient: Sending on   LPF/wlan0/00:1c:bf:32:75:6c
Aug 20 13:26:15 luke-laptop dhclient: Sending on   Socket/fallback
Aug 20 13:26:15 luke-laptop avahi-daemon[30320]: Registering new address record for fe80::21c:bfff:fe32:756c on wlan0.*.
Aug 20 13:26:17 luke-laptop dhclient: DHCPREQUEST of 192.168.0.100 on wlan0 to 255.255.255.255 port 67
Aug 20 13:26:24 luke-laptop dhclient: DHCPREQUEST of 192.168.0.100 on wlan0 to 255.255.255.255 port 67
Aug 20 13:26:24 luke-laptop dhclient: DHCPACK of 192.168.0.100 from 192.168.0.1
Aug 20 13:26:24 luke-laptop NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> reboot
Aug 20 13:26:24 luke-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Aug 20 13:26:24 luke-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Aug 20 13:26:24 luke-laptop NetworkManager: <info>    address 192.168.0.100
Aug 20 13:26:24 luke-laptop NetworkManager: <info>    prefix 24 (255.255.255.0)
Aug 20 13:26:24 luke-laptop NetworkManager: <info>    gateway 192.168.0.1
Aug 20 13:26:24 luke-laptop NetworkManager: <info>    nameserver '192.168.0.1'
Aug 20 13:26:24 luke-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Aug 20 13:26:24 luke-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Aug 20 13:26:24 luke-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Aug  20 13:26:24 luke-laptop avahi-daemon[30320]: Joining mDNS multicast  group on interface wlan0.IPv4 with address 192.168.0.100.
Aug 20 13:26:24 luke-laptop avahi-daemon[30320]: New relevant interface wlan0.IPv4 for mDNS.
Aug 20 13:26:24 luke-laptop avahi-daemon[30320]: Registering new address record for 192.168.0.100 on wlan0.IPv4.
Aug 20 13:26:24 luke-laptop dhclient: bound to 192.168.0.100 -- renewal in 82538 seconds.
Aug 20 13:26:25 luke-laptop NetworkManager: <info>  Policy set 'Ifupdown (eth0)' (eth0) as default for routing and DNS.
Aug 20 13:26:25 luke-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Aug 20 13:26:25 luke-laptop NetworkManager: <info>  Activation (wlan0) successful, device activated.
Aug 20 13:26:25 luke-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Aug 20 13:26:26 luke-laptop dhclient: DHCPREQUEST of 217.208.111.65 on eth0 to 213.67.15.242 port 67
Aug 20 13:26:47 luke-laptop dhclient: DHCPREQUEST of 217.208.111.65 on eth0 to 213.67.15.242 port 67
Aug 20 13:26:47 luke-laptop ntpdate[32742]: can't find host ntp.ubuntu.com
```Dmesg: 

```
[20432.694552] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[20442.962890] wlan0: deauthenticating from 00:1f:1f:6d:0d:0c by local choice (reason=3)
[20442.964496] wlan0: direct probe to AP 00:1f:1f:6d:0d:0c (try 1)
[20442.968385] wlan0: direct probe responded
[20442.968394] wlan0: authenticate with AP 00:1f:1f:6d:0d:0c (try 1)
[20442.970282] wlan0: authenticated
[20442.970318] wlan0: associate with AP 00:1f:1f:6d:0d:0c (try 1)
[20442.972947] wlan0: RX AssocResp from 00:1f:1f:6d:0d:0c (capab=0x411 status=0 aid=1)
[20442.972953] wlan0: associated
[20442.975583] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[20453.860045] wlan0: no IPv6 routers present
[20493.890182] wlan0: deauthenticating from 00:1f:1f:6d:0d:0c by local choice (reason=3)
[20494.350958] iwl3945 0000:0c:00.0: PCI INT A disabled
[20494.515822] cfg80211: Calling CRDA to update world regulatory domain
[20494.526690] cfg80211: World regulatory domain updated:
[20494.526696]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[20494.526703]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[20494.526709]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[20494.526714]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[20494.526720]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[20494.526725]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[20494.584461] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[20494.584468] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[20494.584583] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[20494.584608] iwl3945 0000:0c:00.0: setting latency timer to 64
[20494.640833] iwl3945 0000:0c:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[20494.640841] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
[20494.641001] iwl3945 0000:0c:00.0: irq 28 for MSI/MSI-X
[20494.641502] phy0: Selected rate control algorithm 'iwl-3945-rs'
[20494.653268] iwl3945 0000:0c:00.0: firmware: requesting iwlwifi-3945-2.ucode
[20494.659406] iwl3945 0000:0c:00.0: loaded firmware version 15.32.2.9
[20494.729608] Registered led device: iwl-phy0::radio
[20494.729953] Registered led device: iwl-phy0::assoc
[20494.730398] Registered led device: iwl-phy0::RX
[20494.730944] Registered led device: iwl-phy0::TX
```Any help, or simply pointing in me in the right direction, would be appreciated.

---

### Post by wadelius on 2010-09-15
This could be [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/348204?comments=all]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/348204?comments=all"). I've found a way to fix it for me, and I've posted it on the bug. It has to do with tcp window scaling.

---

