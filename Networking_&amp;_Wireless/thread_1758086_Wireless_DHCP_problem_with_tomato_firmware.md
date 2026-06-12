---
title: "Wireless DHCP problem with tomato firmware"
date: 2011-05-14
forum: Networking &amp; Wireless
---

### Post by danielsbrewer on 2011-05-14
Hello,

I can't seem to get wireless DHCP to work in my home wireless network.  In summary, if I ask network-manager to use DHCP then the wireless connection fails, but if I provide the information it works.  The DHCP works fine on at least three other wireless networks that I have tried.  My wireless router runs the tomato firmware.  Other devices such as an iphone and android phone work fine with DHCP on my home network.

My wireless interface is an Intel Corporation WiFi Link 5100.

I wondered whether it was somethign to do with ipv6 so I disabled it on my netbook, by adding the following sysctrl.conf:
```

net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default_disable = 1
net.ipv6.conf.lo.disable = 1

```
This did not help.

Here is the relevant bit from the logs:
```
May 14 07:45:35 AcerAspireOne NetworkManager[469]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
May 14 07:45:35 AcerAspireOne NetworkManager[469]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
May 14 07:45:35 AcerAspireOne NetworkManager[469]: <info> (wlan1): device state change: 6 -> 4 (reason 0)
May 14 07:45:35 AcerAspireOne NetworkManager[469]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
May 14 07:45:35 AcerAspireOne NetworkManager[469]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
May 14 07:45:35 AcerAspireOne NetworkManager[469]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
May 14 07:45:35 AcerAspireOne NetworkManager[469]: <info> (wlan1): device state change: 4 -> 5 (reason 0)
May 14 07:45:35 AcerAspireOne NetworkManager[469]: <info> Activation (wlan1/wireless): connection 'Auto BrewerNet' has security, and secrets exist.  No new secrets needed.
May 14 07:45:35 AcerAspireOne NetworkManager[469]: <info> Config: added 'ssid' value 'BrewerNet'
May 14 07:45:35 AcerAspireOne NetworkManager[469]: <info> Config: added 'scan_ssid' value '1'
May 14 07:45:35 AcerAspireOne NetworkManager[469]: <info> Config: added 'key_mgmt' value 'NONE'
May 14 07:45:35 AcerAspireOne NetworkManager[469]: <info> Config: added 'auth_alg' value 'OPEN'
May 14 07:45:35 AcerAspireOne NetworkManager[469]: <info> Config: added 'wep_key0' value '<omitted>'
May 14 07:45:35 AcerAspireOne NetworkManager[469]: <info> Config: added 'wep_tx_keyidx' value '0'
May 14 07:45:35 AcerAspireOne NetworkManager[469]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May 14 07:45:35 AcerAspireOne NetworkManager[469]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
May 14 07:45:35 AcerAspireOne NetworkManager[469]: <info> Config: set interface ap_scan to 1
May 14 07:45:35 AcerAspireOne NetworkManager[469]: <info> (wlan1): supplicant connection state:  disconnected -> scanning
May 14 07:45:38 AcerAspireOne wpa_supplicant[528]: Trying to associate with 00:0d:0b:d4:ba:3c (SSID='BrewerNet' freq=2452 MHz)
May 14 07:45:38 AcerAspireOne NetworkManager[469]: <info> (wlan1): supplicant connection state:  scanning -> associating
May 14 07:45:38 AcerAspireOne wpa_supplicant[528]: Associated with 00:0d:0b:d4:ba:3c
May 14 07:45:38 AcerAspireOne wpa_supplicant[528]: CTRL-EVENT-CONNECTED - Connection to 00:0d:0b:d4:ba:3c completed (auth) [id=0 id_str=]
May 14 07:45:38 AcerAspireOne kernel: [  634.982031] wlan1: authenticate with 00:0d:0b:d4:ba:3c (try 1)
May 14 07:45:38 AcerAspireOne kernel: [  634.985028] wlan1: authenticated
May 14 07:45:38 AcerAspireOne kernel: [  634.985127] wlan1: associate with 00:0d:0b:d4:ba:3c (try 1)
May 14 07:45:38 AcerAspireOne kernel: [  634.987293] wlan1: RX AssocResp from 00:0d:0b:d4:ba:3c (capab=0x411 status=0 aid=3)
May 14 07:45:38 AcerAspireOne kernel: [  634.987305] wlan1: associated
May 14 07:45:38 AcerAspireOne NetworkManager[469]: <info> (wlan1): supplicant connection state:  associating -> associated
May 14 07:45:38 AcerAspireOne NetworkManager[469]: <info> (wlan1): supplicant connection state:  associated -> completed
May 14 07:45:38 AcerAspireOne NetworkManager[469]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'BrewerNet'.
May 14 07:45:38 AcerAspireOne NetworkManager[469]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) scheduled.
May 14 07:45:38 AcerAspireOne NetworkManager[469]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) started...
May 14 07:45:38 AcerAspireOne NetworkManager[469]: <info> (wlan1): device state change: 5 -> 7 (reason 0)
May 14 07:45:38 AcerAspireOne NetworkManager[469]: <info> Activation (wlan1) Beginning DHCPv4 transaction (timeout in 45 seconds)
May 14 07:45:38 AcerAspireOne NetworkManager[469]: <info> dhclient started with pid 2002
May 14 07:45:38 AcerAspireOne NetworkManager[469]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) complete.
May 14 07:45:38 AcerAspireOne dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
May 14 07:45:38 AcerAspireOne dhclient: Copyright 2004-2010 Internet Systems Consortium.
May 14 07:45:38 AcerAspireOne dhclient: All rights reserved.
May 14 07:45:38 AcerAspireOne dhclient: For info, please visit https://www.isc.org/software/dhcp/
May 14 07:45:38 AcerAspireOne dhclient:
May 14 07:45:38 AcerAspireOne NetworkManager[469]: <info> (wlan1): DHCPv4 state changed nbi -> preinit
May 14 07:45:38 AcerAspireOne dhclient: Listening on LPF/wlan1/00:21:6b:97:c7:68
May 14 07:45:38 AcerAspireOne dhclient: Sending on   LPF/wlan1/00:21:6b:97:c7:68
May 14 07:45:38 AcerAspireOne dhclient: Sending on   Socket/fallback
May 14 07:45:38 AcerAspireOne dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 3
May 14 07:45:41 AcerAspireOne dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 4
May 14 07:45:45 AcerAspireOne dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 9
May 14 07:45:54 AcerAspireOne dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 9
May 14 07:46:03 AcerAspireOne dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 12
May 14 07:46:15 AcerAspireOne dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 17
May 14 07:46:23 AcerAspireOne NetworkManager[469]: <warn> (wlan1): DHCPv4 request timed out.
May 14 07:46:23 AcerAspireOne NetworkManager[469]: <info> (wlan1): canceled DHCP transaction, DHCP client pid 2002
May 14 07:46:23 AcerAspireOne NetworkManager[469]: <info> Activation (wlan1) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
May 14 07:46:23 AcerAspireOne NetworkManager[469]: <info> Activation (wlan1) Stage 4 of 5 (IP4 Configure Timeout) started...
May 14 07:46:23 AcerAspireOne NetworkManager[469]: <warn> Activation (wlan1/wireless): could not get IP configuration for connection 'Auto BrewerNet'.
May 14 07:46:23 AcerAspireOne NetworkManager[469]: <info> (wlan1): device state change: 7 -> 6 (reason 0)
May 14 07:46:23 AcerAspireOne NetworkManager[469]: <info> Activation (wlan1/wireless): asking for new secrets
May 14 07:46:23 AcerAspireOne NetworkManager[469]: <info> Activation (wlan1) Stage 4 of 5 (IP4 Configure Timeout) complete.
May 14 07:46:30 AcerAspireOne NetworkManager[469]: <info> (wlan1): device state change: 6 -> 9 (reason 7)
May 14 07:46:30 AcerAspireOne NetworkManager[469]: <warn> Activation (wlan1) failed for access point (BrewerNet)
May 14 07:46:30 AcerAspireOne NetworkManager[469]: <info> Marking connection 'Auto BrewerNet' invalid.
May 14 07:46:30 AcerAspireOne NetworkManager[469]: <warn> Activation (wlan1) failed.
May 14 07:46:30 AcerAspireOne NetworkManager[469]: <info> (wlan1): device state change: 9 -> 3 (reason 0)
May 14 07:46:30 AcerAspireOne NetworkManager[469]: <info> (wlan1): deactivating device (reason: 0).
May 14 07:46:30 AcerAspireOne kernel: [  687.415174] wlan1: deauthenticating from 00:0d:0b:d4:ba:3c by local choice (reason=3)

```

---

