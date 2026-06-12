---
title: "Thinkpad W500 wireless connection keeps dropping"
date: 2010-10-27
forum: Networking &amp; Wireless
---

### Post by lunatico on 2010-10-27
Hi All,

Basically the title summarizes it. I have a Thinkpad W500 with:
```
Network controller: Intel Corporation Wireless WiFi Link 5300
```
I have Ubuntu 10.04 32bit installed:
```
Linux dani-laptop 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:48:22 UTC 2010 i686 GNU/Linux

```
It has been working fine since I installed 10.04 but recently (end of last week I think) it stared dropping the wireless connection very often. So it will disconnect and reconnect, but I can't seem to find a pattern, sometimes it goes for hours without an issue and sometimes it does it several times in a row.

Bellow is an extract of syslogs from when this happens. But not sure if what I need is there... the only weird thing I can see is:
```
Oct 27 18:58:33 username-laptop wpa_supplicant[1296]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
```

Any help is much appreciated!


```
Oct 27 18:58:32 username-laptop wpa_supplicant[1296]: Trying to associate with 00:1e:be:a6:c0:0f (SSID='accessp' freq=5280 MHz)
Oct 27 18:58:32 username-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associating
Oct 27 18:58:32 username-laptop kernel: [123835.372217] wlan0: deauthenticating from 00:1e:7a:6f:d9:90 by local choice (reason=3)
Oct 27 18:58:32 username-laptop kernel: [123835.411394] wlan0: deauthenticating from 00:1e:7a:6f:d9:90 by local choice (reason=3)
Oct 27 18:58:33 username-laptop wpa_supplicant[1296]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct 27 18:58:33 username-laptop kernel: [123835.414803] wlan0: direct probe to AP 00:1e:be:a6:c0:0f (try 1)
Oct 27 18:58:33 username-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Oct 27 18:58:33 username-laptop kernel: [123835.612570] wlan0: direct probe to AP 00:1e:be:a6:c0:0f (try 2)
Oct 27 18:58:33 username-laptop kernel: [123835.613015] wlan0: direct probe responded
Oct 27 18:58:33 username-laptop kernel: [123835.613022] wlan0: authenticate with AP 00:1e:be:a6:c0:0f (try 1)
Oct 27 18:58:33 username-laptop kernel: [123835.613845] wlan0: authenticated
Oct 27 18:58:33 username-laptop kernel: [123835.613881] wlan0: associate with AP 00:1e:be:a6:c0:0f (try 1)
Oct 27 18:58:33 username-laptop kernel: [123835.616023] wlan0: RX AssocResp from 00:1e:be:a6:c0:0f (capab=0x11 status=0 aid=2)
Oct 27 18:58:33 username-laptop kernel: [123835.616029] wlan0: associated
Oct 27 18:58:33 username-laptop wpa_supplicant[1296]: Associated with 00:1e:be:a6:c0:0f
Oct 27 18:58:33 username-laptop wpa_supplicant[1296]: CTRL-EVENT-EAP-STARTED EAP authentication started
Oct 27 18:58:33 username-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> associated
Oct 27 18:58:35 username-laptop NetworkManager: <debug> [1288202315.001732] periodic_update(): Roamed from BSSID 00:1E:7A:6F:D9:90 (accessp) to 00:1E:BE:A6:C0:0F (accessp)
Oct 27 18:58:48 username-laptop NetworkManager: <info>  (wlan0): device state change: 8 -> 3 (reason 11)
Oct 27 18:58:48 username-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 11).
Oct 27 18:58:48 username-laptop NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 2794
Oct 27 18:58:48 username-laptop avahi-daemon[1050]: Withdrawing address record for 144.254.150.157 on wlan0.
Oct 27 18:58:48 username-laptop avahi-daemon[1050]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 144.254.150.157.
Oct 27 18:58:48 username-laptop avahi-daemon[1050]: Interface wlan0.IPv4 no longer relevant for mDNS.
Oct 27 18:58:48 username-laptop kernel: [123850.628566] wlan0: deauthenticating from 00:1e:be:a6:c0:0f by local choice (reason=3)
Oct 27 18:58:48 username-laptop wpa_supplicant[1296]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct 27 18:58:48 username-laptop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Oct 27 18:58:48 username-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'accessp'
Oct 27 18:58:48 username-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Oct 27 18:58:48 username-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Oct 27 18:58:48 username-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> disconnected
Oct 27 18:58:48 username-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Oct 27 18:58:48 username-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Oct 27 18:58:48 username-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Oct 27 18:58:48 username-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Oct 27 18:58:48 username-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Oct 27 18:58:48 username-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'accessp' has security, and secrets exist.  No new secrets needed.
Oct 27 18:58:48 username-laptop NetworkManager: <info>  Config: added 'ssid' value 'accessp'
Oct 27 18:58:48 username-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Oct 27 18:58:48 username-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-EAP'
Oct 27 18:58:48 username-laptop NetworkManager: <info>  Config: added 'password' value '<omitted>'
Oct 27 18:58:48 username-laptop NetworkManager: <info>  Config: added 'eap' value 'PEAP'
Oct 27 18:58:48 username-laptop NetworkManager: <info>  Config: added 'fragment_size' value '1300'
Oct 27 18:58:48 username-laptop NetworkManager: <info>  Config: added 'phase2' value 'auth=MSCHAPV2'
Oct 27 18:58:48 username-laptop NetworkManager: <info>  Config: added 'identity' value 'username'
Oct 27 18:58:48 username-laptop NetworkManager: <info>  Config: added 'anonymous_identity' value 'anonymous'
Oct 27 18:58:48 username-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Oct 27 18:58:48 username-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Oct 27 18:58:48 username-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Oct 27 18:58:48 username-laptop postfix/master[1404]: reload -- version 2.7.0, configuration /etc/postfix
Oct 27 18:58:50 username-laptop wpa_supplicant[1296]: Trying to associate with 00:1e:be:a6:c0:0f (SSID='accessp' freq=5280 MHz)
Oct 27 18:58:50 username-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Oct 27 18:58:50 username-laptop kernel: [123853.277128] wlan0: deauthenticating from 00:1e:be:a6:c0:0f by local choice (reason=3)
Oct 27 18:58:50 username-laptop kernel: [123853.307151] wlan0: direct probe to AP 00:1e:be:a6:c0:0f (try 1)
Oct 27 18:58:50 username-laptop kernel: [123853.307731] wlan0: direct probe responded
Oct 27 18:58:50 username-laptop kernel: [123853.307738] wlan0: authenticate with AP 00:1e:be:a6:c0:0f (try 1)
Oct 27 18:58:50 username-laptop kernel: [123853.308627] wlan0: authenticated
Oct 27 18:58:50 username-laptop kernel: [123853.308964] wlan0: associate with AP 00:1e:be:a6:c0:0f (try 1)
Oct 27 18:58:50 username-laptop kernel: [123853.310722] wlan0: RX AssocResp from 00:1e:be:a6:c0:0f (capab=0x11 status=0 aid=2)
Oct 27 18:58:50 username-laptop kernel: [123853.310729] wlan0: associated
Oct 27 18:58:50 username-laptop wpa_supplicant[1296]: Associated with 00:1e:be:a6:c0:0f
Oct 27 18:58:50 username-laptop wpa_supplicant[1296]: CTRL-EVENT-EAP-STARTED EAP authentication started
Oct 27 18:58:50 username-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Oct 27 18:59:20 username-laptop wpa_supplicant[1296]: CTRL-EVENT-EAP-STARTED EAP authentication started
Oct 27 18:59:20 username-laptop wpa_supplicant[1296]: CTRL-EVENT-EAP-METHOD EAP vendor 0 method 25 (PEAP) selected
Oct 27 18:59:20 username-laptop wpa_supplicant[1296]: OpenSSL: tls_connection_handshake - Failed to read possible Application Data error:00000000:lib(0):func(0):reason(0)
Oct 27 18:59:20 username-laptop wpa_supplicant[1296]: EAP-TLV: TLV Result - Success - EAP-TLV/Phase2 Completed
Oct 27 18:59:20 username-laptop wpa_supplicant[1296]: CTRL-EVENT-EAP-SUCCESS EAP authentication completed successfully
Oct 27 18:59:20 username-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Oct 27 18:59:20 username-laptop wpa_supplicant[1296]: WPA: Key negotiation completed with 00:1e:be:a6:c0:0f [PTK=CCMP GTK=TKIP]
Oct 27 18:59:20 username-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Oct 27 18:59:20 username-laptop wpa_supplicant[1296]: CTRL-EVENT-CONNECTED - Connection to 00:1e:be:a6:c0:0f completed (reauth) [id=1 id_str=]
Oct 27 18:59:20 username-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Oct 27 18:59:20 username-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'accessp'.
Oct 27 18:59:20 username-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Oct 27 18:59:20 username-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Oct 27 18:59:20 username-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Oct 27 18:59:20 username-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Oct 27 18:59:20 username-laptop NetworkManager: <info>  dhclient started with pid 4665
Oct 27 18:59:20 username-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Oct 27 18:59:20 username-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Oct 27 18:59:20 username-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Oct 27 18:59:20 username-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Oct 27 18:59:20 username-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Oct 27 18:59:20 username-laptop dhclient: Copyright 2004-2009 Internet Systems Consortium.
Oct 27 18:59:20 username-laptop dhclient: All rights reserved.
Oct 27 18:59:20 username-laptop dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct 27 18:59:20 username-laptop dhclient: 
Oct 27 18:59:20 username-laptop NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Oct 27 18:59:20 username-laptop dhclient: Listening on LPF/wlan0/00:21:6a:8d:3f:e8
Oct 27 18:59:20 username-laptop dhclient: Sending on   LPF/wlan0/00:21:6a:8d:3f:e8
Oct 27 18:59:20 username-laptop dhclient: Sending on   Socket/fallback
Oct 27 18:59:24 username-laptop dhclient: DHCPREQUEST of 144.254.150.157 on wlan0 to 255.255.255.255 port 67
Oct 27 18:59:24 username-laptop dhclient: DHCPACK of 144.254.150.157 from 10.1.1.2
Oct 27 18:59:24 username-laptop dhclient: bound to 144.254.150.157 -- renewal in 6147 seconds.
Oct 27 18:59:24 username-laptop NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> reboot
Oct 27 18:59:24 username-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Oct 27 18:59:24 username-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Oct 27 18:59:24 username-laptop NetworkManager: <info>    address 144.254.150.157
Oct 27 18:59:24 username-laptop NetworkManager: <info>    prefix 24 (255.255.255.0)
Oct 27 18:59:24 username-laptop NetworkManager: <info>    gateway 144.254.150.1
Oct 27 18:59:24 username-laptop NetworkManager: <info>    hostname 'username-laptop'
Oct 27 18:59:24 username-laptop NetworkManager: <info>    nameserver '144.254.71.184'
Oct 27 18:59:24 username-laptop NetworkManager: <info>    nameserver '144.254.10.123'
Oct 27 18:59:24 username-laptop NetworkManager: <info>    domain name 'cisco.com'
Oct 27 18:59:24 username-laptop NetworkManager: <info>    wins '144.254.227.102'
Oct 27 18:59:24 username-laptop NetworkManager: <info>    wins '171.69.2.87'
Oct 27 18:59:24 username-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Oct 27 18:59:24 username-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Oct 27 18:59:24 username-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Oct 27 18:59:24 username-laptop avahi-daemon[1050]: Joining mDNS multicast group on interface wlan0.IPv4 with address 144.254.150.157.
Oct 27 18:59:24 username-laptop avahi-daemon[1050]: New relevant interface wlan0.IPv4 for mDNS.
Oct 27 18:59:24 username-laptop avahi-daemon[1050]: Registering new address record for 144.254.150.157 on wlan0.IPv4.
Oct 27 18:59:25 username-laptop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Oct 27 18:59:25 username-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Oct 27 18:59:25 username-laptop NetworkManager: <info>  Activation (wlan0) successful, device activated.
Oct 27 18:59:25 username-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Oct 27 18:59:25 username-laptop postfix/master[1404]: reload -- version 2.7.0, configuration /etc/postfix
Oct 27 18:59:29 username-laptop ntpdate[4765]: no server suitable for synchronization found
```

---

### Post by not_a_phd on 2010-11-01
I have almost identical symptoms on an eeePC901 with RaLink 2860 chipset running ra2860sta drivers. Posted my issue as a new thread [http://ubuntuforums.org/showthread.php?t=1610960](http://ubuntuforums.org/showthread.php?t=1610960) . Mine cuts out and reconnects every 5 - 10 seconds. 

Did you ever resolve your problem?

---

### Post by lunatico on 2010-11-02
> **not_a_phd said:**
> 
Did you ever resolve your problem?

Well you problem does look similar, but most likely they're not. Different wireless cards, different Ubuntu release.
And mine doesn't do that every 5 seconds.
In fact I think I fixed it.... did a BIOS upgrade and haven't noticed any disconnections since. Fingers crossed.

For clarity, my laptop is a Thinkpad W500.

---

### Post by lunatico on 2010-11-04
Even after the BIOS upgrade this still happens, not as often as before but still happens. :(

---

### Post by lunatico on 2010-11-05
[https://answers.edge.launchpad.net/ubuntu/+source/gnome-nettool/+question/132614](https://answers.edge.launchpad.net/ubuntu/+source/gnome-nettool/+question/132614)

---

### Post by lunatico on 2010-11-08
Still trying to find a solution.
Anyone knows how to enable fast reconnect?

Back in the days when wpa_supplicant configuration had to be done via config file and command line this was possible but not sure how to do this now on 10.04.

---

### Post by lunatico on 2010-11-24
I've found that this is a network-manager issue. I have uninstalled network-manager and installed wicd and the reconnections are gone.
Not ideal because I like NM and it has features that I need like VPN and USB 3G donggle support.

---

