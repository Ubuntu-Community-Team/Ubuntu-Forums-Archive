---
title: "Problems connecting wirelessly"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by lduperval on 2010-01-07
Hi,

I have a D-Link DIR-615 wireless router and my wireless card is a Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03) card.

I installed the wireless router and it worked fine. Then, I suspended my system and since then, wireless has stopped working. It works in Windows without a hitch. I don't understand what the problem is.

With NetworkManager, I get logging output that looks like this:

```
Jan  7 15:48:33 hplaptop NetworkManager: <info>  Activation (eth1) starting connection 'myssid'
Jan  7 15:48:33 hplaptop NetworkManager: <info>  (eth1): device state change: 3 -> 4 (reason 0)
Jan  7 15:48:33 hplaptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jan  7 15:48:33 hplaptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Jan  7 15:48:33 hplaptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jan  7 15:48:33 hplaptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jan  7 15:48:33 hplaptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jan  7 15:48:33 hplaptop NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
Jan  7 15:48:33 hplaptop NetworkManager: <info>  Activation (eth1/wireless): access point 'myssid' has security, but secrets are required.
Jan  7 15:48:33 hplaptop NetworkManager: <info>  (eth1): device state change: 5 -> 6 (reason 0)
Jan  7 15:48:33 hplaptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jan  7 15:48:33 hplaptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jan  7 15:48:33 hplaptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Jan  7 15:48:33 hplaptop NetworkManager: <info>  (eth1): device state change: 6 -> 4 (reason 0)
Jan  7 15:48:33 hplaptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jan  7 15:48:33 hplaptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jan  7 15:48:33 hplaptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jan  7 15:48:33 hplaptop NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
Jan  7 15:48:33 hplaptop NetworkManager: <info>  Activation (eth1/wireless): connection 'myssid' has security, and secrets exist.  No new secrets needed.
Jan  7 15:48:33 hplaptop NetworkManager: <info>  Config: added 'ssid' value 'myssid'
Jan  7 15:48:33 hplaptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jan  7 15:48:33 hplaptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Jan  7 15:48:33 hplaptop NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Jan  7 15:48:33 hplaptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  7 15:48:33 hplaptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  7 15:48:33 hplaptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jan  7 15:48:33 hplaptop NetworkManager: <info>  Config: set interface ap_scan to 1
Jan  7 15:48:33 hplaptop NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Jan  7 15:48:38 hplaptop wpa_supplicant[1149]: CTRL-EVENT-SCAN-RESULTS 
Jan  7 15:48:38 hplaptop wpa_supplicant[1149]: WPS-AP-AVAILABLE 
Jan  7 15:48:38 hplaptop wpa_supplicant[1149]: Trying to associate with xx:xx:xx:xx:xx:xx (SSID='myssid' freq=2437 MHz)
Jan  7 15:48:38 hplaptop wpa_supplicant[1149]: Association request to the driver failed
Jan  7 15:48:38 hplaptop NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Jan  7 15:48:40 hplaptop wpa_supplicant[1149]: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Jan  7 15:48:40 hplaptop wpa_supplicant[1149]: Associated with xx:xx:xx:xx:xx:xx
Jan  7 15:48:40 hplaptop NetworkManager: <info>  (eth1): supplicant connection state:  associating -> associated
Jan  7 15:48:41 hplaptop NetworkManager: <info>  (eth1): supplicant connection state:  associated -> 4-way handshake
Jan  7 15:48:41 hplaptop wpa_supplicant[1149]: WPA: Key negotiation completed with xx:xx:xx:xx:xx:xx [PTK=CCMP GTK=CCMP]
Jan  7 15:48:41 hplaptop wpa_supplicant[1149]: CTRL-EVENT-CONNECTED - Connection to xx:xx:xx:xx:xx:xx completed (reauth) [id=0 id_str=]
Jan  7 15:48:41 hplaptop NetworkManager: <info>  (eth1): supplicant connection state:  4-way handshake -> group handshake
Jan  7 15:48:41 hplaptop NetworkManager: <info>  (eth1): supplicant connection state:  group handshake -> completed
Jan  7 15:48:41 hplaptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'myssid'.
Jan  7 15:48:41 hplaptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Jan  7 15:48:41 hplaptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Jan  7 15:48:41 hplaptop NetworkManager: <info>  (eth1): device state change: 5 -> 7 (reason 0)
Jan  7 15:48:41 hplaptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction (timeout in 45 seconds)
Jan  7 15:48:41 hplaptop dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan  7 15:48:41 hplaptop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan  7 15:48:41 hplaptop dhclient: All rights reserved.
Jan  7 15:48:41 hplaptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jan  7 15:48:41 hplaptop dhclient: 
Jan  7 15:48:41 hplaptop NetworkManager: <info>  dhclient started with pid 3081
Jan  7 15:48:41 hplaptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jan  7 15:48:41 hplaptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Jan  7 15:48:41 hplaptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) started...
Jan  7 15:48:41 hplaptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP6 Configure Get) complete.
Jan  7 15:48:41 hplaptop NetworkManager: <info>  DHCP: device eth1 state changed normal exit -> preinit
Jan  7 15:48:41 hplaptop dhclient: Listening on LPF/eth1/xx:xx:xx:xx:xx:xx
Jan  7 15:48:41 hplaptop dhclient: Sending on   LPF/eth1/xx:xx:xx:xx:xx:xx
Jan  7 15:48:41 hplaptop dhclient: Sending on   Socket/fallback
Jan  7 15:48:44 hplaptop dhclient: DHCPREQUEST of 192.168.0.13 on eth1 to 255.255.255.255 port 67
Jan  7 15:48:50 hplaptop dhclient: DHCPREQUEST of 192.168.0.13 on eth1 to 255.255.255.255 port 67
Jan  7 15:49:05 hplaptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Jan  7 15:49:11 hplaptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Jan  7 15:49:26 hplaptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
Jan  7 15:49:27 hplaptop NetworkManager: <info>  (eth1): DHCP transaction took too long, stopping it.
Jan  7 15:49:27 hplaptop NetworkManager: <info>  (eth1): canceled DHCP transaction, dhcp client pid 3081
Jan  7 15:49:27 hplaptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jan  7 15:49:27 hplaptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) started...
Jan  7 15:49:27 hplaptop NetworkManager: <info>  (eth1): device state change: 7 -> 9 (reason 5)
Jan  7 15:49:27 hplaptop NetworkManager: <info>  Activation (eth1) failed for access point (myssid)
Jan  7 15:49:27 hplaptop NetworkManager: <info>  Marking connection 'myssid' invalid.
Jan  7 15:49:27 hplaptop NetworkManager: <info>  Activation (eth1) failed.
Jan  7 15:49:27 hplaptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jan  7 15:49:27 hplaptop NetworkManager: <info>  (eth1): device state change: 9 -> 3 (reason 0)
Jan  7 15:49:27 hplaptop NetworkManager: <info>  (eth1): deactivating device (reason: 0).
Jan  7 15:49:27 hplaptop wpa_supplicant[1149]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jan  7 15:49:37 hplaptop wpa_supplicant[1149]: CTRL-EVENT-SCAN-RESULTS 


```

I read somewhere that wicd might work better so I tried installing it but I get an error saying it couldn't get an IP address. This is somme of the output of daemon.log:

```

Jan  7 16:33:57 hplaptop dhclient: There is already a pid file /var/run/dhclient.pid with pid 4860
Jan  7 16:33:57 hplaptop dhclient: killed old client process, removed PID file
Jan  7 16:33:57 hplaptop dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan  7 16:33:57 hplaptop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan  7 16:33:57 hplaptop dhclient: All rights reserved.
Jan  7 16:33:57 hplaptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jan  7 16:33:57 hplaptop dhclient: 
Jan  7 16:33:57 hplaptop dhclient: Listening on LPF/eth0/xx:xx:xx:xx:xx:xx
Jan  7 16:33:57 hplaptop dhclient: Sending on   LPF/eth0/xx:xx:xx:xx:xx:xx
Jan  7 16:33:57 hplaptop dhclient: Sending on   Socket/fallback
Jan  7 16:33:57 hplaptop dhclient: DHCPRELEASE on eth0 to 192.168.0.1 port 67
Jan  7 16:33:57 hplaptop dhclient: send_packet: Network is unreachable
Jan  7 16:33:57 hplaptop dhclient: send_packet: please consult README file regarding broadcast address.
Jan  7 16:33:58 hplaptop dhclient: receive_packet failed on eth0: Network is down
Jan  7 16:33:58 hplaptop avahi-autoipd(eth1)[4852]: SIOCSIFFLAGS failed: Permission denied
Jan  7 16:33:58 hplaptop avahi-autoipd(eth1)[4852]: Callout STOP, address 169.254.7.119 on interface eth1
Jan  7 16:33:58 hplaptop dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan  7 16:33:58 hplaptop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan  7 16:33:58 hplaptop dhclient: All rights reserved.
Jan  7 16:33:58 hplaptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jan  7 16:33:58 hplaptop dhclient: 
Jan  7 16:33:58 hplaptop dhclient: Listening on LPF/eth1/xx:xx:xx:xx:xx:xx
Jan  7 16:33:58 hplaptop dhclient: Sending on   LPF/eth1/xx:xx:xx:xx:xx:xx
Jan  7 16:33:58 hplaptop dhclient: Sending on   Socket/fallback
Jan  7 16:34:12 hplaptop dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan  7 16:34:12 hplaptop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan  7 16:34:12 hplaptop dhclient: All rights reserved.
Jan  7 16:34:12 hplaptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jan  7 16:34:12 hplaptop dhclient: 
Jan  7 16:34:13 hplaptop dhclient: Listening on LPF/eth1/xx:xx:xx:xx:xx:xx
Jan  7 16:34:13 hplaptop dhclient: Sending on   LPF/eth1/xx:xx:xx:xx:xx:xx
Jan  7 16:34:13 hplaptop dhclient: Sending on   Socket/fallback
Jan  7 16:34:17 hplaptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Jan  7 16:34:21 hplaptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Jan  7 16:34:32 hplaptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
Jan  7 16:34:48 hplaptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Jan  7 16:34:57 hplaptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Jan  7 16:35:06 hplaptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Jan  7 16:35:18 hplaptop dhclient: No DHCPOFFERS received.
Jan  7 16:35:18 hplaptop dhclient: No working leases in persistent database - sleeping.
Jan  7 16:35:18 hplaptop avahi-autoipd(eth1)[4981]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Jan  7 16:35:18 hplaptop avahi-autoipd(eth1)[4981]: Successfully called chroot().
Jan  7 16:35:18 hplaptop avahi-autoipd(eth1)[4981]: Successfully dropped root privileges.
Jan  7 16:35:18 hplaptop avahi-autoipd(eth1)[4981]: Starting with address 169.254.7.119
Jan  7 16:35:23 hplaptop avahi-autoipd(eth1)[4981]: Callout BIND, address 169.254.7.119 on interface eth1
Jan  7 16:35:27 hplaptop avahi-autoipd(eth1)[4981]: Successfully claimed IP address 169.254.7.119

```

I should be getting an address in the 192.168.x.x range but I don't.

Ay ideas what could be the problem?

Thanks,

L

---

### Post by lduperval on 2010-01-07
Let me add that I tried removing security and hiding the SSID, and so far it works. I would much prefer enabling security, though.

L

---

