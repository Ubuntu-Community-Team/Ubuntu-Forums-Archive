---
title: "Internet connection suddenly vanished... then randomly came back"
date: 2013-05-10
forum: Networking &amp; Wireless
---

### Post by fizikz on 2013-05-10
Hardware: Intel 6200AGN wireless adapter (wlan1)
Driver: iwlwifi
Wireless AP: TP-Link TL-WR841N

The problem: The internet connection suddenly dropped. I could not reach any IP, including those of the wireless AP and router within my own network. I verified with another computer that both the network and internet were operational.

The wireless connection was intact for the whole time, there was no drop of the wireless connection, and I was able to disconnect and reconnect to various APs in my home. However, no page would load in the browser.

The system in question is assigned a static DHCP IP of 192.168.2.8 by the router.

Here is part of the syslog from around the time the internet drop occurred:

```
May 10 13:21:01 ssg1 kernel: [55680.964029] iwlwifi 0000:03:00.0: Queue 11 stuck for 2000 ms.
May 10 13:21:01 ssg1 kernel: [55680.964035] iwlwifi 0000:03:00.0: Current read_ptr 169 write_ptr 88
May 10 13:21:01 ssg1 kernel: [55680.964039] iwlwifi 0000:03:00.0: On demand firmware reload
May 10 13:21:01 ssg1 kernel: [55680.964545] ieee80211 phy0: Hardware restart was requested
May 10 13:21:01 ssg1 kernel: [55680.964762] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
May 10 13:21:01 ssg1 kernel: [55680.971676] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x1
May 10 13:24:32 ssg1 NetworkManager[1056]: <info> (wlan1): disconnecting for new activation request.
May 10 13:24:32 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: activated -> disconnected (reason 'none') [100 30 0]
May 10 13:24:33 ssg1 NetworkManager[1056]: <info> (wlan1): deactivating device (reason 'none') [0]
May 10 13:24:33 ssg1 NetworkManager[1056]: <info> (wlan1): canceled DHCP transaction, DHCP client pid 16917
May 10 13:24:33 ssg1 kernel: [55892.532987] wlan1: deauthenticating from a0:f3:c1:c1:18:ea by local choice (reason=3)
May 10 13:24:33 ssg1 kernel: [55892.556230] cfg80211: All devices are disconnected, going to restore regulatory settings
May 10 13:24:33 ssg1 kernel: [55892.556241] cfg80211: Restoring regulatory settings
May 10 13:24:33 ssg1 kernel: [55892.556249] cfg80211: Calling CRDA to update world regulatory domain
May 10 13:24:33 ssg1 NetworkManager[1056]: <info> DNS: starting dnsmasq...
May 10 13:24:33 ssg1 dnsmasq[16923]: exiting on receipt of SIGTERM
May 10 13:24:33 ssg1 kernel: [55893.235138] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
May 10 13:24:33 ssg1 kernel: [55893.235143] cfg80211: World regulatory domain updated:
May 10 13:24:33 ssg1 kernel: [55893.235145] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May 10 13:24:33 ssg1 kernel: [55893.235149] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 13:24:33 ssg1 kernel: [55893.235152] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 10 13:24:33 ssg1 kernel: [55893.235156] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 10 13:24:33 ssg1 kernel: [55893.235159] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 13:24:33 ssg1 kernel: [55893.235162] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 13:24:34 ssg1 wpa_supplicant[1260]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
May 10 13:24:34 ssg1 NetworkManager[1056]: <info> (wlan1): writing resolv.conf to /sbin/resolvconf
May 10 13:24:34 ssg1 dnsmasq[20207]: started, version 2.59 cache disabled
May 10 13:24:34 ssg1 dnsmasq[20207]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
May 10 13:24:34 ssg1 dnsmasq[20207]: warning: no upstream servers configured
May 10 13:24:34 ssg1 NetworkManager[1056]: <info> Activation (wlan1) starting connection 'carbon'
May 10 13:24:34 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 10 13:24:34 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
May 10 13:24:34 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: completed -> disconnected
May 10 13:24:34 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
May 10 13:24:34 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
May 10 13:24:34 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
May 10 13:24:34 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
May 10 13:24:34 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: prepare -> config (reason 'none') [40 50 0]
May 10 13:24:34 ssg1 NetworkManager[1056]: <info> Activation (wlan1/wireless): access point 'carbon' has security, but secrets are required.
May 10 13:24:34 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: config -> need-auth (reason 'none') [50 60 0]
May 10 13:24:34 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
May 10 13:24:34 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
May 10 13:24:34 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
May 10 13:24:34 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: need-auth -> prepare (reason 'none') [60 40 0]
May 10 13:24:34 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
May 10 13:24:34 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
May 10 13:24:34 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
May 10 13:24:34 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: prepare -> config (reason 'none') [40 50 0]
May 10 13:24:34 ssg1 NetworkManager[1056]: <info> Activation (wlan1/wireless): connection 'carbon' has security, and secrets exist.  No new secrets needed.
May 10 13:24:34 ssg1 NetworkManager[1056]: <info> Config: added 'ssid' value 'carbon'
May 10 13:24:34 ssg1 NetworkManager[1056]: <info> Config: added 'scan_ssid' value '1'
May 10 13:24:34 ssg1 NetworkManager[1056]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
May 10 13:24:34 ssg1 NetworkManager[1056]: <info> Config: added 'auth_alg' value 'OPEN'
May 10 13:24:34 ssg1 NetworkManager[1056]: <info> Config: added 'psk' value '<omitted>'
May 10 13:24:34 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
May 10 13:24:35 ssg1 dbus[1018]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May 10 13:24:35 ssg1 NetworkManager[1056]: <info> Config: set interface ap_scan to 1
May 10 13:24:35 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: disconnected -> scanning
May 10 13:24:35 ssg1 dbus[1018]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 10 13:24:38 ssg1 wpa_supplicant[1260]: Trying to authenticate with a0:f3:c1:c1:18:ea (SSID='carbon' freq=2412 MHz)
May 10 13:24:38 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: scanning -> authenticating
May 10 13:24:38 ssg1 kernel: [55897.969296] wlan1: authenticate with a0:f3:c1:c1:18:ea (try 1)
May 10 13:24:38 ssg1 kernel: [55897.973360] wlan1: authenticated
May 10 13:24:38 ssg1 kernel: [55897.973855] wlan1: associate with a0:f3:c1:c1:18:ea (try 1)
May 10 13:24:38 ssg1 wpa_supplicant[1260]: Trying to associate with a0:f3:c1:c1:18:ea (SSID='carbon' freq=2412 MHz)
May 10 13:24:38 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: authenticating -> associating
May 10 13:24:38 ssg1 kernel: [55897.977956] wlan1: RX ReassocResp from a0:f3:c1:c1:18:ea (capab=0x431 status=0 aid=1)
May 10 13:24:38 ssg1 kernel: [55897.977961] wlan1: associated
May 10 13:24:38 ssg1 kernel: [55897.977965] wlan1: No basic rates in AssocResp. Using min supported rate instead.
May 10 13:24:38 ssg1 wpa_supplicant[1260]: Associated with a0:f3:c1:c1:18:ea
May 10 13:24:38 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: associating -> associated
May 10 13:24:39 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: associated -> 4-way handshake
May 10 13:24:39 ssg1 wpa_supplicant[1260]: WPA: Key negotiation completed with a0:f3:c1:c1:18:ea [PTK=CCMP GTK=CCMP]
May 10 13:24:39 ssg1 wpa_supplicant[1260]: CTRL-EVENT-CONNECTED - Connection to a0:f3:c1:c1:18:ea completed (reauth) [id=0 id_str=]
May 10 13:24:39 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: 4-way handshake -> completed
May 10 13:24:39 ssg1 NetworkManager[1056]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'carbon'.
May 10 13:24:39 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) scheduled.
May 10 13:24:39 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) started...
May 10 13:24:39 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: config -> ip-config (reason 'none') [50 70 0]
May 10 13:24:39 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Beginning DHCPv4 transaction (timeout in 45 seconds)
May 10 13:24:39 ssg1 NetworkManager[1056]: <info> dhclient started with pid 20230
May 10 13:24:39 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Beginning IP6 addrconf.
May 10 13:24:39 ssg1 dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
May 10 13:24:39 ssg1 dhclient: Copyright 2004-2011 Internet Systems Consortium.
May 10 13:24:39 ssg1 dhclient: All rights reserved.
May 10 13:24:39 ssg1 dhclient: For info, please visit https://www.isc.org/software/dhcp/
May 10 13:24:39 ssg1 dhclient: 
May 10 13:24:40 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) complete.
May 10 13:24:40 ssg1 NetworkManager[1056]: <info> (wlan1): DHCPv4 state changed nbi -> preinit
May 10 13:24:40 ssg1 dhclient: Listening on LPF/wlan1/00:23:14:dd:2c:5c
May 10 13:24:40 ssg1 dhclient: Sending on   LPF/wlan1/00:23:14:dd:2c:5c
May 10 13:24:40 ssg1 dhclient: Sending on   Socket/fallback
May 10 13:24:40 ssg1 dhclient: DHCPREQUEST of 192.168.2.8 on wlan1 to 255.255.255.255 port 67
May 10 13:24:40 ssg1 dhclient: DHCPACK of 192.168.2.8 from 192.168.2.1
May 10 13:24:40 ssg1 dhclient: bound to 192.168.2.8 -- renewal in 139539721 seconds.
May 10 13:24:40 ssg1 NetworkManager[1056]: <info> (wlan1): DHCPv4 state changed preinit -> reboot
May 10 13:24:40 ssg1 NetworkManager[1056]: <info>   address 192.168.2.8
May 10 13:24:40 ssg1 NetworkManager[1056]: <info>   prefix 24 (255.255.255.0)
May 10 13:24:40 ssg1 NetworkManager[1056]: <info>   gateway 192.168.2.1
May 10 13:24:40 ssg1 NetworkManager[1056]: <info>   nameserver '192.168.1.254'
May 10 13:24:40 ssg1 NetworkManager[1056]: <info>   nameserver '192.168.2.1'
May 10 13:24:40 ssg1 NetworkManager[1056]: <info>   domain name 'esr9850'
May 10 13:24:40 ssg1 NetworkManager[1056]: <info>   wins '192.168.2.1'
May 10 13:24:40 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
May 10 13:24:40 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Commit) started...
May 10 13:24:41 ssg1 dnsmasq[20207]: exiting on receipt of SIGTERM
May 10 13:24:41 ssg1 NetworkManager[1056]: <info> DNS: starting dnsmasq...
May 10 13:24:41 ssg1 NetworkManager[1056]: <info> (wlan1): writing resolv.conf to /sbin/resolvconf
May 10 13:24:41 ssg1 dnsmasq[20236]: started, version 2.59 cache disabled
May 10 13:24:41 ssg1 dnsmasq[20236]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
May 10 13:24:41 ssg1 dnsmasq[20236]: using nameserver 192.168.2.1#53
May 10 13:24:41 ssg1 dnsmasq[20236]: using nameserver 192.168.1.254#53
May 10 13:24:41 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: ip-config -> activated (reason 'none') [70 100 0]
May 10 13:24:41 ssg1 NetworkManager[1056]: <info> Policy set 'carbon' (wlan1) as default for IPv4 routing and DNS.
May 10 13:24:41 ssg1 NetworkManager[1056]: <info> Activation (wlan1) successful, device activated.
May 10 13:24:41 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Commit) complete.
May 10 13:24:50 ssg1 kernel: [55910.160034] wlan1: no IPv6 routers present
May 10 13:24:59 ssg1 NetworkManager[1056]: <info> (wlan1): IP6 addrconf timed out or failed.
May 10 13:24:59 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May 10 13:24:59 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) started...
May 10 13:24:59 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
May 10 13:25:01 ssg1 CRON[20317]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> (wlan1): disconnecting for new activation request.
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: activated -> disconnected (reason 'none') [100 30 0]
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> (wlan1): deactivating device (reason 'none') [0]
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> (wlan1): canceled DHCP transaction, DHCP client pid 20230
May 10 13:25:13 ssg1 dnsmasq[20236]: exiting on receipt of SIGTERM
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> DNS: starting dnsmasq...
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> (wlan1): writing resolv.conf to /sbin/resolvconf
May 10 13:25:13 ssg1 dbus[1018]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> Activation (wlan1) starting connection 'tester2 1'
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 10 13:25:13 ssg1 kernel: [55932.923756] wlan1: deauthenticating from a0:f3:c1:c1:18:ea by local choice (reason=3)
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: prepare -> config (reason 'none') [40 50 0]
May 10 13:25:13 ssg1 dbus[1018]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 10 13:25:13 ssg1 wpa_supplicant[1260]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
May 10 13:25:13 ssg1 kernel: [55932.980452] cfg80211: All devices are disconnected, going to restore regulatory settings
May 10 13:25:13 ssg1 kernel: [55932.980460] cfg80211: Restoring regulatory settings
May 10 13:25:13 ssg1 kernel: [55932.980470] cfg80211: Calling CRDA to update world regulatory domain
May 10 13:25:13 ssg1 kernel: [55932.986791] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
May 10 13:25:13 ssg1 kernel: [55932.986795] cfg80211: World regulatory domain updated:
May 10 13:25:13 ssg1 kernel: [55932.986797] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May 10 13:25:13 ssg1 kernel: [55932.986801] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 13:25:13 ssg1 kernel: [55932.986804] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 10 13:25:13 ssg1 kernel: [55932.986808] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 10 13:25:13 ssg1 kernel: [55932.986811] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 13:25:13 ssg1 kernel: [55932.986814] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> Activation (wlan1/wireless): access point 'tester2 1' has security, but secrets are required.
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: config -> need-auth (reason 'none') [50 60 0]
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: completed -> disconnected
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: need-auth -> prepare (reason 'none') [60 40 0]
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: prepare -> config (reason 'none') [40 50 0]
May 10 13:25:13 ssg1 dnsmasq[20320]: started, version 2.59 cache disabled
May 10 13:25:13 ssg1 dnsmasq[20320]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
May 10 13:25:13 ssg1 dnsmasq[20320]: warning: no upstream servers configured
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> Activation (wlan1/wireless): connection 'tester2 1' has security, and secrets exist.  No new secrets needed.
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> Config: added 'ssid' value 'tester2'
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> Config: added 'scan_ssid' value '1'
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> Config: added 'auth_alg' value 'OPEN'
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> Config: added 'psk' value '<omitted>'
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
May 10 13:25:13 ssg1 NetworkManager[1056]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> Config: set interface ap_scan to 1
May 10 13:25:13 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: disconnected -> scanning
May 10 13:25:16 ssg1 wpa_supplicant[1260]: Trying to authenticate with 10:bf:48:3c:a3:d8 (SSID='tester2' freq=2437 MHz)
May 10 13:25:16 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: scanning -> authenticating
May 10 13:25:16 ssg1 wpa_supplicant[1260]: Trying to associate with 10:bf:48:3c:a3:d8 (SSID='tester2' freq=2437 MHz)
May 10 13:25:16 ssg1 kernel: [55936.196221] wlan1: authenticate with 10:bf:48:3c:a3:d8 (try 1)
May 10 13:25:16 ssg1 kernel: [55936.198120] wlan1: authenticated
May 10 13:25:16 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: authenticating -> associating
May 10 13:25:17 ssg1 kernel: [55936.276111] wlan1: associate with 10:bf:48:3c:a3:d8 (try 1)
May 10 13:25:17 ssg1 kernel: [55936.279363] wlan1: RX AssocResp from 10:bf:48:3c:a3:d8 (capab=0x411 status=0 aid=1)
May 10 13:25:17 ssg1 kernel: [55936.279368] wlan1: associated
May 10 13:25:17 ssg1 wpa_supplicant[1260]: Associated with 10:bf:48:3c:a3:d8
May 10 13:25:17 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: associating -> 4-way handshake
May 10 13:25:17 ssg1 wpa_supplicant[1260]: WPA: Key negotiation completed with 10:bf:48:3c:a3:d8 [PTK=CCMP GTK=CCMP]
May 10 13:25:17 ssg1 wpa_supplicant[1260]: CTRL-EVENT-CONNECTED - Connection to 10:bf:48:3c:a3:d8 completed (reauth) [id=0 id_str=]
May 10 13:25:17 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: 4-way handshake -> completed
May 10 13:25:17 ssg1 NetworkManager[1056]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'tester2'.
May 10 13:25:17 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) scheduled.
May 10 13:25:17 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) started...
May 10 13:25:17 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: config -> ip-config (reason 'none') [50 70 0]
May 10 13:25:17 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Beginning DHCPv4 transaction (timeout in 45 seconds)
May 10 13:25:17 ssg1 NetworkManager[1056]: <info> dhclient started with pid 20346
May 10 13:25:17 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Beginning IP6 addrconf.
May 10 13:25:17 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) complete.
May 10 13:25:17 ssg1 dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
May 10 13:25:17 ssg1 dhclient: Copyright 2004-2011 Internet Systems Consortium.
May 10 13:25:17 ssg1 dhclient: All rights reserved.
May 10 13:25:17 ssg1 dhclient: For info, please visit https://www.isc.org/software/dhcp/
May 10 13:25:17 ssg1 dhclient: 
May 10 13:25:17 ssg1 NetworkManager[1056]: <info> (wlan1): DHCPv4 state changed nbi -> preinit
May 10 13:25:17 ssg1 dhclient: Listening on LPF/wlan1/00:23:14:dd:2c:5c
May 10 13:25:17 ssg1 dhclient: Sending on   LPF/wlan1/00:23:14:dd:2c:5c
May 10 13:25:17 ssg1 dhclient: Sending on   Socket/fallback
May 10 13:25:17 ssg1 dhclient: DHCPREQUEST of 192.168.2.111 on wlan1 to 255.255.255.255 port 67
May 10 13:25:17 ssg1 dhclient: DHCPNAK from 192.168.2.1
May 10 13:25:17 ssg1 NetworkManager[1056]: <info> (wlan1): DHCPv4 state changed preinit -> expire
May 10 13:25:17 ssg1 dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 3
May 10 13:25:17 ssg1 NetworkManager[1056]: <info> (wlan1): DHCPv4 state changed expire -> preinit
May 10 13:25:17 ssg1 dhclient: DHCPREQUEST of 192.168.2.8 on wlan1 to 255.255.255.255 port 67
May 10 13:25:17 ssg1 dhclient: DHCPOFFER of 192.168.2.8 from 192.168.2.1
May 10 13:25:17 ssg1 dhclient: DHCPACK of 192.168.2.8 from 192.168.2.1
May 10 13:25:17 ssg1 dhclient: bound to 192.168.2.8 -- renewal in 124462717 seconds.
May 10 13:25:17 ssg1 NetworkManager[1056]: <info> (wlan1): DHCPv4 state changed preinit -> bound
May 10 13:25:17 ssg1 NetworkManager[1056]: <info>   address 192.168.2.8
May 10 13:25:17 ssg1 NetworkManager[1056]: <info>   prefix 24 (255.255.255.0)
May 10 13:25:17 ssg1 NetworkManager[1056]: <info>   gateway 192.168.2.1
May 10 13:25:17 ssg1 NetworkManager[1056]: <info>   nameserver '192.168.1.254'
May 10 13:25:17 ssg1 NetworkManager[1056]: <info>   nameserver '192.168.2.1'
May 10 13:25:17 ssg1 NetworkManager[1056]: <info>   domain name 'esr9850'
May 10 13:25:17 ssg1 NetworkManager[1056]: <info>   wins '192.168.2.1'
May 10 13:25:17 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
May 10 13:25:17 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Commit) started...
May 10 13:25:18 ssg1 NetworkManager[1056]: <info> DNS: starting dnsmasq...
May 10 13:25:18 ssg1 dnsmasq[20320]: exiting on receipt of SIGTERM
May 10 13:25:18 ssg1 NetworkManager[1056]: <info> (wlan1): writing resolv.conf to /sbin/resolvconf
May 10 13:25:18 ssg1 dnsmasq[20351]: started, version 2.59 cache disabled
May 10 13:25:18 ssg1 dnsmasq[20351]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
May 10 13:25:18 ssg1 dnsmasq[20351]: using nameserver 192.168.2.1#53
May 10 13:25:18 ssg1 dnsmasq[20351]: using nameserver 192.168.1.254#53
May 10 13:25:18 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: ip-config -> activated (reason 'none') [70 100 0]
May 10 13:25:18 ssg1 ntpdate[20291]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
May 10 13:25:18 ssg1 ntpdate[20291]: no servers can be used, exiting
May 10 13:25:18 ssg1 NetworkManager[1056]: <info> Policy set 'tester2 1' (wlan1) as default for IPv4 routing and DNS.
May 10 13:25:18 ssg1 NetworkManager[1056]: <info> Activation (wlan1) successful, device activated.
May 10 13:25:18 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Commit) complete.
May 10 13:25:26 ssg1 ntpdate[20406]: adjust time server 91.189.94.4 offset 0.018284 sec
May 10 13:25:27 ssg1 kernel: [55947.024060] wlan1: no IPv6 routers present
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> (wlan1): disconnecting for new activation request.
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: activated -> disconnected (reason 'none') [100 30 0]
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> (wlan1): deactivating device (reason 'none') [0]
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> (wlan1): canceled DHCP transaction, DHCP client pid 20346
May 10 13:25:36 ssg1 kernel: [55955.836042] wlan1: deauthenticating from 10:bf:48:3c:a3:d8 by local choice (reason=3)
May 10 13:25:36 ssg1 wpa_supplicant[1260]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
May 10 13:25:36 ssg1 kernel: [55955.896219] cfg80211: All devices are disconnected, going to restore regulatory settings
May 10 13:25:36 ssg1 kernel: [55955.896226] cfg80211: Restoring regulatory settings
May 10 13:25:36 ssg1 kernel: [55955.896231] cfg80211: Calling CRDA to update world regulatory domain
May 10 13:25:36 ssg1 dnsmasq[20351]: exiting on receipt of SIGTERM
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> DNS: starting dnsmasq...
May 10 13:25:36 ssg1 dnsmasq[20431]: started, version 2.59 cache disabled
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> (wlan1): writing resolv.conf to /sbin/resolvconf
May 10 13:25:36 ssg1 kernel: [55955.905681] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
May 10 13:25:36 ssg1 kernel: [55955.905686] cfg80211: World regulatory domain updated:
May 10 13:25:36 ssg1 kernel: [55955.905688] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May 10 13:25:36 ssg1 kernel: [55955.905692] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 13:25:36 ssg1 kernel: [55955.905695] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 10 13:25:36 ssg1 kernel: [55955.905698] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 10 13:25:36 ssg1 kernel: [55955.905701] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 13:25:36 ssg1 kernel: [55955.905704] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 13:25:36 ssg1 dnsmasq[20431]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
May 10 13:25:36 ssg1 dnsmasq[20431]: warning: no upstream servers configured
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> Activation (wlan1) starting connection 'tester5 1'
May 10 13:25:36 ssg1 dbus[1018]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: completed -> disconnected
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: prepare -> config (reason 'none') [40 50 0]
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> Activation (wlan1/wireless): access point 'tester5 1' has security, but secrets are required.
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: config -> need-auth (reason 'none') [50 60 0]
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: need-auth -> prepare (reason 'none') [60 40 0]
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: prepare -> config (reason 'none') [40 50 0]
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> Activation (wlan1/wireless): connection 'tester5 1' has security, and secrets exist.  No new secrets needed.
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> Config: added 'ssid' value 'tester5'
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> Config: added 'scan_ssid' value '1'
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> Config: added 'auth_alg' value 'OPEN'
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> Config: added 'psk' value '<omitted>'
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
May 10 13:25:36 ssg1 dbus[1018]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> Config: set interface ap_scan to 1
May 10 13:25:36 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: disconnected -> scanning
May 10 13:25:39 ssg1 wpa_supplicant[1260]: Trying to authenticate with 10:bf:48:3c:a3:dc (SSID='tester5' freq=5745 MHz)
May 10 13:25:39 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: scanning -> authenticating
May 10 13:25:39 ssg1 kernel: [55959.138652] wlan1: authenticate with 10:bf:48:3c:a3:dc (try 1)
May 10 13:25:40 ssg1 kernel: [55959.336047] wlan1: authenticate with 10:bf:48:3c:a3:dc (try 2)
May 10 13:25:40 ssg1 kernel: [55959.536047] wlan1: authenticate with 10:bf:48:3c:a3:dc (try 3)
May 10 13:25:40 ssg1 kernel: [55959.736061] wlan1: authentication with 10:bf:48:3c:a3:dc timed out
May 10 13:25:48 ssg1 wpa_supplicant[1260]: Trying to authenticate with 10:bf:48:3c:a3:dc (SSID='tester5' freq=5745 MHz)
May 10 13:25:48 ssg1 kernel: [55968.051929] wlan1: authenticate with 10:bf:48:3c:a3:dc (try 1)
May 10 13:25:48 ssg1 kernel: [55968.248048] wlan1: authenticate with 10:bf:48:3c:a3:dc (try 2)
May 10 13:25:49 ssg1 wpa_supplicant[1260]: Trying to associate with 10:bf:48:3c:a3:dc (SSID='tester5' freq=5745 MHz)
May 10 13:25:49 ssg1 kernel: [55968.448057] wlan1: authenticate with 10:bf:48:3c:a3:dc (try 3)
May 10 13:25:49 ssg1 kernel: [55968.449297] wlan1: authenticated
May 10 13:25:49 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: authenticating -> associating
May 10 13:25:49 ssg1 kernel: [55968.519151] wlan1: associate with 10:bf:48:3c:a3:dc (try 1)
May 10 13:25:49 ssg1 kernel: [55968.716052] wlan1: associate with 10:bf:48:3c:a3:dc (try 2)
May 10 13:25:49 ssg1 kernel: [55968.717212] wlan1: RX AssocResp from 10:bf:48:3c:a3:dc (capab=0x11 status=0 aid=1)
May 10 13:25:49 ssg1 kernel: [55968.717219] wlan1: associated
May 10 13:25:49 ssg1 wpa_supplicant[1260]: Associated with 10:bf:48:3c:a3:dc
May 10 13:25:49 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: associating -> associated
May 10 13:25:49 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: associated -> 4-way handshake
May 10 13:25:49 ssg1 wpa_supplicant[1260]: WPA: Key negotiation completed with 10:bf:48:3c:a3:dc [PTK=CCMP GTK=CCMP]
May 10 13:25:49 ssg1 wpa_supplicant[1260]: CTRL-EVENT-CONNECTED - Connection to 10:bf:48:3c:a3:dc completed (reauth) [id=0 id_str=]
May 10 13:25:49 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: 4-way handshake -> completed
May 10 13:25:49 ssg1 NetworkManager[1056]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'tester5'.
May 10 13:25:49 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) scheduled.
May 10 13:25:49 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) started...
May 10 13:25:49 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: config -> ip-config (reason 'none') [50 70 0]
May 10 13:25:49 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Beginning DHCPv4 transaction (timeout in 45 seconds)
May 10 13:25:49 ssg1 NetworkManager[1056]: <info> dhclient started with pid 20452
May 10 13:25:49 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Beginning IP6 addrconf.
May 10 13:25:49 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) complete.
May 10 13:25:49 ssg1 dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
May 10 13:25:49 ssg1 dhclient: Copyright 2004-2011 Internet Systems Consortium.
May 10 13:25:49 ssg1 dhclient: All rights reserved.
May 10 13:25:49 ssg1 dhclient: For info, please visit https://www.isc.org/software/dhcp/
May 10 13:25:49 ssg1 dhclient: 
May 10 13:25:49 ssg1 NetworkManager[1056]: <info> (wlan1): DHCPv4 state changed nbi -> preinit
May 10 13:25:49 ssg1 dhclient: Listening on LPF/wlan1/00:23:14:dd:2c:5c
May 10 13:25:49 ssg1 dhclient: Sending on   LPF/wlan1/00:23:14:dd:2c:5c
May 10 13:25:49 ssg1 dhclient: Sending on   Socket/fallback
May 10 13:25:49 ssg1 dhclient: DHCPREQUEST of 192.168.2.111 on wlan1 to 255.255.255.255 port 67
May 10 13:25:49 ssg1 dhclient: DHCPNAK from 192.168.2.1
May 10 13:25:49 ssg1 NetworkManager[1056]: <info> (wlan1): DHCPv4 state changed preinit -> expire
May 10 13:25:49 ssg1 dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 3
May 10 13:25:49 ssg1 NetworkManager[1056]: <info> (wlan1): DHCPv4 state changed expire -> preinit
May 10 13:25:49 ssg1 dhclient: DHCPREQUEST of 192.168.2.8 on wlan1 to 255.255.255.255 port 67
May 10 13:25:49 ssg1 dhclient: DHCPOFFER of 192.168.2.8 from 192.168.2.1
May 10 13:25:49 ssg1 dhclient: DHCPACK of 192.168.2.8 from 192.168.2.1
May 10 13:25:49 ssg1 dhclient: bound to 192.168.2.8 -- renewal in 148312537 seconds.
May 10 13:25:49 ssg1 NetworkManager[1056]: <info> (wlan1): DHCPv4 state changed preinit -> bound
May 10 13:25:49 ssg1 NetworkManager[1056]: <info>   address 192.168.2.8
May 10 13:25:49 ssg1 NetworkManager[1056]: <info>   prefix 24 (255.255.255.0)
May 10 13:25:49 ssg1 NetworkManager[1056]: <info>   gateway 192.168.2.1
May 10 13:25:49 ssg1 NetworkManager[1056]: <info>   nameserver '192.168.1.254'
May 10 13:25:49 ssg1 NetworkManager[1056]: <info>   nameserver '192.168.2.1'
May 10 13:25:49 ssg1 NetworkManager[1056]: <info>   domain name 'esr9850'
May 10 13:25:49 ssg1 NetworkManager[1056]: <info>   wins '192.168.2.1'
May 10 13:25:49 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
May 10 13:25:49 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Commit) started...
May 10 13:25:50 ssg1 NetworkManager[1056]: <info> DNS: starting dnsmasq...
May 10 13:25:50 ssg1 dnsmasq[20431]: exiting on receipt of SIGTERM
May 10 13:25:50 ssg1 NetworkManager[1056]: <info> (wlan1): writing resolv.conf to /sbin/resolvconf
May 10 13:25:50 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: ip-config -> activated (reason 'none') [70 100 0]
May 10 13:25:50 ssg1 dnsmasq[20457]: started, version 2.59 cache disabled
May 10 13:25:50 ssg1 dnsmasq[20457]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
May 10 13:25:50 ssg1 dnsmasq[20457]: using nameserver 192.168.2.1#53
May 10 13:25:50 ssg1 dnsmasq[20457]: using nameserver 192.168.1.254#53
May 10 13:25:51 ssg1 NetworkManager[1056]: <info> Policy set 'tester5 1' (wlan1) as default for IPv4 routing and DNS.
May 10 13:25:51 ssg1 NetworkManager[1056]: <info> Activation (wlan1) successful, device activated.
May 10 13:25:51 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Commit) complete.
May 10 13:25:51 ssg1 dbus[1018]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May 10 13:25:51 ssg1 dbus[1018]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 10 13:25:59 ssg1 ntpdate[20514]: adjust time server 91.189.94.4 offset 0.003968 sec
May 10 13:25:59 ssg1 kernel: [55979.104037] wlan1: no IPv6 routers present
May 10 13:26:05 ssg1 kernel: [55984.515252] pidgin[14913]: segfault at 300c ip 0d611525 sp bfec9970 error 4 in libgail.so[d5f1000+4e000]
May 10 13:26:09 ssg1 NetworkManager[1056]: <info> (wlan1): IP6 addrconf timed out or failed.
May 10 13:26:09 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May 10 13:26:09 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) started...
May 10 13:26:09 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
May 10 13:26:51 ssg1 NetworkManager[1056]: <info> (wlan1): disconnecting for new activation request.
May 10 13:26:51 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: activated -> disconnected (reason 'none') [100 30 0]
May 10 13:26:51 ssg1 NetworkManager[1056]: <info> (wlan1): deactivating device (reason 'none') [0]
May 10 13:26:51 ssg1 NetworkManager[1056]: <info> (wlan1): canceled DHCP transaction, DHCP client pid 20452
May 10 13:26:51 ssg1 dnsmasq[20457]: exiting on receipt of SIGTERM
May 10 13:26:51 ssg1 NetworkManager[1056]: <info> DNS: starting dnsmasq...
May 10 13:26:51 ssg1 NetworkManager[1056]: <info> (wlan1): writing resolv.conf to /sbin/resolvconf
May 10 13:26:51 ssg1 dbus[1018]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May 10 13:26:51 ssg1 NetworkManager[1056]: <info> Activation (wlan1) starting connection 'carbon'
May 10 13:26:51 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 10 13:26:51 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
May 10 13:26:51 ssg1 kernel: [56031.251714] wlan1: deauthenticating from 10:bf:48:3c:a3:dc by local choice (reason=3)
May 10 13:26:51 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
May 10 13:26:51 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
May 10 13:26:51 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
May 10 13:26:51 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
May 10 13:26:51 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: prepare -> config (reason 'none') [40 50 0]
May 10 13:26:51 ssg1 dbus[1018]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 10 13:26:52 ssg1 dnsmasq[21089]: started, version 2.59 cache disabled
May 10 13:26:52 ssg1 dnsmasq[21089]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
May 10 13:26:52 ssg1 dnsmasq[21089]: warning: no upstream servers configured
May 10 13:26:52 ssg1 wpa_supplicant[1260]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
May 10 13:26:52 ssg1 kernel: [56031.304280] cfg80211: All devices are disconnected, going to restore regulatory settings
May 10 13:26:52 ssg1 kernel: [56031.304288] cfg80211: Restoring regulatory settings
May 10 13:26:52 ssg1 kernel: [56031.304293] cfg80211: Calling CRDA to update world regulatory domain
May 10 13:26:52 ssg1 NetworkManager[1056]: <info> Activation (wlan1/wireless): access point 'carbon' has security, but secrets are required.
May 10 13:26:52 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: config -> need-auth (reason 'none') [50 60 0]
May 10 13:26:52 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
May 10 13:26:52 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: completed -> disconnected
May 10 13:26:52 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
May 10 13:26:52 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
May 10 13:26:52 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: need-auth -> prepare (reason 'none') [60 40 0]
May 10 13:26:52 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
May 10 13:26:52 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
May 10 13:26:52 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
May 10 13:26:52 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: prepare -> config (reason 'none') [40 50 0]
May 10 13:26:52 ssg1 kernel: [56031.313601] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
May 10 13:26:52 ssg1 kernel: [56031.313605] cfg80211: World regulatory domain updated:
May 10 13:26:52 ssg1 kernel: [56031.313608] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May 10 13:26:52 ssg1 kernel: [56031.313611] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 13:26:52 ssg1 kernel: [56031.313615] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 10 13:26:52 ssg1 kernel: [56031.313618] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 10 13:26:52 ssg1 kernel: [56031.313621] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 13:26:52 ssg1 kernel: [56031.313624] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 13:26:52 ssg1 NetworkManager[1056]: <info> Activation (wlan1/wireless): connection 'carbon' has security, and secrets exist.  No new secrets needed.
May 10 13:26:52 ssg1 NetworkManager[1056]: <info> Config: added 'ssid' value 'carbon'
May 10 13:26:52 ssg1 NetworkManager[1056]: <info> Config: added 'scan_ssid' value '1'
May 10 13:26:52 ssg1 NetworkManager[1056]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
May 10 13:26:52 ssg1 NetworkManager[1056]: <info> Config: added 'auth_alg' value 'OPEN'
May 10 13:26:52 ssg1 NetworkManager[1056]: <info> Config: added 'psk' value '<omitted>'
May 10 13:26:52 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
May 10 13:26:52 ssg1 NetworkManager[1056]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
May 10 13:26:52 ssg1 NetworkManager[1056]: <info> Config: set interface ap_scan to 1
May 10 13:26:52 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: disconnected -> scanning
May 10 13:26:55 ssg1 wpa_supplicant[1260]: Trying to authenticate with a0:f3:c1:c1:18:ea (SSID='carbon' freq=2412 MHz)
May 10 13:26:55 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: scanning -> authenticating
May 10 13:26:55 ssg1 kernel: [56034.618583] wlan1: authenticate with a0:f3:c1:c1:18:ea (try 1)
May 10 13:26:55 ssg1 wpa_supplicant[1260]: Trying to associate with a0:f3:c1:c1:18:ea (SSID='carbon' freq=2412 MHz)
May 10 13:26:55 ssg1 kernel: [56034.621134] wlan1: authenticated
May 10 13:26:55 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: authenticating -> associating
May 10 13:26:55 ssg1 kernel: [56034.693074] wlan1: waiting for beacon from a0:f3:c1:c1:18:ea
May 10 13:26:55 ssg1 kernel: [56034.706846] wlan1: beacon received
May 10 13:26:55 ssg1 kernel: [56034.716037] wlan1: associate with a0:f3:c1:c1:18:ea (try 1)
May 10 13:26:55 ssg1 kernel: [56034.720092] wlan1: RX AssocResp from a0:f3:c1:c1:18:ea (capab=0x431 status=0 aid=1)
May 10 13:26:55 ssg1 kernel: [56034.720097] wlan1: associated
May 10 13:26:55 ssg1 kernel: [56034.720103] wlan1: No basic rates in AssocResp. Using min supported rate instead.
May 10 13:26:55 ssg1 wpa_supplicant[1260]: Associated with a0:f3:c1:c1:18:ea
May 10 13:26:55 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: associating -> associated
May 10 13:26:56 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: associated -> 4-way handshake
May 10 13:26:56 ssg1 wpa_supplicant[1260]: WPA: Key negotiation completed with a0:f3:c1:c1:18:ea [PTK=CCMP GTK=CCMP]
May 10 13:26:56 ssg1 wpa_supplicant[1260]: CTRL-EVENT-CONNECTED - Connection to a0:f3:c1:c1:18:ea completed (reauth) [id=0 id_str=]
May 10 13:26:56 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: 4-way handshake -> completed
May 10 13:26:56 ssg1 NetworkManager[1056]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'carbon'.
May 10 13:26:56 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) scheduled.
May 10 13:26:56 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) started...
May 10 13:26:56 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: config -> ip-config (reason 'none') [50 70 0]
May 10 13:26:56 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Beginning DHCPv4 transaction (timeout in 45 seconds)
May 10 13:26:56 ssg1 NetworkManager[1056]: <info> dhclient started with pid 21226
May 10 13:26:56 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Beginning IP6 addrconf.
May 10 13:26:56 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) complete.
May 10 13:26:56 ssg1 dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
May 10 13:26:56 ssg1 dhclient: Copyright 2004-2011 Internet Systems Consortium.
May 10 13:26:56 ssg1 dhclient: All rights reserved.
May 10 13:26:56 ssg1 dhclient: For info, please visit https://www.isc.org/software/dhcp/
May 10 13:26:56 ssg1 dhclient: 
May 10 13:26:56 ssg1 NetworkManager[1056]: <info> (wlan1): DHCPv4 state changed nbi -> preinit
May 10 13:26:56 ssg1 dhclient: Listening on LPF/wlan1/00:23:14:dd:2c:5c
May 10 13:26:56 ssg1 dhclient: Sending on   LPF/wlan1/00:23:14:dd:2c:5c
May 10 13:26:56 ssg1 dhclient: Sending on   Socket/fallback
May 10 13:26:56 ssg1 dhclient: DHCPREQUEST of 192.168.2.8 on wlan1 to 255.255.255.255 port 67
May 10 13:26:56 ssg1 dhclient: DHCPACK of 192.168.2.8 from 192.168.2.1
May 10 13:26:56 ssg1 dhclient: bound to 192.168.2.8 -- renewal in 150943398 seconds.
May 10 13:26:56 ssg1 NetworkManager[1056]: <info> (wlan1): DHCPv4 state changed preinit -> reboot
May 10 13:26:56 ssg1 NetworkManager[1056]: <info>   address 192.168.2.8
May 10 13:26:56 ssg1 NetworkManager[1056]: <info>   prefix 24 (255.255.255.0)
May 10 13:26:56 ssg1 NetworkManager[1056]: <info>   gateway 192.168.2.1
May 10 13:26:56 ssg1 NetworkManager[1056]: <info>   nameserver '192.168.1.254'
May 10 13:26:56 ssg1 NetworkManager[1056]: <info>   nameserver '192.168.2.1'
May 10 13:26:56 ssg1 NetworkManager[1056]: <info>   domain name 'esr9850'
May 10 13:26:56 ssg1 NetworkManager[1056]: <info>   wins '192.168.2.1'
May 10 13:26:56 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
May 10 13:26:56 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Commit) started...
May 10 13:26:57 ssg1 NetworkManager[1056]: <info> DNS: starting dnsmasq...
May 10 13:26:57 ssg1 dnsmasq[21089]: exiting on receipt of SIGTERM
May 10 13:26:57 ssg1 NetworkManager[1056]: <info> (wlan1): writing resolv.conf to /sbin/resolvconf
May 10 13:26:57 ssg1 dnsmasq[21239]: started, version 2.59 cache disabled
May 10 13:26:57 ssg1 dnsmasq[21239]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
May 10 13:26:57 ssg1 dnsmasq[21239]: using nameserver 192.168.2.1#53
May 10 13:26:57 ssg1 dnsmasq[21239]: using nameserver 192.168.1.254#53
May 10 13:26:57 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: ip-config -> activated (reason 'none') [70 100 0]
May 10 13:26:57 ssg1 NetworkManager[1056]: <info> Policy set 'carbon' (wlan1) as default for IPv4 routing and DNS.
May 10 13:26:57 ssg1 NetworkManager[1056]: <info> Activation (wlan1) successful, device activated.
May 10 13:26:57 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Commit) complete.
May 10 13:27:06 ssg1 ntpdate[21283]: adjust time server 91.189.94.4 offset -0.003890 sec
May 10 13:27:06 ssg1 kernel: [56045.936021] wlan1: no IPv6 routers present
May 10 13:27:16 ssg1 NetworkManager[1056]: <info> (wlan1): IP6 addrconf timed out or failed.
May 10 13:27:16 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May 10 13:27:16 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) started...
May 10 13:27:16 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
May 10 13:35:01 ssg1 CRON[21563]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
May 10 13:38:50 ssg1 NetworkManager[1056]: <info> disable requested (sleeping: no  enabled: yes)
May 10 13:38:50 ssg1 NetworkManager[1056]: <info> sleeping or disabling...
May 10 13:38:50 ssg1 NetworkManager[1056]: <info> (eth0): now unmanaged
May 10 13:38:50 ssg1 NetworkManager[1056]: <info> (eth0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
May 10 13:38:50 ssg1 NetworkManager[1056]: <info> (eth0): cleaning up...
May 10 13:38:50 ssg1 NetworkManager[1056]: <info> (eth0): taking down device.
May 10 13:38:50 ssg1 NetworkManager[1056]: <info> (wlan1): now unmanaged
May 10 13:38:50 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: activated -> unmanaged (reason 'sleeping') [100 10 37]
May 10 13:38:50 ssg1 NetworkManager[1056]: <info> (wlan1): deactivating device (reason 'sleeping') [37]
May 10 13:38:50 ssg1 NetworkManager[1056]: <info> (wlan1): canceled DHCP transaction, DHCP client pid 21226
May 10 13:38:50 ssg1 kernel: [56750.006655] wlan1: deauthenticating from a0:f3:c1:c1:18:ea by local choice (reason=3)
May 10 13:38:50 ssg1 kernel: [56750.056706] cfg80211: All devices are disconnected, going to restore regulatory settings
May 10 13:38:50 ssg1 kernel: [56750.056717] cfg80211: Restoring regulatory settings
May 10 13:38:50 ssg1 kernel: [56750.056744] cfg80211: Calling CRDA to update world regulatory domain
May 10 13:38:50 ssg1 wpa_supplicant[1260]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
May 10 13:38:50 ssg1 dnsmasq[21239]: exiting on receipt of SIGTERM
May 10 13:38:50 ssg1 NetworkManager[1056]: <info> DNS: starting dnsmasq...
May 10 13:38:50 ssg1 kernel: [56750.062764] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
May 10 13:38:50 ssg1 kernel: [56750.062769] cfg80211: World regulatory domain updated:
May 10 13:38:50 ssg1 kernel: [56750.062772] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May 10 13:38:50 ssg1 kernel: [56750.062775] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 13:38:50 ssg1 kernel: [56750.062779] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 10 13:38:50 ssg1 kernel: [56750.062782] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 10 13:38:50 ssg1 kernel: [56750.062785] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 13:38:50 ssg1 kernel: [56750.062788] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 13:38:50 ssg1 NetworkManager[1056]: <info> (wlan1): writing resolv.conf to /sbin/resolvconf
May 10 13:38:50 ssg1 dnsmasq[21584]: started, version 2.59 cache disabled
May 10 13:38:50 ssg1 dnsmasq[21584]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
May 10 13:38:50 ssg1 dnsmasq[21584]: warning: no upstream servers configured
May 10 13:38:50 ssg1 NetworkManager[1056]: <info> (wlan1): cleaning up...
May 10 13:38:50 ssg1 NetworkManager[1056]: <info> (wlan1): taking down device.
May 10 13:38:50 ssg1 dbus[1018]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May 10 13:38:50 ssg1 dbus[1018]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 10 13:39:04 ssg1 NetworkManager[1056]: <info> enable requested (sleeping: no  enabled: no)
May 10 13:39:04 ssg1 NetworkManager[1056]: <info> waking up and re-enabling...
May 10 13:39:04 ssg1 NetworkManager[1056]: <info> WWAN now enabled by management service
May 10 13:39:04 ssg1 NetworkManager[1056]: <info> (eth0): now managed
May 10 13:39:04 ssg1 NetworkManager[1056]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May 10 13:39:04 ssg1 NetworkManager[1056]: <info> (eth0): bringing up device.
May 10 13:39:04 ssg1 NetworkManager[1056]: <info> (eth0): preparing device.
May 10 13:39:04 ssg1 NetworkManager[1056]: <info> (eth0): deactivating device (reason 'managed') [2]
May 10 13:39:04 ssg1 NetworkManager[1056]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May 10 13:39:04 ssg1 NetworkManager[1056]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May 10 13:39:04 ssg1 NetworkManager[1056]: <info> (wlan1): now managed
May 10 13:39:04 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May 10 13:39:04 ssg1 NetworkManager[1056]: <info> (wlan1): bringing up device.
May 10 13:39:04 ssg1 kernel: [56763.301253] r8169 0000:02:00.0: eth0: link down
May 10 13:39:04 ssg1 kernel: [56763.301495] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 10 13:39:04 ssg1 kernel: [56763.304578] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
May 10 13:39:04 ssg1 kernel: [56763.311482] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x1
May 10 13:39:04 ssg1 NetworkManager[1056]: <info> (wlan1): preparing device.
May 10 13:39:04 ssg1 NetworkManager[1056]: <info> (wlan1): deactivating device (reason 'managed') [2]
May 10 13:39:04 ssg1 kernel: [56763.433274] ADDRCONF(NETDEV_UP): wlan1: link is not ready
May 10 13:39:04 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: starting -> ready
May 10 13:39:04 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
May 10 13:39:04 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: ready -> inactive
May 10 13:39:04 ssg1 NetworkManager[1056]: <warn> Trying to remove a non-existant call id.
May 10 13:39:08 ssg1 NetworkManager[1056]: <info> Auto-activating connection 'carbon'.
May 10 13:39:08 ssg1 NetworkManager[1056]: <info> Activation (wlan1) starting connection 'carbon'
May 10 13:39:08 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 10 13:39:08 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
May 10 13:39:08 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
May 10 13:39:08 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
May 10 13:39:08 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
May 10 13:39:08 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
May 10 13:39:08 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: prepare -> config (reason 'none') [40 50 0]
May 10 13:39:08 ssg1 NetworkManager[1056]: <info> Activation (wlan1/wireless): access point 'carbon' has security, but secrets are required.
May 10 13:39:08 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: config -> need-auth (reason 'none') [50 60 0]
May 10 13:39:08 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
May 10 13:39:08 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
May 10 13:39:08 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
May 10 13:39:08 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: need-auth -> prepare (reason 'none') [60 40 0]
May 10 13:39:08 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
May 10 13:39:08 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
May 10 13:39:08 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
May 10 13:39:08 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: prepare -> config (reason 'none') [40 50 0]
May 10 13:39:08 ssg1 NetworkManager[1056]: <info> Activation (wlan1/wireless): connection 'carbon' has security, and secrets exist.  No new secrets needed.
May 10 13:39:08 ssg1 NetworkManager[1056]: <info> Config: added 'ssid' value 'carbon'
May 10 13:39:08 ssg1 NetworkManager[1056]: <info> Config: added 'scan_ssid' value '1'
May 10 13:39:08 ssg1 NetworkManager[1056]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
May 10 13:39:08 ssg1 NetworkManager[1056]: <info> Config: added 'auth_alg' value 'OPEN'
May 10 13:39:08 ssg1 NetworkManager[1056]: <info> Config: added 'psk' value '<omitted>'
May 10 13:39:08 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
May 10 13:39:08 ssg1 NetworkManager[1056]: <info> Config: set interface ap_scan to 1
May 10 13:39:08 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: inactive -> scanning
May 10 13:39:11 ssg1 wpa_supplicant[1260]: Trying to authenticate with a0:f3:c1:c1:18:ea (SSID='carbon' freq=2412 MHz)
May 10 13:39:11 ssg1 wpa_supplicant[1260]: Trying to associate with a0:f3:c1:c1:18:ea (SSID='carbon' freq=2412 MHz)
May 10 13:39:11 ssg1 kernel: [56771.048894] wlan1: authenticate with a0:f3:c1:c1:18:ea (try 1)
May 10 13:39:11 ssg1 kernel: [56771.051136] wlan1: authenticated
May 10 13:39:11 ssg1 kernel: [56771.051572] wlan1: associate with a0:f3:c1:c1:18:ea (try 1)
May 10 13:39:11 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: scanning -> associating
May 10 13:39:11 ssg1 kernel: [56771.055606] wlan1: RX AssocResp from a0:f3:c1:c1:18:ea (capab=0x431 status=0 aid=1)
May 10 13:39:11 ssg1 kernel: [56771.055610] wlan1: associated
May 10 13:39:11 ssg1 kernel: [56771.055614] wlan1: No basic rates in AssocResp. Using min supported rate instead.
May 10 13:39:11 ssg1 kernel: [56771.063526] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
May 10 13:39:11 ssg1 wpa_supplicant[1260]: Associated with a0:f3:c1:c1:18:ea
May 10 13:39:11 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: associating -> associated
May 10 13:39:12 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: associated -> 4-way handshake
May 10 13:39:12 ssg1 wpa_supplicant[1260]: WPA: Key negotiation completed with a0:f3:c1:c1:18:ea [PTK=CCMP GTK=CCMP]
May 10 13:39:12 ssg1 wpa_supplicant[1260]: CTRL-EVENT-CONNECTED - Connection to a0:f3:c1:c1:18:ea completed (auth) [id=0 id_str=]
May 10 13:39:12 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: 4-way handshake -> completed
May 10 13:39:12 ssg1 NetworkManager[1056]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'carbon'.
May 10 13:39:12 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) scheduled.
May 10 13:39:12 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) started...
May 10 13:39:12 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: config -> ip-config (reason 'none') [50 70 0]
May 10 13:39:12 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Beginning DHCPv4 transaction (timeout in 45 seconds)
May 10 13:39:12 ssg1 dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
May 10 13:39:12 ssg1 NetworkManager[1056]: <info> dhclient started with pid 21605
May 10 13:39:12 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Beginning IP6 addrconf.
May 10 13:39:12 ssg1 dhclient: Copyright 2004-2011 Internet Systems Consortium.
May 10 13:39:12 ssg1 dhclient: All rights reserved.
May 10 13:39:12 ssg1 dhclient: For info, please visit https://www.isc.org/software/dhcp/
May 10 13:39:12 ssg1 dhclient: 
May 10 13:39:12 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) complete.
May 10 13:39:12 ssg1 NetworkManager[1056]: <info> (wlan1): DHCPv4 state changed nbi -> preinit
May 10 13:39:12 ssg1 dhclient: Listening on LPF/wlan1/00:23:14:dd:2c:5c
May 10 13:39:12 ssg1 dhclient: Sending on   LPF/wlan1/00:23:14:dd:2c:5c
May 10 13:39:12 ssg1 dhclient: Sending on   Socket/fallback
May 10 13:39:12 ssg1 dhclient: DHCPREQUEST of 192.168.2.8 on wlan1 to 255.255.255.255 port 67
May 10 13:39:12 ssg1 dhclient: DHCPACK of 192.168.2.8 from 192.168.2.1
May 10 13:39:12 ssg1 dhclient: bound to 192.168.2.8 -- renewal in 156915567 seconds.
May 10 13:39:12 ssg1 NetworkManager[1056]: <info> (wlan1): DHCPv4 state changed preinit -> reboot
May 10 13:39:12 ssg1 NetworkManager[1056]: <info>   address 192.168.2.8
May 10 13:39:12 ssg1 NetworkManager[1056]: <info>   prefix 24 (255.255.255.0)
May 10 13:39:12 ssg1 NetworkManager[1056]: <info>   gateway 192.168.2.1
May 10 13:39:12 ssg1 NetworkManager[1056]: <info>   nameserver '192.168.1.254'
May 10 13:39:12 ssg1 NetworkManager[1056]: <info>   nameserver '192.168.2.1'
May 10 13:39:12 ssg1 NetworkManager[1056]: <info>   domain name 'esr9850'
May 10 13:39:12 ssg1 NetworkManager[1056]: <info>   wins '192.168.2.1'
May 10 13:39:12 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
May 10 13:39:12 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Commit) started...
May 10 13:39:13 ssg1 dnsmasq[21584]: exiting on receipt of SIGTERM
May 10 13:39:13 ssg1 NetworkManager[1056]: <info> DNS: starting dnsmasq...
May 10 13:39:13 ssg1 NetworkManager[1056]: <info> (wlan1): writing resolv.conf to /sbin/resolvconf
May 10 13:39:13 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: ip-config -> activated (reason 'none') [70 100 0]
May 10 13:39:13 ssg1 dnsmasq[21610]: started, version 2.59 cache disabled
May 10 13:39:13 ssg1 dnsmasq[21610]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
May 10 13:39:13 ssg1 dnsmasq[21610]: using nameserver 192.168.2.1#53
May 10 13:39:13 ssg1 dnsmasq[21610]: using nameserver 192.168.1.254#53
May 10 13:39:14 ssg1 NetworkManager[1056]: <info> Policy set 'carbon' (wlan1) as default for IPv4 routing and DNS.
May 10 13:39:14 ssg1 NetworkManager[1056]: <info> Activation (wlan1) successful, device activated.
May 10 13:39:14 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Commit) complete.
May 10 13:39:14 ssg1 dbus[1018]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May 10 13:39:14 ssg1 dbus[1018]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 10 13:39:22 ssg1 ntpdate[21655]: adjust time server 91.189.94.4 offset 0.000939 sec
May 10 13:39:23 ssg1 kernel: [56782.832063] wlan1: no IPv6 routers present
May 10 13:39:32 ssg1 NetworkManager[1056]: <info> (wlan1): IP6 addrconf timed out or failed.
May 10 13:39:32 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May 10 13:39:32 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) started...
May 10 13:39:32 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
May 10 13:45:01 ssg1 CRON[21829]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
May 10 13:48:08 ssg1 NetworkManager[1056]: <info> disable requested (sleeping: no  enabled: yes)
May 10 13:48:08 ssg1 NetworkManager[1056]: <info> sleeping or disabling...
May 10 13:48:08 ssg1 NetworkManager[1056]: <info> (eth0): now unmanaged
May 10 13:48:08 ssg1 NetworkManager[1056]: <info> (eth0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
May 10 13:48:08 ssg1 NetworkManager[1056]: <info> (eth0): cleaning up...
May 10 13:48:08 ssg1 NetworkManager[1056]: <info> (eth0): taking down device.
May 10 13:48:08 ssg1 NetworkManager[1056]: <info> (wlan1): now unmanaged
May 10 13:48:08 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: activated -> unmanaged (reason 'sleeping') [100 10 37]
May 10 13:48:08 ssg1 NetworkManager[1056]: <info> (wlan1): deactivating device (reason 'sleeping') [37]
May 10 13:48:08 ssg1 NetworkManager[1056]: <info> (wlan1): canceled DHCP transaction, DHCP client pid 21605
May 10 13:48:08 ssg1 NetworkManager[1056]: <info> DNS: starting dnsmasq...
May 10 13:48:08 ssg1 dnsmasq[21610]: exiting on receipt of SIGTERM
May 10 13:48:08 ssg1 NetworkManager[1056]: <info> (wlan1): writing resolv.conf to /sbin/resolvconf
May 10 13:48:08 ssg1 NetworkManager[1056]: <info> (wlan1): cleaning up...
May 10 13:48:08 ssg1 kernel: [57307.792174] wlan1: deauthenticating from a0:f3:c1:c1:18:ea by local choice (reason=3)
May 10 13:48:08 ssg1 wpa_supplicant[1260]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
May 10 13:48:08 ssg1 kernel: [57307.832336] cfg80211: All devices are disconnected, going to restore regulatory settings
May 10 13:48:08 ssg1 kernel: [57307.832347] cfg80211: Restoring regulatory settings
May 10 13:48:08 ssg1 kernel: [57307.832356] cfg80211: Calling CRDA to update world regulatory domain
May 10 13:48:08 ssg1 dnsmasq[21848]: started, version 2.59 cache disabled
May 10 13:48:08 ssg1 dnsmasq[21848]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
May 10 13:48:08 ssg1 dnsmasq[21848]: warning: no upstream servers configured
May 10 13:48:08 ssg1 NetworkManager[1056]: <info> (wlan1): taking down device.
May 10 13:48:08 ssg1 kernel: [57307.840249] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
May 10 13:48:08 ssg1 kernel: [57307.840253] cfg80211: World regulatory domain updated:
May 10 13:48:08 ssg1 kernel: [57307.840256] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May 10 13:48:08 ssg1 kernel: [57307.840259] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 13:48:08 ssg1 kernel: [57307.840263] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 10 13:48:08 ssg1 kernel: [57307.840266] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 10 13:48:08 ssg1 kernel: [57307.840269] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 13:48:08 ssg1 kernel: [57307.840272] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 13:48:08 ssg1 dbus[1018]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May 10 13:48:08 ssg1 dbus[1018]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 10 13:48:21 ssg1 NetworkManager[1056]: <info> enable requested (sleeping: no  enabled: no)
May 10 13:48:21 ssg1 NetworkManager[1056]: <info> waking up and re-enabling...
May 10 13:48:21 ssg1 NetworkManager[1056]: <info> (eth0): now managed
May 10 13:48:21 ssg1 NetworkManager[1056]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May 10 13:48:21 ssg1 NetworkManager[1056]: <info> (eth0): bringing up device.
May 10 13:48:21 ssg1 NetworkManager[1056]: <info> (eth0): preparing device.
May 10 13:48:21 ssg1 NetworkManager[1056]: <info> (eth0): deactivating device (reason 'managed') [2]
May 10 13:48:21 ssg1 NetworkManager[1056]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May 10 13:48:21 ssg1 NetworkManager[1056]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May 10 13:48:21 ssg1 NetworkManager[1056]: <info> (wlan1): now managed
May 10 13:48:21 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May 10 13:48:21 ssg1 NetworkManager[1056]: <info> (wlan1): bringing up device.
May 10 13:48:21 ssg1 kernel: [57320.420468] r8169 0000:02:00.0: eth0: link down
May 10 13:48:21 ssg1 kernel: [57320.420705] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 10 13:48:21 ssg1 kernel: [57320.422558] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
May 10 13:48:21 ssg1 kernel: [57320.429418] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x1
May 10 13:48:21 ssg1 NetworkManager[1056]: <info> (wlan1): preparing device.
May 10 13:48:21 ssg1 NetworkManager[1056]: <info> (wlan1): deactivating device (reason 'managed') [2]
May 10 13:48:21 ssg1 kernel: [57320.553608] ADDRCONF(NETDEV_UP): wlan1: link is not ready
May 10 13:48:21 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: starting -> ready
May 10 13:48:21 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
May 10 13:48:21 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: ready -> inactive
May 10 13:48:21 ssg1 NetworkManager[1056]: <warn> Trying to remove a non-existant call id.
May 10 13:48:25 ssg1 NetworkManager[1056]: <info> Auto-activating connection 'carbon'.
May 10 13:48:25 ssg1 NetworkManager[1056]: <info> Activation (wlan1) starting connection 'carbon'
May 10 13:48:25 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 10 13:48:25 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
May 10 13:48:25 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
May 10 13:48:25 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
May 10 13:48:25 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
May 10 13:48:25 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
May 10 13:48:25 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: prepare -> config (reason 'none') [40 50 0]
May 10 13:48:25 ssg1 NetworkManager[1056]: <info> Activation (wlan1/wireless): access point 'carbon' has security, but secrets are required.
May 10 13:48:25 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: config -> need-auth (reason 'none') [50 60 0]
May 10 13:48:25 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
May 10 13:48:25 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
May 10 13:48:25 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
May 10 13:48:25 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: need-auth -> prepare (reason 'none') [60 40 0]
May 10 13:48:25 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
May 10 13:48:25 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
May 10 13:48:25 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
May 10 13:48:25 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: prepare -> config (reason 'none') [40 50 0]
May 10 13:48:25 ssg1 NetworkManager[1056]: <info> Activation (wlan1/wireless): connection 'carbon' has security, and secrets exist.  No new secrets needed.
May 10 13:48:25 ssg1 NetworkManager[1056]: <info> Config: added 'ssid' value 'carbon'
May 10 13:48:25 ssg1 NetworkManager[1056]: <info> Config: added 'scan_ssid' value '1'
May 10 13:48:25 ssg1 NetworkManager[1056]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
May 10 13:48:25 ssg1 NetworkManager[1056]: <info> Config: added 'auth_alg' value 'OPEN'
May 10 13:48:25 ssg1 NetworkManager[1056]: <info> Config: added 'psk' value '<omitted>'
May 10 13:48:25 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
May 10 13:48:25 ssg1 NetworkManager[1056]: <info> Config: set interface ap_scan to 1
May 10 13:48:25 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: inactive -> scanning
May 10 13:48:29 ssg1 wpa_supplicant[1260]: Trying to authenticate with a0:f3:c1:c1:18:ea (SSID='carbon' freq=2412 MHz)
May 10 13:48:29 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: scanning -> authenticating
May 10 13:48:29 ssg1 wpa_supplicant[1260]: Trying to associate with a0:f3:c1:c1:18:ea (SSID='carbon' freq=2412 MHz)
May 10 13:48:29 ssg1 kernel: [57328.325235] wlan1: authenticate with a0:f3:c1:c1:18:ea (try 1)
May 10 13:48:29 ssg1 kernel: [57328.327466] wlan1: authenticated
May 10 13:48:29 ssg1 kernel: [57328.327859] wlan1: associate with a0:f3:c1:c1:18:ea (try 1)
May 10 13:48:29 ssg1 kernel: [57328.331932] wlan1: RX AssocResp from a0:f3:c1:c1:18:ea (capab=0x431 status=0 aid=1)
May 10 13:48:29 ssg1 kernel: [57328.331936] wlan1: associated
May 10 13:48:29 ssg1 kernel: [57328.331940] wlan1: No basic rates in AssocResp. Using min supported rate instead.
May 10 13:48:29 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: authenticating -> associating
May 10 13:48:29 ssg1 wpa_supplicant[1260]: Associated with a0:f3:c1:c1:18:ea
May 10 13:48:29 ssg1 kernel: [57328.340170] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
May 10 13:48:29 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: associating -> associated
May 10 13:48:30 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: associated -> 4-way handshake
May 10 13:48:30 ssg1 wpa_supplicant[1260]: WPA: Key negotiation completed with a0:f3:c1:c1:18:ea [PTK=CCMP GTK=CCMP]
May 10 13:48:30 ssg1 wpa_supplicant[1260]: CTRL-EVENT-CONNECTED - Connection to a0:f3:c1:c1:18:ea completed (auth) [id=0 id_str=]
May 10 13:48:30 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: 4-way handshake -> completed
May 10 13:48:30 ssg1 NetworkManager[1056]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'carbon'.
May 10 13:48:30 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) scheduled.
May 10 13:48:30 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) started...
May 10 13:48:30 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: config -> ip-config (reason 'none') [50 70 0]
May 10 13:48:30 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Beginning DHCPv4 transaction (timeout in 45 seconds)
May 10 13:48:30 ssg1 NetworkManager[1056]: <info> dhclient started with pid 21872
May 10 13:48:30 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Beginning IP6 addrconf.
May 10 13:48:30 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) complete.
May 10 13:48:30 ssg1 dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
May 10 13:48:30 ssg1 dhclient: Copyright 2004-2011 Internet Systems Consortium.
May 10 13:48:30 ssg1 dhclient: All rights reserved.
May 10 13:48:30 ssg1 dhclient: For info, please visit https://www.isc.org/software/dhcp/
May 10 13:48:30 ssg1 dhclient: 
May 10 13:48:30 ssg1 NetworkManager[1056]: <info> (wlan1): DHCPv4 state changed nbi -> preinit
May 10 13:48:30 ssg1 dhclient: Listening on LPF/wlan1/00:23:14:dd:2c:5c
May 10 13:48:30 ssg1 dhclient: Sending on   LPF/wlan1/00:23:14:dd:2c:5c
May 10 13:48:30 ssg1 dhclient: Sending on   Socket/fallback
May 10 13:48:30 ssg1 dhclient: DHCPREQUEST of 192.168.2.8 on wlan1 to 255.255.255.255 port 67
May 10 13:48:30 ssg1 dhclient: DHCPACK of 192.168.2.8 from 192.168.2.1
May 10 13:48:30 ssg1 dhclient: bound to 192.168.2.8 -- renewal in 153843775 seconds.
May 10 13:48:30 ssg1 NetworkManager[1056]: <info> (wlan1): DHCPv4 state changed preinit -> reboot
May 10 13:48:30 ssg1 NetworkManager[1056]: <info>   address 192.168.2.8
May 10 13:48:30 ssg1 NetworkManager[1056]: <info>   prefix 24 (255.255.255.0)
May 10 13:48:30 ssg1 NetworkManager[1056]: <info>   gateway 192.168.2.1
May 10 13:48:30 ssg1 NetworkManager[1056]: <info>   nameserver '192.168.1.254'
May 10 13:48:30 ssg1 NetworkManager[1056]: <info>   nameserver '192.168.2.1'
May 10 13:48:30 ssg1 NetworkManager[1056]: <info>   domain name 'esr9850'
May 10 13:48:30 ssg1 NetworkManager[1056]: <info>   wins '192.168.2.1'
May 10 13:48:30 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
May 10 13:48:30 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Commit) started...
May 10 13:48:31 ssg1 NetworkManager[1056]: <info> DNS: starting dnsmasq...
May 10 13:48:31 ssg1 dnsmasq[21848]: exiting on receipt of SIGTERM
May 10 13:48:31 ssg1 NetworkManager[1056]: <info> (wlan1): writing resolv.conf to /sbin/resolvconf
May 10 13:48:31 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: ip-config -> activated (reason 'none') [70 100 0]
May 10 13:48:31 ssg1 dnsmasq[21875]: started, version 2.59 cache disabled
May 10 13:48:31 ssg1 dnsmasq[21875]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
May 10 13:48:31 ssg1 dnsmasq[21875]: using nameserver 192.168.2.1#53
May 10 13:48:31 ssg1 dnsmasq[21875]: using nameserver 192.168.1.254#53
May 10 13:48:31 ssg1 NetworkManager[1056]: <info> Policy set 'carbon' (wlan1) as default for IPv4 routing and DNS.
May 10 13:48:31 ssg1 NetworkManager[1056]: <info> Activation (wlan1) successful, device activated.
May 10 13:48:31 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Commit) complete.
May 10 13:48:31 ssg1 dbus[1018]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May 10 13:48:31 ssg1 dbus[1018]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 10 13:48:39 ssg1 ntpdate[21921]: adjust time server 91.189.94.4 offset -0.012701 sec
May 10 13:48:40 ssg1 kernel: [57339.680046] wlan1: no IPv6 routers present
May 10 13:48:50 ssg1 NetworkManager[1056]: <info> (wlan1): IP6 addrconf timed out or failed.
May 10 13:48:50 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May 10 13:48:50 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) started...
May 10 13:48:50 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
May 10 13:52:04 ssg1 wpa_supplicant[1260]: CTRL-EVENT-DISCONNECTED bssid=a0:f3:c1:c1:18:ea reason=4
May 10 13:52:04 ssg1 kernel: [57544.036198] cfg80211: All devices are disconnected, going to restore regulatory settings
May 10 13:52:04 ssg1 kernel: [57544.036208] cfg80211: Restoring regulatory settings
May 10 13:52:04 ssg1 kernel: [57544.036216] cfg80211: Calling CRDA to update world regulatory domain
May 10 13:52:04 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: completed -> disconnected
May 10 13:52:04 ssg1 kernel: [57544.041495] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
May 10 13:52:04 ssg1 kernel: [57544.041499] cfg80211: World regulatory domain updated:
May 10 13:52:04 ssg1 kernel: [57544.041501] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May 10 13:52:04 ssg1 kernel: [57544.041504] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 13:52:04 ssg1 kernel: [57544.041508] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 10 13:52:04 ssg1 kernel: [57544.041511] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 10 13:52:04 ssg1 kernel: [57544.041514] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 13:52:04 ssg1 kernel: [57544.041520] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 13:52:04 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: disconnected -> scanning
May 10 13:52:08 ssg1 wpa_supplicant[1260]: Trying to authenticate with a0:f3:c1:c1:18:ea (SSID='carbon' freq=2412 MHz)
May 10 13:52:08 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: scanning -> authenticating
May 10 13:52:08 ssg1 kernel: [57547.342344] wlan1: authenticate with a0:f3:c1:c1:18:ea (try 1)
May 10 13:52:08 ssg1 wpa_supplicant[1260]: Trying to associate with a0:f3:c1:c1:18:ea (SSID='carbon' freq=2412 MHz)
May 10 13:52:08 ssg1 kernel: [57547.344568] wlan1: authenticated
May 10 13:52:08 ssg1 kernel: [57547.345096] wlan1: associate with a0:f3:c1:c1:18:ea (try 1)
May 10 13:52:08 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: authenticating -> associating
May 10 13:52:08 ssg1 kernel: [57547.349213] wlan1: RX ReassocResp from a0:f3:c1:c1:18:ea (capab=0x431 status=0 aid=1)
May 10 13:52:08 ssg1 kernel: [57547.349217] wlan1: associated
May 10 13:52:08 ssg1 kernel: [57547.349221] wlan1: No basic rates in AssocResp. Using min supported rate instead.
May 10 13:52:08 ssg1 wpa_supplicant[1260]: Associated with a0:f3:c1:c1:18:ea
May 10 13:52:08 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: associating -> associated
May 10 13:52:09 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: associated -> 4-way handshake
May 10 13:52:09 ssg1 wpa_supplicant[1260]: WPA: Key negotiation completed with a0:f3:c1:c1:18:ea [PTK=CCMP GTK=CCMP]
May 10 13:52:09 ssg1 wpa_supplicant[1260]: CTRL-EVENT-CONNECTED - Connection to a0:f3:c1:c1:18:ea completed (reauth) [id=0 id_str=]
May 10 13:52:09 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: 4-way handshake -> completed
May 10 13:55:01 ssg1 CRON[21977]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
May 10 13:56:04 ssg1 wpa_supplicant[1260]: CTRL-EVENT-DISCONNECTED bssid=a0:f3:c1:c1:18:ea reason=4
May 10 13:56:04 ssg1 kernel: [57784.044222] cfg80211: All devices are disconnected, going to restore regulatory settings
May 10 13:56:04 ssg1 kernel: [57784.044232] cfg80211: Restoring regulatory settings
May 10 13:56:04 ssg1 kernel: [57784.044239] cfg80211: Calling CRDA to update world regulatory domain
May 10 13:56:04 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: completed -> disconnected
May 10 13:56:04 ssg1 kernel: [57784.049755] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
May 10 13:56:04 ssg1 kernel: [57784.049760] cfg80211: World regulatory domain updated:
May 10 13:56:04 ssg1 kernel: [57784.049763] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May 10 13:56:04 ssg1 kernel: [57784.049766] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 13:56:04 ssg1 kernel: [57784.049770] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 10 13:56:04 ssg1 kernel: [57784.049773] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 10 13:56:04 ssg1 kernel: [57784.049776] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 13:56:04 ssg1 kernel: [57784.049779] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 13:56:04 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: disconnected -> scanning
May 10 13:56:07 ssg1 wpa_supplicant[1260]: Trying to authenticate with a0:f3:c1:c1:18:ea (SSID='carbon' freq=2412 MHz)
May 10 13:56:07 ssg1 kernel: [57787.268595] wlan1: authenticate with a0:f3:c1:c1:18:ea (try 1)
May 10 13:56:07 ssg1 kernel: [57787.270837] wlan1: authenticated
May 10 13:56:07 ssg1 wpa_supplicant[1260]: Trying to associate with a0:f3:c1:c1:18:ea (SSID='carbon' freq=2412 MHz)
May 10 13:56:07 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: scanning -> authenticating
May 10 13:56:08 ssg1 kernel: [57787.273145] wlan1: associate with a0:f3:c1:c1:18:ea (try 1)
May 10 13:56:08 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: authenticating -> associating
May 10 13:56:08 ssg1 kernel: [57787.277230] wlan1: RX ReassocResp from a0:f3:c1:c1:18:ea (capab=0x431 status=0 aid=1)
May 10 13:56:08 ssg1 kernel: [57787.277234] wlan1: associated
May 10 13:56:08 ssg1 kernel: [57787.277238] wlan1: No basic rates in AssocResp. Using min supported rate instead.
May 10 13:56:08 ssg1 wpa_supplicant[1260]: Associated with a0:f3:c1:c1:18:ea
May 10 13:56:08 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: associating -> associated
May 10 13:56:09 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: associated -> 4-way handshake
May 10 13:56:09 ssg1 wpa_supplicant[1260]: WPA: Key negotiation completed with a0:f3:c1:c1:18:ea [PTK=CCMP GTK=CCMP]
May 10 13:56:09 ssg1 wpa_supplicant[1260]: CTRL-EVENT-CONNECTED - Connection to a0:f3:c1:c1:18:ea completed (reauth) [id=0 id_str=]
May 10 13:56:09 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: 4-way handshake -> completed
May 10 13:58:10 ssg1 wpa_supplicant[1260]: WPA: Group rekeying completed with a0:f3:c1:c1:18:ea [GTK=CCMP]
May 10 13:58:44  wpa_supplicant[1260]: last message repeated 3 times
May 10 13:58:44 ssg1 kernel: [57944.033873] wlan1: deauthenticated from a0:f3:c1:c1:18:ea (Reason: 6)
May 10 13:58:44 ssg1 wpa_supplicant[1260]: CTRL-EVENT-DISCONNECTED bssid=a0:f3:c1:c1:18:ea reason=6
May 10 13:58:44 ssg1 kernel: [57944.070970] cfg80211: All devices are disconnected, going to restore regulatory settings
May 10 13:58:44 ssg1 kernel: [57944.070985] cfg80211: Restoring regulatory settings
May 10 13:58:44 ssg1 kernel: [57944.071025] cfg80211: Calling CRDA to update world regulatory domain
May 10 13:58:44 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: completed -> disconnected
May 10 13:58:44 ssg1 kernel: [57944.076230] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
May 10 13:58:44 ssg1 kernel: [57944.076234] cfg80211: World regulatory domain updated:
May 10 13:58:44 ssg1 kernel: [57944.076236] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May 10 13:58:44 ssg1 kernel: [57944.076240] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 13:58:44 ssg1 kernel: [57944.076243] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 10 13:58:44 ssg1 kernel: [57944.076246] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 10 13:58:44 ssg1 kernel: [57944.076249] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 13:58:44 ssg1 kernel: [57944.076252] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 13:58:44 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: disconnected -> scanning
May 10 13:58:48 ssg1 wpa_supplicant[1260]: Trying to authenticate with a0:f3:c1:c1:18:ea (SSID='carbon' freq=2412 MHz)
May 10 13:58:48 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: scanning -> authenticating
May 10 13:58:48 ssg1 wpa_supplicant[1260]: Trying to associate with a0:f3:c1:c1:18:ea (SSID='carbon' freq=2412 MHz)
May 10 13:58:48 ssg1 kernel: [57947.321075] wlan1: authenticate with a0:f3:c1:c1:18:ea (try 1)
May 10 13:58:48 ssg1 kernel: [57947.323263] wlan1: authenticated
May 10 13:58:48 ssg1 kernel: [57947.323651] wlan1: associate with a0:f3:c1:c1:18:ea (try 1)
May 10 13:58:48 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: authenticating -> associating
May 10 13:58:48 ssg1 kernel: [57947.328830] wlan1: RX ReassocResp from a0:f3:c1:c1:18:ea (capab=0x431 status=0 aid=1)
May 10 13:58:48 ssg1 kernel: [57947.328836] wlan1: associated
May 10 13:58:48 ssg1 kernel: [57947.328841] wlan1: No basic rates in AssocResp. Using min supported rate instead.
May 10 13:58:48 ssg1 wpa_supplicant[1260]: Associated with a0:f3:c1:c1:18:ea
May 10 13:58:48 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: associating -> associated
May 10 13:58:49 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: associated -> 4-way handshake
May 10 13:58:49 ssg1 wpa_supplicant[1260]: WPA: Key negotiation completed with a0:f3:c1:c1:18:ea [PTK=CCMP GTK=CCMP]
May 10 13:58:49 ssg1 wpa_supplicant[1260]: CTRL-EVENT-CONNECTED - Connection to a0:f3:c1:c1:18:ea completed (reauth) [id=0 id_str=]
May 10 13:58:49 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: 4-way handshake -> completed
May 10 14:00:04 ssg1 wpa_supplicant[1260]: CTRL-EVENT-DISCONNECTED bssid=a0:f3:c1:c1:18:ea reason=4
May 10 14:00:04 ssg1 kernel: [58024.036215] cfg80211: All devices are disconnected, going to restore regulatory settings
May 10 14:00:04 ssg1 kernel: [58024.036225] cfg80211: Restoring regulatory settings
May 10 14:00:04 ssg1 kernel: [58024.036232] cfg80211: Calling CRDA to update world regulatory domain
May 10 14:00:04 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: completed -> disconnected
May 10 14:00:04 ssg1 kernel: [58024.041439] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
May 10 14:00:04 ssg1 kernel: [58024.041444] cfg80211: World regulatory domain updated:
May 10 14:00:04 ssg1 kernel: [58024.041446] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May 10 14:00:04 ssg1 kernel: [58024.041450] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 14:00:04 ssg1 kernel: [58024.041453] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 10 14:00:04 ssg1 kernel: [58024.041456] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 10 14:00:04 ssg1 kernel: [58024.041459] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 14:00:04 ssg1 kernel: [58024.041462] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 14:00:04 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: disconnected -> scanning
May 10 14:00:08 ssg1 wpa_supplicant[1260]: Trying to authenticate with a0:f3:c1:c1:18:ea (SSID='carbon' freq=2412 MHz)
May 10 14:00:08 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: scanning -> authenticating
May 10 14:00:08 ssg1 kernel: [58027.398045] wlan1: authenticate with a0:f3:c1:c1:18:ea (try 1)
May 10 14:00:08 ssg1 wpa_supplicant[1260]: Trying to associate with a0:f3:c1:c1:18:ea (SSID='carbon' freq=2412 MHz)
May 10 14:00:08 ssg1 kernel: [58027.400350] wlan1: authenticated
May 10 14:00:08 ssg1 kernel: [58027.400897] wlan1: associate with a0:f3:c1:c1:18:ea (try 1)
May 10 14:00:08 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: authenticating -> associating
May 10 14:00:08 ssg1 kernel: [58027.405049] wlan1: RX ReassocResp from a0:f3:c1:c1:18:ea (capab=0x431 status=0 aid=1)
May 10 14:00:08 ssg1 kernel: [58027.405057] wlan1: associated
May 10 14:00:08 ssg1 kernel: [58027.405063] wlan1: No basic rates in AssocResp. Using min supported rate instead.
May 10 14:00:08 ssg1 wpa_supplicant[1260]: Associated with a0:f3:c1:c1:18:ea
May 10 14:00:08 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: associating -> associated
May 10 14:00:09 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: associated -> 4-way handshake
May 10 14:00:09 ssg1 wpa_supplicant[1260]: WPA: Key negotiation completed with a0:f3:c1:c1:18:ea [PTK=CCMP GTK=CCMP]
May 10 14:00:09 ssg1 wpa_supplicant[1260]: CTRL-EVENT-CONNECTED - Connection to a0:f3:c1:c1:18:ea completed (reauth) [id=0 id_str=]
May 10 14:00:09 ssg1 NetworkManager[1056]: <info> (wlan1): supplicant interface state: 4-way handshake -> completed

```

The log from the router is brief but shows some info as well: 

```
May 10 13:48:19 [SYSTEM]: DHCP Server, Sending ACK of 192.168.2.8
May 10 13:42:21 [SYSTEM]: DHCP Server, Sending ACK of 192.168.2.105
May 10 13:41:18 [SYSTEM]: DHCP Server, Sending ACK of 192.168.2.7
May 10 13:39:02 [SYSTEM]: DHCP Server, Sending ACK of 192.168.2.8
May 10 13:30:11 [SYSTEM]: SCHEDULE, Wireless Radio On
May 10 13:30:11 [SYSTEM]: SCHEDULE, stop Power Save
May 10 13:30:11 [SYSTEM]: SCHEDULE, Schedule Stopping
May 10 13:30:11 [SYSTEM]: WLAN[2.4G],AutoChannel change to 4
May 10 13:30:08 [SYSTEM]: WLAN[2.4G],Available Channel: [CH.1 ~ CH.11]
May 10 13:26:46 [SYSTEM]: DHCP Server, Sending ACK of 192.168.2.8
May 10 13:25:39 [SYSTEM]: DHCP Server, Sending ACK of 192.168.2.8
May 10 13:25:39 [SYSTEM]: DHCP Server, Sending OFFER of 192.168.2.8
May 10 13:25:06 [SYSTEM]: DHCP Server, Sending ACK of 192.168.2.8
May 10 13:25:06 [SYSTEM]: DHCP Server, Sending OFFER of 192.168.2.8
May 10 13:24:29 [SYSTEM]: DHCP Server, Sending ACK of 192.168.2.8
```

I left it alone for a while and after I returned a few hours later, the internet and network connections were working fine again. Are there any clues in the logs as to the cause of the issue?

---

### Post by varunendra on 2013-05-11
This part of syslog looks interesting to me -
> **fizikz said:**
> ```
May 10 13:27:16 ssg1 NetworkManager[1056]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
May 10 13:35:01 ssg1 CRON[21563]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
[B]May 10 13:38:50 ssg1 NetworkManager[1056]: <info> disable requested (sleeping: no  enabled: yes)
May 10 13:38:50 ssg1 NetworkManager[1056]: <info> sleeping or disabling...
May 10 13:38:50 ssg1 NetworkManager[1056]: <info> (eth0): now unmanaged
May 10 13:38:50 ssg1 NetworkManager[1056]: <info> (eth0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
May 10 13:38:50 ssg1 NetworkManager[1056]: <info> (eth0): cleaning up...
May 10 13:38:50 ssg1 NetworkManager[1056]: <info> (eth0): taking down device.
May 10 13:38:50 ssg1 NetworkManager[1056]: <info> (wlan1): now unmanaged
May 10 13:38:50 ssg1 NetworkManager[1056]: <info> (wlan1): device state change: activated -> unmanaged (reason 'sleeping') [100 10 37]
May 10 13:38:50 ssg1 NetworkManager[1056]: <info> (wlan1): deactivating device (reason 'sleeping') [37]
May 10 13:38:50 ssg1 NetworkManager[1056]: <info> (wlan1): canceled DHCP transaction, DHCP client pid 21226[/B]
May 10 13:38:50 ssg1 kernel: [56750.006655] wlan1: deauthenticating from a0:f3:c1:c1:18:ea by local choice (reason=3)
May 10 13:38:50 ssg1 kernel: [56750.056706] cfg80211: All devices are disconnected, going to restore regulatory settings
```
....followed by some further occurences of "sleeping or disabling".

Please post outputs of :
```
ifconfig
iwconfig
grep -iR [0-9a-z] /sys/module/iwlwifi/parameters
```

---

### Post by fizikz on 2013-05-11
> **varunendra said:**
> This part of syslog looks interesting to me -

....followed by some further occurences of "sleeping or disabling".

Please post outputs of :
```
ifconfig
iwconfig
grep -iR [0-9a-z] /sys/module/iwlwifi/parameters
```

I should have mentioned that after the initial internet drop, I stopped/started networking via the network manager, so that could be the lines related to "sleeping or disabling."

```
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:f3:f3:89:a1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:355 errors:0 dropped:0 overruns:0 frame:0
          TX packets:355 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:56287 (56.2 KB)  TX bytes:56287 (56.2 KB)

wlan1     Link encap:Ethernet  HWaddr 00:23:14:dd:2c:5c  
          inet addr:192.168.2.8  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::223:14ff:fedd:2c5c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9619 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11356524 (11.3 MB)  TX bytes:1231124 (1.2 MB)
```

```
~$ iwconfig
lo        no wireless extensions.

wlan1     IEEE 802.11abgn  ESSID:"carbon"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: A0:F3:C1:C1:18:EA   
          Bit Rate=144.4 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3334  Invalid misc:197   Missed beacon:0

eth0      no wireless extensions.
```

```
~$ grep -iR [0-9a-z] /sys/module/iwlwifi/parameters
/sys/module/iwlwifi/parameters/no_sleep_autoadjust:Y
/sys/module/iwlwifi/parameters/auto_agg:Y
/sys/module/iwlwifi/parameters/power_level:0
/sys/module/iwlwifi/parameters/power_save:N
/sys/module/iwlwifi/parameters/led_mode:0
/sys/module/iwlwifi/parameters/bt_coex_active:Y
/sys/module/iwlwifi/parameters/wd_disable:0
/sys/module/iwlwifi/parameters/ack_check:N
/sys/module/iwlwifi/parameters/plcp_check:Y
/sys/module/iwlwifi/parameters/bt_ch_inhibition:Y
/sys/module/iwlwifi/parameters/antenna_coupling:0
/sys/module/iwlwifi/parameters/ucode_alternative:1
/sys/module/iwlwifi/parameters/fw_restart:1
/sys/module/iwlwifi/parameters/amsdu_size_8K:1
/sys/module/iwlwifi/parameters/11n_disable:0
/sys/module/iwlwifi/parameters/queues_num:0
/sys/module/iwlwifi/parameters/swcrypto:0

```

---

### Post by fizikz on 2013-05-12
I switched back to my old and stable Intel 3945ABG network adapter, but the drop happened again. I've copied some of the new log contents at the time of the drop.

syslog:
```
May 12 19:05:01 ssg1 CRON[7889]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
May 12 19:06:46 ssg1 kernel: [70598.500076] ieee80211 phy0: wlan2: No probe response from AP a0:f3:c1:c1:18:ea after 500ms, disconnecting.
May 12 19:06:46 ssg1 wpa_supplicant[1149]: CTRL-EVENT-DISCONNECTED bssid=a0:f3:c1:c1:18:ea reason=4
May 12 19:06:46 ssg1 kernel: [70598.536287] cfg80211: All devices are disconnected, going to restore regulatory settings
May 12 19:06:46 ssg1 kernel: [70598.536294] cfg80211: Restoring regulatory settings
May 12 19:06:46 ssg1 kernel: [70598.536299] cfg80211: Calling CRDA to update world regulatory domain
May 12 19:06:46 ssg1 NetworkManager[1017]: <info> (wlan2): supplicant interface state: completed -> disconnected
May 12 19:06:46 ssg1 NetworkManager[1017]: <info> (wlan2): supplicant interface state: disconnected -> scanning
May 12 19:06:46 ssg1 kernel: [70599.123108] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
May 12 19:06:46 ssg1 kernel: [70599.123113] cfg80211: World regulatory domain updated:
May 12 19:06:46 ssg1 kernel: [70599.123116] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May 12 19:06:46 ssg1 kernel: [70599.123120] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 12 19:06:46 ssg1 kernel: [70599.123123] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 12 19:06:46 ssg1 kernel: [70599.123126] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 12 19:06:46 ssg1 kernel: [70599.123129] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 12 19:06:46 ssg1 kernel: [70599.123132] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 12 19:06:48 ssg1 wpa_supplicant[1149]: Trying to authenticate with a0:f3:c1:c1:18:ea (SSID='carbon' freq=2437 MHz)
May 12 19:06:48 ssg1 kernel: [70600.983019] wlan2: authenticate with a0:f3:c1:c1:18:ea (try 1)
May 12 19:06:48 ssg1 wpa_supplicant[1149]: Trying to associate with a0:f3:c1:c1:18:ea (SSID='carbon' freq=2437 MHz)
May 12 19:06:48 ssg1 NetworkManager[1017]: <info> (wlan2): supplicant interface state: scanning -> authenticating
May 12 19:06:48 ssg1 kernel: [70600.985199] wlan2: authenticated
May 12 19:06:48 ssg1 kernel: [70600.985787] wlan2: associate with a0:f3:c1:c1:18:ea (try 1)
May 12 19:06:48 ssg1 NetworkManager[1017]: <info> (wlan2): supplicant interface state: authenticating -> associating
May 12 19:06:48 ssg1 kernel: [70600.988647] wlan2: RX ReassocResp from a0:f3:c1:c1:18:ea (capab=0x431 status=0 aid=1)
May 12 19:06:48 ssg1 kernel: [70600.988655] wlan2: associated
May 12 19:06:48 ssg1 kernel: [70600.988661] wlan2: No basic rates in AssocResp. Using min supported rate instead.
May 12 19:06:48 ssg1 wpa_supplicant[1149]: Associated with a0:f3:c1:c1:18:ea
May 12 19:06:48 ssg1 NetworkManager[1017]: <info> (wlan2): supplicant interface state: associating -> associated
May 12 19:06:49 ssg1 wpa_supplicant[1149]: WPA: Key negotiation completed with a0:f3:c1:c1:18:ea [PTK=CCMP GTK=CCMP]
May 12 19:06:49 ssg1 wpa_supplicant[1149]: CTRL-EVENT-CONNECTED - Connection to a0:f3:c1:c1:18:ea completed (reauth) [id=0 id_str=]
May 12 19:06:49 ssg1 NetworkManager[1017]: <info> (wlan2): supplicant interface state: associated -> completed
May 12 19:11:39 ssg1 wpa_supplicant[1149]: WPA: Group rekeying completed with a0:f3:c1:c1:18:ea [GTK=CCMP]
```

dmesg:
```
[   29.841575] r8169 0000:02:00.0: eth0: link down
[   29.841760] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.842088] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.064114] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   30.153320] ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   30.153627] ADDRCONF(NETDEV_UP): wlan2: link is not ready
```

---

### Post by varunendra on 2013-05-13
> **fizikz said:**
> 
```
May 12 19:05:01 ssg1 CRON[7889]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
May 12 19:06:46 ssg1 kernel: [70598.500076] ieee80211 phy0: wlan2: **No probe response from AP a0:f3:c1:c1:18:ea [COLOR="#FF0000"]after 500ms[/COLOR], disconnecting**.
May 12 19:06:46 ssg1 wpa_supplicant[1149]: CTRL-EVENT-DISCONNECTED bssid=a0:f3:c1:c1:18:ea reason=4
```
I was recently suggested to take notice of this kind of messages. (in this post : [http://ubuntuforums.org/showthread.php?t=2141623&p=12639394#post12639394](http://ubuntuforums.org/showthread.php?t=2141623&p=12639394#post12639394))
So now I feel uncomfortable by its presence too.

> I switched back to my old and stable Intel 3945ABG network adapter, but the drop happened again...
Assuming you are on the same 3945 adapter now, please try -
```
echo "options mac80211 probe_wait_ms=1000" | sudo tee /etc/modprobe.d/mac80211.conf
```
....then do -
```
sudo modprobe -rfv iwl3945
sudo modprobe -v iwl3945
```
.. or a restart. And see if the "....No probe response from AP a0:f3:c1:c1:18:ea after 1000ms, disconnecting" message appears anymore. If it does, you may try changing the value from 1000 to 2000 in etc/modprobe.d/mac80211.conf file that we created above.

Additionally, disable IPv6 permanently on your interfaces as suggested here : [http://ubuntuforums.org/showthread.php?t=2143561&p=12640479#post12640479](http://ubuntuforums.org/showthread.php?t=2143561&p=12640479#post12640479)

---

### Post by fizikz on 2013-05-13
Thanks. I made the changes you suggested, with the mac80211.conf and IPv6 disabling. I don't think I'm using IPv6 yet, but why does it need to be disabled? Won't it increasingly be used?

Yes, I am still using the Intel 3945 adapter at the moment, although the intention is to upgrade it to an Intel 5100 with wireless N. Recently I upgraded to a 5100 and I was having freezes with the it, so in trying to isolate a cause, I swapped it with another 5100, and also tried a 6200. I still got freezes with all of those, meaning that it's unlikely to be an issue with a faulty card, so I switched back to the 3945 to make sure that my system is in fact stable. These drops are something new which I did not experience with any card before. I hope these changes solve the drops, otherwise I may have to resort to doing a clean install of 12.04.

---

### Post by varunendra on 2013-05-14
> **fizikz said:**
> Thanks. I made the changes you suggested, with the mac80211.conf and IPv6 disabling. I don't think I'm using IPv6 yet, but why does it need to be disabled? Won't it increasingly be used?
Yes it will be. But as long as it is not used all the way from your PC to your router to your ISP, and probably to all those sites that you might be visiting, it is but an unnecessary extra path which can sometimes indulge and delay dns request so long that a connection may timeout. So, if you and your ISP both are not using it, it is a good idea to disable it, especially when there are doubts on it.

That does not make IPv6 a bad thing, it is just the lack of its widespread support yet that sometimes makes it an obstacle. Although I must admit that I haven't read up on its progress for about a year, so my information may be outdated.

Anyway did you check the dmesg to see if there are still any "No probe response from AP...." messages? Did it make any noticeable improvement?

> I hope these changes solve the drops, otherwise I may have to resort to doing a clean install of 12.04.
I consider that a good idea. But for any version, test it via live cd/usb before installing. Only install if it seems to work better.

---

### Post by fizikz on 2013-05-14
Since the problem was intermittent, I'd need several days to be confident of any conclusion, but so far I have neither seen that message in the logs, nor have I noticed any drops. So far, so good!

> But for any version, test it via live cd/usb before installing. Only install if it seems to work better. 

Thanks! I should have thought of that! When I get a chance, I'll install the Intel 5100 again and use a live usb for a while to see how it does.

---

### Post by varunendra on 2013-05-14
Good Luck! :)

---

### Post by fizikz on 2013-05-14
I spoke too soon. I got a "No probe response from AP after 1000ms" message. I'll change it to 2000ms in the config file created earlier. However, I do wonder about it. 1000ms or 2000ms is a very long time for computers. Is this really the best solution?

```
May 14 19:20:41 ssg1 kernel: [159029.805068] ieee80211 phy0: wlan2: No probe response from AP a0:f3:c1:c1:18:ea after 1000ms, disconnecting.
May 14 19:20:41 ssg1 wpa_supplicant[1156]: CTRL-EVENT-DISCONNECTED bssid=a0:f3:c1:c1:18:ea reason=4
May 14 19:20:41 ssg1 kernel: [159029.844376] cfg80211: All devices are disconnected, going to restore regulatory settings
May 14 19:20:41 ssg1 kernel: [159029.844396] cfg80211: Restoring regulatory settings
May 14 19:20:41 ssg1 kernel: [159029.844400] cfg80211: Calling CRDA to update world regulatory domain
May 14 19:20:41 ssg1 NetworkManager[1034]: <info> (wlan2): supplicant interface state: completed -> disconnected
May 14 19:20:41 ssg1 NetworkManager[1034]: <info> (wlan2): supplicant interface state: disconnected -> scanning
May 14 19:20:43 ssg1 kernel: [159031.458887] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
May 14 19:20:43 ssg1 kernel: [159031.458891] cfg80211: World regulatory domain updated:
May 14 19:20:43 ssg1 kernel: [159031.458894] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May 14 19:20:43 ssg1 kernel: [159031.458897] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 14 19:20:43 ssg1 kernel: [159031.458901] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 14 19:20:43 ssg1 kernel: [159031.458904] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 14 19:20:43 ssg1 kernel: [159031.458907] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 14 19:20:43 ssg1 kernel: [159031.458910] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 14 19:20:44 ssg1 wpa_supplicant[1156]: Trying to authenticate with 00:02:6f:92:17:68 (SSID='carbon' freq=2462 MHz)
May 14 19:20:44 ssg1 NetworkManager[1034]: <info> (wlan2): supplicant interface state: scanning -> authenticating
May 14 19:20:44 ssg1 wpa_supplicant[1156]: Trying to associate with 00:02:6f:92:17:68 (SSID='carbon' freq=2462 MHz)
May 14 19:20:44 ssg1 kernel: [159032.500522] wlan2: authenticate with 00:02:6f:92:17:68 (try 1)
May 14 19:20:44 ssg1 kernel: [159032.501614] wlan2: authenticated
May 14 19:20:44 ssg1 NetworkManager[1034]: <info> (wlan2): supplicant interface state: authenticating -> associating
May 14 19:20:44 ssg1 kernel: [159032.505866] wlan2: associate with 00:02:6f:92:17:68 (try 1)
May 14 19:20:44 ssg1 kernel: [159032.507641] wlan2: RX ReassocResp from 00:02:6f:92:17:68 (capab=0xc31 status=0 aid=3)
May 14 19:20:44 ssg1 kernel: [159032.507648] wlan2: associated
May 14 19:20:44 ssg1 wpa_supplicant[1156]: Associated with 00:02:6f:92:17:68
May 14 19:20:44 ssg1 NetworkManager[1034]: <info> (wlan2): supplicant interface state: associating -> associated
May 14 19:20:44 ssg1 NetworkManager[1034]: <info> (wlan2): supplicant interface state: associated -> 4-way handshake
May 14 19:20:44 ssg1 wpa_supplicant[1156]: WPA: Key negotiation completed with 00:02:6f:92:17:68 [PTK=CCMP GTK=CCMP]
May 14 19:20:44 ssg1 wpa_supplicant[1156]: CTRL-EVENT-CONNECTED - Connection to 00:02:6f:92:17:68 completed (reauth) [id=0 id_str=]
May 14 19:20:44 ssg1 NetworkManager[1034]: <info> (wlan2): supplicant interface state: 4-way handshake -> completed
May 14 19:20:47 ssg1 NetworkManager[1034]: <info> (wlan2): roamed from BSSID A0:F3:C1:C1:18:EA (carbon) to 00:02:6F:92:17:68 (carbon)
```

---

### Post by varunendra on 2013-05-14
> **fizikz said:**
> I spoke too soon. I got a "No probe response from AP after 1000ms" message. I'll change it to 2000ms in the config file created earlier. However, I do wonder about it. 1000ms or 2000ms is a very long time for computers. Is this really the best solution?
Yes, a long time for a computer, even an ancient one. But for negotiation-authentication between two wireless devices, not too long. Although 2000 is a bit on the higher side, 500ms is too short for that. Just compare with the usual time when a connection attempt starts through the time when you get a "Connection established" status, it will seem normal.

Please also check -
cat /sys/module/iwl3945/parameters/swcrypto
if it returns "0" then try -
```
sudo modprobe -rfv iwl3945
sudo modprobe -v iwl3945 swcrypto=1
```
..and make sure the encryption type in the router/access-point is set to WPA2-PSK only (not always necessary, but recommended; whereas WPA/WPA2 mixed mode is almost always problematic).

However, this also seems worth noticing -
> **fizikz said:**
> ```

**May 14 19:20:47 ssg1 NetworkManager[1034]: <info> (wlan2): [B]roamed from BSSID A0:F3:C1:C1:18:EA (carbon) to 00:02:6F:92:17:68 (carbon)**[/B]
```
If the above changes seem ineffective and this kind of messages keep re-appearing, you may try binding the SSID "carbon" with any 'one' access point of your choice by saving its mac address in BSSID field of the Network Manager setting for the connection, so that it doesn't automatically roam from one ap to another. If you need to connect to more than one (of the same SSID), you may try creating multiple such profiles with different names (although I don't know if it's effective or not, just assuming). You *should be able to* then use these profiles to switch to the ap of choice manually.

Alternatively, you may try using 'wicd' instead of Network Manager. It often works better in these circumstances.

To get and share a detailed diagnostic report, you may use the "Wireless Script" link in my signature. It should be able to provide some more insight into the overall settings.

---

### Post by fizikz on 2013-05-15
swcrypto=1 is confirmed.

The router and access point are set to WPA2-PSK and not mixed mode.

In this particular case the roaming was because I had momentarily disconnected the AP, so there was no real problem. However, it does happen that sometimes it can automatically connect to the AP which is farther away. I would like to be able to choose the AP I connect to and I have made two Network Connections with different names in Network Manager, both with the same SSID, but with the different BSSIDs (MAC) of the different APs. However, I see no way of specifying which connection to use. In Network Manager, I see the list of SSIDs but not the Network Connections I made.

As for wicd, I believe I had tried installing it a while back and hadn't managed to get it to work. Also, I prefer to keep most core aspects of the install close to the Ubuntu defaults for simplicity and standardization. 

Your script is pretty neat. I had tried several of those commands myself previously, but here is the output of your script with more complete information: [http://paste.ubuntu.com/5666538/]("http://paste.ubuntu.com/5666538/")

---

### Post by varunendra on 2013-05-15
> **fizikz said:**
> Your script is pretty neat.
Not my script, I just use it. It was created by people I credited in that post :)

> here is the output of your script with more complete information: [http://paste.ubuntu.com/5666538/]("http://paste.ubuntu.com/5666538/")
Nothing looks suspicious in there to my inexperienced eyes. However, there were a number of connection-disconnection cycles in a short interval as per dmesg part. Were you manually cycling it or was it happening by itself?

How's the overall connection quality after increasing the "probe_wait_ms" parameter to 2000ms ?

---

### Post by fizikz on 2013-05-16
In that instance, the disconnect errors were because the AP was being power cycled. Normally it is stable. 

After changing the "probe_wait_ms" parameter to 2000, I have not seen any drops in the last day or so. If I don't experience any more drops in the next few days, I'll consider this solved.

Thanks for all your help!

---

### Post by varunendra on 2013-05-16
> **fizikz said:**
> After changing the "probe_wait_ms" parameter to 2000, I have not seen any drops in the last day or so. If I don't experience any more drops in the next few days, I'll consider this solved.

Thanks for all your help!

You're welcome! We just try and hope.. :)

---

### Post by fizikz on 2013-05-31
My wireless remained stable with the Intel 3945ABG with this fix, so I'll consider this solved.

I have tried upgrading to wireless N once again, this time by using the Intel 4965AGN adapter, and I've run into a different sort of wireless drop issue: [http://ubuntuforums.org/showthread.php?t=2150398&p=12672425#post12672425]("http://ubuntuforums.org/showthread.php?t=2150398&p=12672425#post12672425")

However, since the drops stopped with the Intel 3945, I will mark this thread as solved.

---

### Post by varunendra on 2013-06-01
> **fizikz said:**
> My wireless remained stable with the Intel 3945ABG with this fix, so I'll consider this solved.
Great! Thanks for taking the time to get back to us for the feedback. :)

> I have tried upgrading to wireless N once again, this time by using the Intel 4965AGN adapter, and I've run into a different sort of wireless drop issue: [http://ubuntuforums.org/showthread.php?t=2150398&p=12672425#post12672425]("http://ubuntuforums.org/showthread.php?t=2150398&p=12672425#post12672425")
Looks like Hadaka has picked up your thread. He is quite resourceful and determined, and we often keep discussing issues in the background. So you can trust him for the best kind of help we both can offer.

> However, since the drops stopped with the Intel 3945, I will mark this thread as solved.
Yes, please do so. Follow the link in my signature to see how.

---

