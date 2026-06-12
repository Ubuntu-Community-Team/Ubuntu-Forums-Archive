---
title: "Unable to connect to specific sites after a while of usage via wifi"
date: 2013-04-17
forum: Networking &amp; Wireless
---

### Post by jierro on 2013-04-17
So the thing is, my wireless is working normaly, but after like 10 minutes of browsing on the internet, I'm not able to reach specific sites anymore. When I'm using launchpad.net, i get constant Timeouts and Bad requests. So when it does that, I have to switch the wifi button to off and on to work it again. It's quite annoying.

Interestingly, when I try the other laptop with linux and connect to the same wifi spot, I get the same problem. I'm running dualboot with Ubuntu 13.04 and Windows 8. It's working flawlessly on Win 8.



I attached the output file of a script, which I found on the other thread.
Any help is greatly appreciated.

---

### Post by jierro on 2013-04-24
Some additional info from syslog, when I switch wifi off/on:

```
Pavilion-dv5 wpa_supplicant[1189]: rfkill: WLAN hard blockedApr 24 15:49:26 Pavilion-dv5 kernel: [  139.471200] iwlwifi 0000:02:00.0: RF_KILL bit toggled to disable radio.
Apr 24 15:49:26 Pavilion-dv5 kernel: [  139.471324] wlan0: deauthenticating from 00:1d:1c:ff:65:9b by local choice (reason=3)
Apr 24 15:49:26 Pavilion-dv5 kernel: [  139.471654] iwlwifi 0000:02:00.0: Not sending command - RF KILL
Apr 24 15:49:26 Pavilion-dv5 kernel: [  139.471663] wlan0: failed to remove key (0, 00:1d:1c:ff:65:9b) from hardware (-5)
Apr 24 15:49:26 Pavilion-dv5 NetworkManager[1177]: <info> WiFi now disabled by radio killswitch
Apr 24 15:49:26 Pavilion-dv5 NetworkManager[1177]: <info> (wlan0): device state change: activated -> unavailable (reason 'none') [100 20 0]
Apr 24 15:49:26 Pavilion-dv5 NetworkManager[1177]: <info> (wlan0): deactivating device (reason 'none') [0]
Apr 24 15:49:26 Pavilion-dv5 NetworkManager[1177]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1421
Apr 24 15:49:26 Pavilion-dv5 wpa_supplicant[1189]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:1d:1c:ff:65:9b reason=3
Apr 24 15:49:26 Pavilion-dv5 kernel: [  139.488497] iwlwifi 0000:02:00.0: Not sending command - RF KILL
Apr 24 15:49:26 Pavilion-dv5 kernel: [  139.488513] iwlwifi 0000:02:00.0: Not sending command - RF KILL
Apr 24 15:49:26 Pavilion-dv5 kernel: [  139.488530] iwlwifi 0000:02:00.0: Not sending command - RF KILL
Apr 24 15:49:26 Pavilion-dv5 kernel: [  139.488542] iwlwifi 0000:02:00.0: Not sending command - RF KILL
Apr 24 15:49:26 Pavilion-dv5 kernel: [  139.488552] iwlwifi 0000:02:00.0: Not sending command - RF KILL
Apr 24 15:49:26 Pavilion-dv5 kernel: [  139.488779] iwlwifi 0000:02:00.0: Not sending command - RF KILL
Apr 24 15:49:26 Pavilion-dv5 kernel: [  139.488788] wlan0: failed to remove key (2, ff:ff:ff:ff:ff:ff) from hardware (-5)
Apr 24 15:49:26 Pavilion-dv5 kernel: [  139.498674] cfg80211: Calling CRDA to update world regulatory domain
Apr 24 15:49:26 Pavilion-dv5 avahi-daemon[1139]: Interface wlan0.IPv6 no longer relevant for mDNS.
Apr 24 15:49:26 Pavilion-dv5 avahi-daemon[1139]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::216:eaff:fe9d:64fe.
Apr 24 15:49:26 Pavilion-dv5 avahi-daemon[1139]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr 24 15:49:26 Pavilion-dv5 avahi-daemon[1139]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.82.
Apr 24 15:49:26 Pavilion-dv5 avahi-daemon[1139]: Withdrawing address record for fe80::216:eaff:fe9d:64fe on wlan0.
Apr 24 15:49:26 Pavilion-dv5 avahi-daemon[1139]: Withdrawing address record for 192.168.1.82 on wlan0.
Apr 24 15:49:26 Pavilion-dv5 wpa_supplicant[1189]: rfkill: WLAN hard blocked
Apr 24 15:49:26 Pavilion-dv5 NetworkManager[1177]: <warn> DNS: plugin dnsmasq update failed
Apr 24 15:49:26 Pavilion-dv5 NetworkManager[1177]: <info> Removing DNS information from /sbin/resolvconf
Apr 24 15:49:26 Pavilion-dv5 dnsmasq[1527]: setting upstream servers from DBus
Apr 24 15:49:26 Pavilion-dv5 kernel: [  139.528043] iwlwifi 0000:02:00.0: Not sending command - RF KILL
Apr 24 15:49:26 Pavilion-dv5 kernel: [  139.529139] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 24 15:49:26 Pavilion-dv5 kernel: [  139.529793] cfg80211: World regulatory domain updated:
Apr 24 15:49:26 Pavilion-dv5 kernel: [  139.529796] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr 24 15:49:26 Pavilion-dv5 kernel: [  139.529799] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 24 15:49:26 Pavilion-dv5 kernel: [  139.529801] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr 24 15:49:26 Pavilion-dv5 kernel: [  139.529803] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr 24 15:49:26 Pavilion-dv5 kernel: [  139.529805] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 24 15:49:26 Pavilion-dv5 kernel: [  139.529807] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 24 15:49:26 Pavilion-dv5 dbus[940]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Apr 24 15:49:26 Pavilion-dv5 dbus[940]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'

```

and

```

Pavilion-dv5 kernel: [  194.338934] iwlwifi 0000:02:00.0: RF_KILL bit toggled to enable radio.
Apr 24 15:50:21 Pavilion-dv5 NetworkManager[1177]: <info> WiFi now enabled by radio killswitch
Apr 24 15:50:21 Pavilion-dv5 NetworkManager[1177]: <info> (wlan0): bringing up device.
Apr 24 15:50:21 Pavilion-dv5 kernel: [  194.367088] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
Apr 24 15:50:21 Pavilion-dv5 kernel: [  194.370075] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
Apr 24 15:50:21 Pavilion-dv5 kernel: [  194.502484] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 24 15:50:21 Pavilion-dv5 NetworkManager[1177]: <info> (wlan0) supports 5 scan SSIDs
Apr 24 15:50:21 Pavilion-dv5 NetworkManager[1177]: <warn> Trying to remove a non-existant call id.
Apr 24 15:50:21 Pavilion-dv5 NetworkManager[1177]: <info> (wlan0): supplicant interface state: starting -> ready
Apr 24 15:50:21 Pavilion-dv5 NetworkManager[1177]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Apr 24 15:50:21 Pavilion-dv5 NetworkManager[1177]: <info> (wlan0): supplicant interface state: ready -> inactive
Apr 24 15:50:21 Pavilion-dv5 NetworkManager[1177]: <info> (wlan0) supports 5 scan SSIDs
Apr 24 15:50:24 Pavilion-dv5 NetworkManager[1177]: <info> Auto-activating connection 'Wi-Fi'.
Apr 24 15:50:24 Pavilion-dv5 NetworkManager[1177]: <info> Activation (wlan0) starting connection 'Wi-Fi'
Apr 24 15:50:24 Pavilion-dv5 NetworkManager[1177]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 24 15:50:24 Pavilion-dv5 NetworkManager[1177]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 24 15:50:24 Pavilion-dv5 NetworkManager[1177]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 24 15:50:24 Pavilion-dv5 NetworkManager[1177]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 24 15:50:24 Pavilion-dv5 NetworkManager[1177]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 24 15:50:24 Pavilion-dv5 NetworkManager[1177]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 24 15:50:24 Pavilion-dv5 NetworkManager[1177]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 24 15:50:24 Pavilion-dv5 NetworkManager[1177]: <info> Activation (wlan0/wireless): access point 'Wi-Fi' has security, but secrets are required.
Apr 24 15:50:24 Pavilion-dv5 NetworkManager[1177]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Apr 24 15:50:24 Pavilion-dv5 NetworkManager[1177]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 24 15:50:24 Pavilion-dv5 NetworkManager[1177]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 24 15:50:24 Pavilion-dv5 NetworkManager[1177]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 24 15:50:24 Pavilion-dv5 NetworkManager[1177]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Apr 24 15:50:24 Pavilion-dv5 NetworkManager[1177]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 24 15:50:24 Pavilion-dv5 NetworkManager[1177]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 24 15:50:24 Pavilion-dv5 NetworkManager[1177]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 24 15:50:24 Pavilion-dv5 NetworkManager[1177]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 24 15:50:24 Pavilion-dv5 NetworkManager[1177]: <info> Activation (wlan0/wireless): connection 'Wi-Fi' has security, and secrets exist.  No new secrets needed.
Apr 24 15:50:24 Pavilion-dv5 NetworkManager[1177]: <info> Config: added 'ssid' value 'Wi-Fi'
Apr 24 15:50:24 Pavilion-dv5 NetworkManager[1177]: <info> Config: added 'scan_ssid' value '1'
Apr 24 15:50:24 Pavilion-dv5 NetworkManager[1177]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 24 15:50:24 Pavilion-dv5 NetworkManager[1177]: <info> Config: added 'psk' value '<omitted>'
Apr 24 15:50:24 Pavilion-dv5 NetworkManager[1177]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 24 15:50:24 Pavilion-dv5 NetworkManager[1177]: <info> Config: set interface ap_scan to 1
Apr 24 15:50:24 Pavilion-dv5 NetworkManager[1177]: <info> (wlan0): supplicant interface state: inactive -> scanning
Apr 24 15:50:27 Pavilion-dv5 wpa_supplicant[1189]: wlan0: SME: Trying to authenticate with 00:1d:1c:ff:65:9b (SSID='Wi-Fi' freq=2412 MHz)
Apr 24 15:50:27 Pavilion-dv5 kernel: [  200.970176] wlan0: authenticate with 00:1d:1c:ff:65:9b
Apr 24 15:50:27 Pavilion-dv5 kernel: [  200.971131] wlan0: send auth to 00:1d:1c:ff:65:9b (try 1/3)
Apr 24 15:50:27 Pavilion-dv5 wpa_supplicant[1189]: wlan0: Trying to associate with 00:1d:1c:ff:65:9b (SSID='Wi-Fi' freq=2412 MHz)
Apr 24 15:50:27 Pavilion-dv5 NetworkManager[1177]: <info> (wlan0): supplicant interface state: scanning -> associating
Apr 24 15:50:27 Pavilion-dv5 kernel: [  200.973354] wlan0: authenticated
Apr 24 15:50:27 Pavilion-dv5 kernel: [  200.973589] iwlwifi 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
Apr 24 15:50:27 Pavilion-dv5 kernel: [  200.976051] wlan0: associate with 00:1d:1c:ff:65:9b (try 1/3)
Apr 24 15:50:27 Pavilion-dv5 wpa_supplicant[1189]: wlan0: Associated with 00:1d:1c:ff:65:9b
Apr 24 15:50:27 Pavilion-dv5 kernel: [  200.980159] wlan0: RX AssocResp from 00:1d:1c:ff:65:9b (capab=0x431 status=0 aid=1)
Apr 24 15:50:27 Pavilion-dv5 kernel: [  200.982008] wlan0: associated
Apr 24 15:50:27 Pavilion-dv5 kernel: [  200.982067] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Apr 24 15:50:27 Pavilion-dv5 kernel: [  200.982214] cfg80211: Calling CRDA for country: GR
Apr 24 15:50:27 Pavilion-dv5 NetworkManager[1177]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Apr 24 15:50:27 Pavilion-dv5 kernel: [  200.992322] cfg80211: Regulatory domain changed to country: GR
Apr 24 15:50:27 Pavilion-dv5 kernel: [  200.992330] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr 24 15:50:27 Pavilion-dv5 kernel: [  200.992337] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Apr 24 15:50:27 Pavilion-dv5 kernel: [  200.992343] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Apr 24 15:50:27 Pavilion-dv5 kernel: [  200.992348] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Apr 24 15:50:27 Pavilion-dv5 kernel: [  200.992354] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
Apr 24 15:50:27 Pavilion-dv5 wpa_supplicant[1189]: wlan0: WPA: Key negotiation completed with 00:1d:1c:ff:65:9b [PTK=TKIP GTK=TKIP]
Apr 24 15:50:27 Pavilion-dv5 wpa_supplicant[1189]: wlan0: CTRL-EVENT-CONNECTED - Connection to 00:1d:1c:ff:65:9b completed (auth) [id=0 id_str=]
Apr 24 15:50:27 Pavilion-dv5 NetworkManager[1177]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Apr 24 15:50:27 Pavilion-dv5 NetworkManager[1177]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Wi-Fi'.
Apr 24 15:50:27 Pavilion-dv5 NetworkManager[1177]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 24 15:50:27 Pavilion-dv5 NetworkManager[1177]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Apr 24 15:50:27 Pavilion-dv5 NetworkManager[1177]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Apr 24 15:50:27 Pavilion-dv5 NetworkManager[1177]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr 24 15:50:27 Pavilion-dv5 NetworkManager[1177]: <info> dhclient started with pid 2749
Apr 24 15:50:27 Pavilion-dv5 NetworkManager[1177]: <info> Activation (wlan0) Beginning IP6 addrconf.
Apr 24 15:50:27 Pavilion-dv5 NetworkManager[1177]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Apr 24 15:50:27 Pavilion-dv5 dhclient: Internet Systems Consortium DHCP Client 4.2.4
Apr 24 15:50:27 Pavilion-dv5 dhclient: Copyright 2004-2012 Internet Systems Consortium.
Apr 24 15:50:27 Pavilion-dv5 dhclient: All rights reserved.
Apr 24 15:50:27 Pavilion-dv5 dhclient: For info, please visit https://www.isc.org/software/dhcp/
Apr 24 15:50:27 Pavilion-dv5 dhclient: 
Apr 24 15:50:27 Pavilion-dv5 dhclient: Listening on LPF/wlan0/00:16:ea:9d:64:fe
Apr 24 15:50:27 Pavilion-dv5 dhclient: Sending on   LPF/wlan0/00:16:ea:9d:64:fe
Apr 24 15:50:27 Pavilion-dv5 dhclient: Sending on   Socket/fallback
Apr 24 15:50:27 Pavilion-dv5 dhclient: DHCPREQUEST of 192.168.1.82 on wlan0 to 255.255.255.255 port 67 (xid=0xe32743c)
Apr 24 15:50:27 Pavilion-dv5 NetworkManager[1177]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Apr 24 15:50:27 Pavilion-dv5 dhclient: DHCPACK of 192.168.1.82 from 192.168.1.254
Apr 24 15:50:27 Pavilion-dv5 dhclient: bound to 192.168.1.82 -- renewal in 41114 seconds.
Apr 24 15:50:27 Pavilion-dv5 NetworkManager[1177]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Apr 24 15:50:27 Pavilion-dv5 NetworkManager[1177]: <info>   address 192.168.1.82
Apr 24 15:50:27 Pavilion-dv5 NetworkManager[1177]: <info>   prefix 24 (255.255.255.0)
Apr 24 15:50:27 Pavilion-dv5 NetworkManager[1177]: <info>   gateway 192.168.1.254
Apr 24 15:50:27 Pavilion-dv5 NetworkManager[1177]: <info>   hostname 'Pavilion-dv5'
Apr 24 15:50:27 Pavilion-dv5 NetworkManager[1177]: <info>   nameserver '192.168.1.254'
Apr 24 15:50:27 Pavilion-dv5 NetworkManager[1177]: <info>   domain name 'lan'
Apr 24 15:50:27 Pavilion-dv5 NetworkManager[1177]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Apr 24 15:50:27 Pavilion-dv5 NetworkManager[1177]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Apr 24 15:50:27 Pavilion-dv5 avahi-daemon[1139]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.82.
Apr 24 15:50:27 Pavilion-dv5 avahi-daemon[1139]: New relevant interface wlan0.IPv4 for mDNS.
Apr 24 15:50:27 Pavilion-dv5 avahi-daemon[1139]: Registering new address record for 192.168.1.82 on wlan0.IPv4.
Apr 24 15:50:28 Pavilion-dv5 NetworkManager[1177]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Apr 24 15:50:28 Pavilion-dv5 NetworkManager[1177]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Apr 24 15:50:28 Pavilion-dv5 NetworkManager[1177]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Apr 24 15:50:29 Pavilion-dv5 NetworkManager[1177]: <info> Policy set 'Wi-Fi' (wlan0) as default for IPv4 routing and DNS.
Apr 24 15:50:29 Pavilion-dv5 NetworkManager[1177]: <info> Writing DNS information to /sbin/resolvconf
Apr 24 15:50:29 Pavilion-dv5 dnsmasq[1527]: setting upstream servers from DBus
Apr 24 15:50:29 Pavilion-dv5 dnsmasq[1527]: using nameserver 192.168.1.254#53
Apr 24 15:50:29 Pavilion-dv5 NetworkManager[1177]: <info> Activation (wlan0) successful, device activated.
Apr 24 15:50:29 Pavilion-dv5 dbus[940]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Apr 24 15:50:29 Pavilion-dv5 dbus[940]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Apr 24 15:50:29 Pavilion-dv5 avahi-daemon[1139]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::216:eaff:fe9d:64fe.
Apr 24 15:50:29 Pavilion-dv5 avahi-daemon[1139]: New relevant interface wlan0.IPv6 for mDNS.
Apr 24 15:50:29 Pavilion-dv5 avahi-daemon[1139]: Registering new address record for fe80::216:eaff:fe9d:64fe on wlan0.*.
Apr 24 15:50:35 Pavilion-dv5 ntpdate[2852]: adjust time server 91.189.94.4 offset 0.198282 sec
Apr 24 15:50:47 Pavilion-dv5 NetworkManager[1177]: <info> (wlan0): IP6 addrconf timed out or failed.
Apr 24 15:50:47 Pavilion-dv5 NetworkManager[1177]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Apr 24 15:50:47 Pavilion-dv5 NetworkManager[1177]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Apr 24 15:50:47 Pavilion-dv5 NetworkManager[1177]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Apr 24 15:51:39 Pavilion-dv5 wpa_supplicant[1189]: wlan0: WPA: Group rekeying completed with 00:1d:1c:ff:65:9b [GTK=TKIP]
Apr 24 16:11:41 Pavilion-dv5 NetworkManager[1177]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted

```

---

### Post by Toz on 2013-04-24
> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Perhaps related: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1118446]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1118446")

---

### Post by jierro on 2013-04-30
So I tried to disable the N-mode of iwlwifi driver:
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi

```

but on second command I get this
```

jierro@Pavilion-dv5:~$ sudo modprobe -rfv iwlwifi
[sudo] password for jierro: 
FATAL: Module iwlwifi is in use.

```

Even if I disable wifi via hardware switch or connect with ethernet cable, I cant remove this module.

---

