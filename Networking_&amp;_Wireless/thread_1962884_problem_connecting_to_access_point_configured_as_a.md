---
title: "problem connecting to access point configured as a repeater"
date: 2012-04-21
forum: Networking &amp; Wireless
---

### Post by alshaimaa on 2012-04-21
[B][SIZE=2]I  configured access point to work as a universal repeater, I can connect to it under  windows, but under Linux I can find the SSID but cannot connect, however  before configuring it as a repeater I could connect under Linux to both the access point and the router.
I'm using Ubuntu 10.10
[/SIZE][/B]

[SIZE=2]By [/SIZE]viewing the sys log and trying to connect I got the following:

Apr 20 23:11:21 alshaimaa-Inspiron-1464 kernel: [29959.036711] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded Apr 20 23:11:22 alshaimaa-Inspiron-1464 NetworkManager[967]: <info> Activation (eth1) starting connection 'Auto TE-Data'
 Apr 20 23:11:22 alshaimaa-Inspiron-1464 NetworkManager[967]: <info> (eth1): device state change: 3 -> 4 (reason 0)
 Apr 20 23:11:22 alshaimaa-Inspiron-1464 NetworkManager[967]:  <info> Activation (eth1) Stage 1 of 5 (Device Prepare)  scheduled...
 Apr 20 23:11:22 alshaimaa-Inspiron-1464 NetworkManager[967]:  <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
 Apr 20 23:11:22 alshaimaa-Inspiron-1464 NetworkManager[967]:  <info> Activation (eth1) Stage 2 of 5 (Device Configure)  scheduled...
 Apr 20 23:11:22 alshaimaa-Inspiron-1464 NetworkManager[967]:  <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
 Apr 20 23:11:22 alshaimaa-Inspiron-1464 NetworkManager[967]:  <info> Activation (eth1) Stage 2 of 5 (Device Configure)  starting...
 Apr 20 23:11:22 alshaimaa-Inspiron-1464 NetworkManager[967]: <info> (eth1): device state change: 4 -> 5 (reason 0)
 Apr 20 23:11:22 alshaimaa-Inspiron-1464 NetworkManager[967]:  <info> Activation (eth1/wireless): connection 'Auto TE-Data'  requires no security.  No secrets needed.
 Apr 20 23:11:22 alshaimaa-Inspiron-1464 NetworkManager[967]: <info> Config: added 'ssid' value 'TE-Data'
 Apr 20 23:11:22 alshaimaa-Inspiron-1464 NetworkManager[967]: <info> Config: added 'scan_ssid' value '1'
 Apr 20 23:11:22 alshaimaa-Inspiron-1464 NetworkManager[967]: <info> Config: added 'key_mgmt' value 'NONE'
 Apr 20 23:11:22 alshaimaa-Inspiron-1464 NetworkManager[967]:  <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
 Apr 20 23:11:22 alshaimaa-Inspiron-1464 NetworkManager[967]: <info> Config: set interface ap_scan to 1
 Apr 20 23:11:22 alshaimaa-Inspiron-1464 NetworkManager[967]:  <info> (eth1): supplicant connection state:  disconnected ->  scanning
 Apr 20 23:11:26 alshaimaa-Inspiron-1464 kernel: [29964.032648] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
 Apr 20 23:11:27 alshaimaa-Inspiron-1464 wpa_supplicant[1077]: Trying  to associate with 54:e6:fc:b9:d9:68 (SSID='TE-Data' freq=2412 MHz)
 Apr 20 23:11:27 alshaimaa-Inspiron-1464 wpa_supplicant[1077]: Association request to the driver failed
 Apr 20 23:11:27 alshaimaa-Inspiron-1464 NetworkManager[967]:  <info> (eth1): supplicant connection state:  scanning ->  associating
 Apr 20 23:11:31 alshaimaa-Inspiron-1464 kernel: [29969.041059] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
 Apr 20 23:11:32 alshaimaa-Inspiron-1464 wpa_supplicant[1077]: Authentication with 54:e6:fc:b9:d9:68 timed out.
 Apr 20 23:11:32 alshaimaa-Inspiron-1464 wpa_supplicant[1077]: Associated with 54:e6:fc:b9:d9:68
 Apr 20 23:11:32 alshaimaa-Inspiron-1464 wpa_supplicant[1077]:  CTRL-EVENT-CONNECTED - Connection to 54:e6:fc:b9:d9:68 completed  (reauth) [id=0 id_str=]
 Apr 20 23:11:32 alshaimaa-Inspiron-1464 NetworkManager[967]:  <info> (eth1): supplicant connection state:  associating ->  disconnected
 Apr 20 23:11:32 alshaimaa-Inspiron-1464 NetworkManager[967]:  <info> (eth1): supplicant connection state:  disconnected ->  scanning
 Apr 20 23:11:32 alshaimaa-Inspiron-1464 NetworkManager[967]:  <info> (eth1): supplicant connection state:  scanning ->  associated
 Apr 20 23:11:32 alshaimaa-Inspiron-1464 NetworkManager[967]:  <info> (eth1): supplicant connection state:  associated ->  completed
 Apr 20 23:11:32 alshaimaa-Inspiron-1464 NetworkManager[967]:  <info> Activation (eth1/wireless) Stage 2 of 5 (Device Configure)  successful.  Connected to wireless network 'TE-Data'.
 Apr 20 23:11:32 alshaimaa-Inspiron-1464 NetworkManager[967]:  <info> Activation (eth1) Stage 3 of 5 (IP Configure Start)  scheduled.
 Apr 20 23:11:32 alshaimaa-Inspiron-1464 NetworkManager[967]:  <info> Activation (eth1) Stage 3 of 5 (IP Configure Start)  started...
 Apr 20 23:11:32 alshaimaa-Inspiron-1464 NetworkManager[967]: <info> (eth1): device state change: 5 -> 7 (reason 0)
 Apr 20 23:11:32 alshaimaa-Inspiron-1464 NetworkManager[967]:  <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in  45 seconds)
 Apr 20 23:11:32 alshaimaa-Inspiron-1464 NetworkManager[967]: <info> dhclient started with pid 21200
 Apr 20 23:11:32 alshaimaa-Inspiron-1464 NetworkManager[967]:  <info> Activation (eth1) Stage 3 of 5 (IP Configure Start)  complete.
 Apr 20 23:11:32 alshaimaa-Inspiron-1464 dhclient: Internet Systems Consortium DHCP Client V3.1.3
 Apr 20 23:11:32 alshaimaa-Inspiron-1464 dhclient: Copyright 2004-2009 Internet Systems Consortium.
 Apr 20 23:11:32 alshaimaa-Inspiron-1464 dhclient: All rights reserved.
 Apr 20 23:11:32 alshaimaa-Inspiron-1464 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
 Apr 20 23:11:32 alshaimaa-Inspiron-1464 dhclient:
 Apr 20 23:11:32 alshaimaa-Inspiron-1464 NetworkManager[967]: <info> (eth1): DHCPv4 state changed nbi -> preinit
 Apr 20 23:11:32 alshaimaa-Inspiron-1464 dhclient: Listening on LPF/eth1/f0:7b:cb:43:07:f6
 Apr 20 23:11:32 alshaimaa-Inspiron-1464 dhclient: Sending on   LPF/eth1/f0:7b:cb:43:07:f6
 Apr 20 23:11:32 alshaimaa-Inspiron-1464 dhclient: Sending on   Socket/fallback
 Apr 20 23:11:32 alshaimaa-Inspiron-1464 dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
 Apr 20 23:11:35 alshaimaa-Inspiron-1464 dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
 Apr 20 23:11:36 alshaimaa-Inspiron-1464 kernel: [29974.038203] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
 Apr 20 23:11:39 alshaimaa-Inspiron-1464 dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
 Apr 20 23:11:41 alshaimaa-Inspiron-1464 kernel: [29979.035313] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
 Apr 20 23:11:45 alshaimaa-Inspiron-1464 dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
 Apr 20 23:11:46 alshaimaa-Inspiron-1464 kernel: [29984.033395] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
 Apr 20 23:11:51 alshaimaa-Inspiron-1464 kernel: [29989.029613] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
 Apr 20 23:11:52 alshaimaa-Inspiron-1464 dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
 Apr 20 23:11:56 alshaimaa-Inspiron-1464 kernel: [29994.029293] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
 Apr 20 23:12:01 alshaimaa-Inspiron-1464 kernel: [29999.022740] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
 Apr 20 23:12:04 alshaimaa-Inspiron-1464 dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
 Apr 20 23:12:06 alshaimaa-Inspiron-1464 kernel: [30004.020990] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
 Apr 20 23:12:11 alshaimaa-Inspiron-1464 kernel: [30009.019057] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
 Apr 20 23:12:15 alshaimaa-Inspiron-1464 dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
 Apr 20 23:12:16 alshaimaa-Inspiron-1464 kernel: [30014.015414] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
 Apr 20 23:12:18 alshaimaa-Inspiron-1464 NetworkManager[967]: <warn> (eth1): DHCPv4 request timed out.
 Apr 20 23:12:18 alshaimaa-Inspiron-1464 NetworkManager[967]:  <info> (eth1): canceled DHCP transaction, DHCP client pid 21200
 Apr 20 23:12:18 alshaimaa-Inspiron-1464 NetworkManager[967]:  <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout)  scheduled...
 Apr 20 23:12:18 alshaimaa-Inspiron-1464 NetworkManager[967]:  <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout)  started...
 Apr 20 23:12:18 alshaimaa-Inspiron-1464 NetworkManager[967]:  <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit)  scheduled...
 Apr 20 23:12:18 alshaimaa-Inspiron-1464 NetworkManager[967]:  <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout)  complete.
 Apr 20 23:12:18 alshaimaa-Inspiron-1464 NetworkManager[967]:  <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit)  started...
 Apr 20 23:12:18 alshaimaa-Inspiron-1464 NetworkManager[967]:  <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) failed  (no IP configuration found)
 Apr 20 23:12:18 alshaimaa-Inspiron-1464 NetworkManager[967]: <info> (eth1): device state change: 7 -> 9 (reason 5)
 Apr 20 23:12:18 alshaimaa-Inspiron-1464 NetworkManager[967]: <warn> Activation (eth1) failed for access point (TE-Data)
 Apr 20 23:12:18 alshaimaa-Inspiron-1464 NetworkManager[967]: <info> Marking connection 'Auto TE-Data' invalid.
 Apr 20 23:12:18 alshaimaa-Inspiron-1464 NetworkManager[967]: <warn> Activation (eth1) failed.
 Apr 20 23:12:18 alshaimaa-Inspiron-1464 NetworkManager[967]:  <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit)  complete.
 Apr 20 23:12:18 alshaimaa-Inspiron-1464 NetworkManager[967]: <info> (eth1): device state change: 9 -> 3 (reason 0)
 Apr 20 23:12:18 alshaimaa-Inspiron-1464 NetworkManager[967]: <info> (eth1): deactivating device (reason: 0).
 Apr 20 23:12:18 alshaimaa-Inspiron-1464 NetworkManager[967]:  <info> Policy set 'Etisalat Default 1' (ppp0) as default for IPv4  routing and DNS.
 Apr 20 23:12:18 alshaimaa-Inspiron-1464 NetworkManager[967]:  <info> Policy set 'Etisalat Default 1' (ppp0) as default for IPv4  routing and DNS.
 Apr 20 23:12:18 alshaimaa-Inspiron-1464 wpa_supplicant[1077]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
 Apr 20 23:12:21 alshaimaa-Inspiron-1464 kernel: [30019.011341] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded

---

