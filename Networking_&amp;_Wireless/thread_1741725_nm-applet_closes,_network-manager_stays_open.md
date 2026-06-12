---
title: "nm-applet closes, network-manager stays open"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by rountrey on 2011-04-28
Hopefully someone can help, I have looked through the forums and launchpad and cannot find a fix. nm-applet is closing at random times, sometimes an hour, some times as little as 10 minutes. but it is becoming very annoying especially when doing online classes. 

When I run nm-applet from the terminal, it works fine for a while then it catches signal 15 and I don't know why. I am running Lucid 64 bit on an Asus X72D with an Atheros AR9285. This has been going on for a week, I also tried updating network-manager from the launchpad ppa to version 0.8.1.998 and it still closes.

Here is what I get from terminal:
```
** Message: applet now removed from the notification area
** Message: applet now embedded in the notification area
** (nm-applet:5714): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:5714): DEBUG: foo_client_state_changed_cb
** (nm-applet:5714): DEBUG: foo_client_state_changed_cb
** Message: Caught signal 15, shutting down...

```

Here is the log, with 2 crashes in it:
```

Apr 28 10:51:25 mammoth ntpdate[4603]: adjust time server 91.189.94.4 offset 0.242640 sec
Apr 28 11:10:16 mammoth NetworkManager[1089]: <info> (wlan0): device state change: 8 -> 3 (reason 38)
Apr 28 11:10:16 mammoth NetworkManager[1089]: <info> (wlan0): deactivating device (reason: 38).
Apr 28 11:10:16 mammoth NetworkManager[1089]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 4558
Apr 28 11:10:16 mammoth avahi-daemon[1093]: Withdrawing address record for 192.168.0.29 on wlan0.
Apr 28 11:10:16 mammoth avahi-daemon[1093]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.29.
Apr 28 11:10:16 mammoth avahi-daemon[1093]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr 28 11:10:16 mammoth NetworkManager[1089]: <info> Updating /etc/hosts with new system hostname
Apr 28 11:10:16 mammoth wpa_supplicant[1318]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Apr 28 11:10:16 mammoth nm-dispatcher.action: nm_dispatcher_action: Invalid connection: '(null)' / 'connection setting not found' invalid: 1
Apr 28 11:10:16 mammoth nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Apr 28 11:12:35 mammoth NetworkManager[1089]: <info> Activation (wlan0) starting connection 'Auto rountrey'
Apr 28 11:12:35 mammoth NetworkManager[1089]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Apr 28 11:12:35 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 28 11:12:35 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 28 11:12:35 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 28 11:12:35 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 28 11:12:35 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 28 11:12:35 mammoth NetworkManager[1089]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 28 11:12:35 mammoth NetworkManager[1089]: <info> Activation (wlan0/wireless): access point 'Auto rountrey' has security, but secrets are required.
Apr 28 11:12:35 mammoth NetworkManager[1089]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 28 11:12:35 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 28 11:12:35 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 28 11:12:35 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 28 11:12:35 mammoth NetworkManager[1089]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Apr 28 11:12:35 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 28 11:12:35 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 28 11:12:35 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 28 11:12:35 mammoth NetworkManager[1089]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 28 11:12:35 mammoth NetworkManager[1089]: <info> Activation (wlan0/wireless): connection 'Auto rountrey' has security, and secrets exist.  No new secrets needed.
Apr 28 11:12:35 mammoth NetworkManager[1089]: <info> Config: added 'ssid' value 'rountrey'
Apr 28 11:12:35 mammoth NetworkManager[1089]: <info> Config: added 'scan_ssid' value '1'
Apr 28 11:12:35 mammoth NetworkManager[1089]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 28 11:12:35 mammoth NetworkManager[1089]: <info> Config: added 'psk' value '<omitted>'
Apr 28 11:12:35 mammoth NetworkManager[1089]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Apr 28 11:12:35 mammoth NetworkManager[1089]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Apr 28 11:12:35 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 28 11:12:35 mammoth NetworkManager[1089]: <info> Config: set interface ap_scan to 1
Apr 28 11:12:35 mammoth NetworkManager[1089]: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Apr 28 11:12:35 mammoth NetworkManager[1089]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 28 11:12:37 mammoth wpa_supplicant[1318]: WPS-AP-AVAILABLE 
Apr 28 11:12:37 mammoth wpa_supplicant[1318]: Trying to associate with c0:3f:0e:28:7f:0a (SSID='rountrey' freq=2437 MHz)
Apr 28 11:12:37 mammoth NetworkManager[1089]: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr 28 11:12:37 mammoth wpa_supplicant[1318]: WPS-AP-AVAILABLE 
Apr 28 11:12:37 mammoth wpa_supplicant[1318]: Associated with c0:3f:0e:28:7f:0a
Apr 28 11:12:37 mammoth NetworkManager[1089]: <info> (wlan0): supplicant connection state:  associating -> associated
Apr 28 11:12:37 mammoth NetworkManager[1089]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Apr 28 11:12:37 mammoth wpa_supplicant[1318]: WPA: Key negotiation completed with c0:3f:0e:28:7f:0a [PTK=CCMP GTK=CCMP]
Apr 28 11:12:37 mammoth wpa_supplicant[1318]: CTRL-EVENT-CONNECTED - Connection to c0:3f:0e:28:7f:0a completed (reauth) [id=0 id_str=]
Apr 28 11:12:37 mammoth NetworkManager[1089]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Apr 28 11:12:37 mammoth NetworkManager[1089]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Apr 28 11:12:37 mammoth NetworkManager[1089]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'rountrey'.
Apr 28 11:12:37 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 28 11:12:37 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Apr 28 11:12:37 mammoth NetworkManager[1089]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Apr 28 11:12:37 mammoth NetworkManager[1089]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr 28 11:12:37 mammoth NetworkManager[1089]: <info> dhclient started with pid 5145
Apr 28 11:12:37 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Apr 28 11:12:37 mammoth dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 28 11:12:37 mammoth dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 28 11:12:37 mammoth dhclient: All rights reserved.
Apr 28 11:12:37 mammoth dhclient: For info, please visit https://www.isc.org/software/dhcp/
Apr 28 11:12:37 mammoth dhclient: 
Apr 28 11:12:37 mammoth NetworkManager[1089]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Apr 28 11:12:37 mammoth dhclient: Listening on LPF/wlan0/1c:4b:d6:fb:75:fe
Apr 28 11:12:37 mammoth dhclient: Sending on   LPF/wlan0/1c:4b:d6:fb:75:fe
Apr 28 11:12:37 mammoth dhclient: Sending on   Socket/fallback
Apr 28 11:12:37 mammoth dhclient: DHCPREQUEST of 192.168.0.29 on wlan0 to 255.255.255.255 port 67
Apr 28 11:12:42 mammoth dhclient: DHCPREQUEST of 192.168.0.29 on wlan0 to 255.255.255.255 port 67
Apr 28 11:12:42 mammoth dhclient: DHCPACK of 192.168.0.29 from 192.168.0.1
Apr 28 11:12:42 mammoth dhclient: bound to 192.168.0.29 -- renewal in 264902 seconds.
Apr 28 11:12:42 mammoth NetworkManager[1089]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Apr 28 11:12:42 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Apr 28 11:12:42 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Apr 28 11:12:42 mammoth NetworkManager[1089]: <info>   address 192.168.0.29
Apr 28 11:12:42 mammoth NetworkManager[1089]: <info>   prefix 24 (255.255.255.0)
Apr 28 11:12:42 mammoth NetworkManager[1089]: <info>   gateway 192.168.0.1
Apr 28 11:12:42 mammoth NetworkManager[1089]: <info>   nameserver '192.168.0.1'
Apr 28 11:12:42 mammoth NetworkManager[1089]: <info>   domain name 'rountrey.net'
Apr 28 11:12:42 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Apr 28 11:12:42 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Apr 28 11:12:42 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Apr 28 11:12:42 mammoth avahi-daemon[1093]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.29.
Apr 28 11:12:42 mammoth avahi-daemon[1093]: New relevant interface wlan0.IPv4 for mDNS.
Apr 28 11:12:42 mammoth avahi-daemon[1093]: Registering new address record for 192.168.0.29 on wlan0.IPv4.
Apr 28 11:12:43 mammoth NetworkManager[1089]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Apr 28 11:12:43 mammoth NetworkManager[1089]: <info> Policy set 'Auto rountrey' (wlan0) as default for IPv4 routing and DNS.
Apr 28 11:12:43 mammoth NetworkManager[1089]: <info> Updating /etc/hosts with new system hostname
Apr 28 11:12:43 mammoth NetworkManager[1089]: <info> Activation (wlan0) successful, device activated.
Apr 28 11:12:43 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Apr 28 11:12:43 mammoth nm-dispatcher.action: nm_dispatcher_action: Invalid connection: '(null)' / 'connection setting not found' invalid: 1
Apr 28 11:12:43 mammoth nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Apr 28 11:12:50 mammoth ntpdate[5188]: adjust time server 91.189.94.4 offset -0.271082 sec
Apr 28 11:30:14 mammoth NetworkManager[1089]: <info> (wlan0): device state change: 8 -> 3 (reason 38)
Apr 28 11:30:14 mammoth NetworkManager[1089]: <info> (wlan0): deactivating device (reason: 38).
Apr 28 11:30:14 mammoth NetworkManager[1089]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 5145
Apr 28 11:30:14 mammoth avahi-daemon[1093]: Withdrawing address record for 192.168.0.29 on wlan0.
Apr 28 11:30:14 mammoth avahi-daemon[1093]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.29.
Apr 28 11:30:14 mammoth avahi-daemon[1093]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr 28 11:30:14 mammoth NetworkManager[1089]: <info> Updating /etc/hosts with new system hostname
Apr 28 11:30:14 mammoth wpa_supplicant[1318]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Apr 28 11:30:15 mammoth nm-dispatcher.action: nm_dispatcher_action: Invalid connection: '(null)' / 'connection setting not found' invalid: 1
Apr 28 11:30:15 mammoth nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Apr 28 11:32:32 mammoth NetworkManager[1089]: <info> Activation (wlan0) starting connection 'Auto rountrey'
Apr 28 11:32:32 mammoth NetworkManager[1089]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Apr 28 11:32:32 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 28 11:32:32 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 28 11:32:32 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 28 11:32:32 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 28 11:32:32 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 28 11:32:32 mammoth NetworkManager[1089]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 28 11:32:32 mammoth NetworkManager[1089]: <info> Activation (wlan0/wireless): access point 'Auto rountrey' has security, but secrets are required.
Apr 28 11:32:32 mammoth NetworkManager[1089]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Apr 28 11:32:32 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 28 11:32:32 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 28 11:32:32 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 28 11:32:32 mammoth NetworkManager[1089]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Apr 28 11:32:32 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 28 11:32:32 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 28 11:32:32 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 28 11:32:32 mammoth NetworkManager[1089]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Apr 28 11:32:32 mammoth NetworkManager[1089]: <info> Activation (wlan0/wireless): connection 'Auto rountrey' has security, and secrets exist.  No new secrets needed.
Apr 28 11:32:32 mammoth NetworkManager[1089]: <info> Config: added 'ssid' value 'rountrey'
Apr 28 11:32:32 mammoth NetworkManager[1089]: <info> Config: added 'scan_ssid' value '1'
Apr 28 11:32:32 mammoth NetworkManager[1089]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 28 11:32:32 mammoth NetworkManager[1089]: <info> Config: added 'psk' value '<omitted>'
Apr 28 11:32:32 mammoth NetworkManager[1089]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Apr 28 11:32:32 mammoth NetworkManager[1089]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Apr 28 11:32:32 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 28 11:32:32 mammoth NetworkManager[1089]: <info> Config: set interface ap_scan to 1
Apr 28 11:32:32 mammoth NetworkManager[1089]: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Apr 28 11:32:32 mammoth NetworkManager[1089]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr 28 11:32:33 mammoth wpa_supplicant[1318]: WPS-AP-AVAILABLE 
Apr 28 11:32:33 mammoth wpa_supplicant[1318]: Trying to associate with c0:3f:0e:28:7f:0a (SSID='rountrey' freq=2437 MHz)
Apr 28 11:32:33 mammoth NetworkManager[1089]: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr 28 11:32:33 mammoth wpa_supplicant[1318]: WPS-AP-AVAILABLE 
Apr 28 11:32:33 mammoth wpa_supplicant[1318]: Associated with c0:3f:0e:28:7f:0a
Apr 28 11:32:33 mammoth NetworkManager[1089]: <info> (wlan0): supplicant connection state:  associating -> associated
Apr 28 11:32:33 mammoth NetworkManager[1089]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Apr 28 11:32:33 mammoth wpa_supplicant[1318]: WPA: Key negotiation completed with c0:3f:0e:28:7f:0a [PTK=CCMP GTK=CCMP]
Apr 28 11:32:33 mammoth wpa_supplicant[1318]: CTRL-EVENT-CONNECTED - Connection to c0:3f:0e:28:7f:0a completed (reauth) [id=0 id_str=]
Apr 28 11:32:33 mammoth NetworkManager[1089]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Apr 28 11:32:33 mammoth NetworkManager[1089]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Apr 28 11:32:33 mammoth NetworkManager[1089]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'rountrey'.
Apr 28 11:32:33 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 28 11:32:33 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Apr 28 11:32:33 mammoth NetworkManager[1089]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Apr 28 11:32:33 mammoth NetworkManager[1089]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr 28 11:32:33 mammoth NetworkManager[1089]: <info> dhclient started with pid 5717
Apr 28 11:32:33 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Apr 28 11:32:33 mammoth dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 28 11:32:33 mammoth dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 28 11:32:33 mammoth dhclient: All rights reserved.
Apr 28 11:32:33 mammoth dhclient: For info, please visit https://www.isc.org/software/dhcp/
Apr 28 11:32:33 mammoth dhclient: 
Apr 28 11:32:33 mammoth NetworkManager[1089]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Apr 28 11:32:33 mammoth dhclient: Listening on LPF/wlan0/1c:4b:d6:fb:75:fe
Apr 28 11:32:33 mammoth dhclient: Sending on   LPF/wlan0/1c:4b:d6:fb:75:fe
Apr 28 11:32:33 mammoth dhclient: Sending on   Socket/fallback
Apr 28 11:32:33 mammoth dhclient: DHCPREQUEST of 192.168.0.29 on wlan0 to 255.255.255.255 port 67
Apr 28 11:32:38 mammoth dhclient: DHCPREQUEST of 192.168.0.29 on wlan0 to 255.255.255.255 port 67
Apr 28 11:32:38 mammoth dhclient: DHCPACK of 192.168.0.29 from 192.168.0.1
Apr 28 11:32:38 mammoth dhclient: bound to 192.168.0.29 -- renewal in 288993 seconds.
Apr 28 11:32:38 mammoth NetworkManager[1089]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Apr 28 11:32:38 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Apr 28 11:32:38 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Apr 28 11:32:38 mammoth NetworkManager[1089]: <info>   address 192.168.0.29
Apr 28 11:32:38 mammoth NetworkManager[1089]: <info>   prefix 24 (255.255.255.0)
Apr 28 11:32:38 mammoth NetworkManager[1089]: <info>   gateway 192.168.0.1
Apr 28 11:32:38 mammoth NetworkManager[1089]: <info>   nameserver '192.168.0.1'
Apr 28 11:32:38 mammoth NetworkManager[1089]: <info>   domain name 'rountrey.net'
Apr 28 11:32:38 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Apr 28 11:32:38 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Apr 28 11:32:38 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Apr 28 11:32:38 mammoth avahi-daemon[1093]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.29.
Apr 28 11:32:38 mammoth avahi-daemon[1093]: New relevant interface wlan0.IPv4 for mDNS.
Apr 28 11:32:38 mammoth avahi-daemon[1093]: Registering new address record for 192.168.0.29 on wlan0.IPv4.
Apr 28 11:32:39 mammoth NetworkManager[1089]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Apr 28 11:32:39 mammoth NetworkManager[1089]: <info> Policy set 'Auto rountrey' (wlan0) as default for IPv4 routing and DNS.
Apr 28 11:32:39 mammoth NetworkManager[1089]: <info> Updating /etc/hosts with new system hostname
Apr 28 11:32:39 mammoth NetworkManager[1089]: <info> Activation (wlan0) successful, device activated.
Apr 28 11:32:39 mammoth NetworkManager[1089]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Apr 28 11:32:39 mammoth nm-dispatcher.action: nm_dispatcher_action: Invalid connection: '(null)' / 'connection setting not found' invalid: 1
Apr 28 11:32:39 mammoth nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Apr 28 11:32:42 mammoth ntpdate[5761]: adjust time server 91.189.94.4 offset 0.290317 sec

```

---

### Post by SnappyU on 2011-04-28
It seems like you are not alone.

[http://ubuntuforums.org/showthread.php?t=1722010](http://ubuntuforums.org/showthread.php?t=1722010)

For awhile, I thought my wifi is going nuts.  And I almost had a reason to upgrade my machine! ;)

It seems to be a bug in the new nm-applet.  It was working fine from Jaunty till maverick.

---

### Post by SnappyU on 2011-04-28
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/664763](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/664763)

---

