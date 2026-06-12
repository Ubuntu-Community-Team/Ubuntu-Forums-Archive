---
title: "What else can I check ?  2different  T400 laptops , Z61 wont work wireless NetGear"
date: 2010-03-13
forum: Networking &amp; Wireless
---

### Post by hbarile on 2010-03-13
Looking for any other ideas before I send router back or quit ubuntu .. 

Ive installed ubuntu on 3 different laptops . 2 T400's and 1 Z61T . I can use these laptops on  other wireless networks fine with no problems, however at my home where I have a Netgear wpn 824v3 router with latest firmware my ubunto laptops  will not connect 95% of the time . occasionally it does through a combintation of rebooting router/restarting/reloading network.  I can connect to my home wirless network fine with all windows laptops but not with ubuntu 9.1.0 .Ive tried three different installs of ubutu on three different laptops . All exhibut same behavior.

Ive disabled Security for my network , and left it OPEN. I can see available networks through network manager , dirvers are loaded, all seems good
 
Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 00
       serial: 00:26:c6:82:07:22
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:31 memory:f4200000-f4201fff

For some reason dhclient cannot get an ip from the  router  for the wirless connection  ( no problems using eth0 or hardwire. I can see that resolv.conf never gets updated when I attempt connection to WLAN0, but does wi ) 

Any ideas on what else with regards to this reouter/ubutu I can look into given that I can go to other access points and connect , but not at home ( even thought all windows laptops can connect wirelessly fine) 


Mar 14 14:04:08 hbarile-laplnx NetworkManager: <info>  Activation (wlan0) starting connection 'Auto few'
Mar 14 14:04:08 hbarile-laplnx NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Mar 14 14:04:08 hbarile-laplnx NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 14 14:04:08 hbarile-laplnx NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 14 14:04:08 hbarile-laplnx NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 14 14:04:08 hbarile-laplnx NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 14 14:04:08 hbarile-laplnx NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 14 14:04:08 hbarile-laplnx NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Mar 14 14:04:08 hbarile-laplnx NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto few' requires no security.  No secrets needed.
Mar 14 14:04:08 hbarile-laplnx NetworkManager: <info>  Config: added 'ssid' value 'few'
Mar 14 14:04:08 hbarile-laplnx NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Mar 14 14:04:08 hbarile-laplnx NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Mar 14 14:04:08 hbarile-laplnx NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 14 14:04:08 hbarile-laplnx NetworkManager: <info>  Config: set interface ap_scan to 1
Mar 14 14:04:08 hbarile-laplnx NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Mar 14 14:04:08 hbarile-laplnx NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Mar 14 14:04:11 hbarile-laplnx wpa_supplicant[1408]: CTRL-EVENT-SCAN-RESULTS 
Mar 14 14:04:11 hbarile-laplnx wpa_supplicant[1408]: Trying to associate with 00:1e:2a:dc:50:26 (SSID='few' freq=2437 MHz)
Mar 14 14:04:11 hbarile-laplnx wpa_supplicant[1408]: Association request to the driver failed
Mar 14 14:04:11 hbarile-laplnx NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Mar 14 14:04:11 hbarile-laplnx kernel: [ 4356.295223] wlan0: authenticate with AP 00:1e:2a:dc:50:26
Mar 14 14:04:11 hbarile-laplnx kernel: [ 4356.297870] wlan0: authenticated
Mar 14 14:04:11 hbarile-laplnx kernel: [ 4356.297878] wlan0: associate with AP 00:1e:2a:dc:50:26
Mar 14 14:04:11 hbarile-laplnx wpa_supplicant[1408]: Associated with 00:1e:2a:dc:50:26
Mar 14 14:04:11 hbarile-laplnx wpa_supplicant[1408]: CTRL-EVENT-CONNECTED - Connection to 00:1e:2a:dc:50:26 completed (reauth) [id=0 id_str=]
Mar 14 14:04:11 hbarile-laplnx kernel: [ 4356.302049] wlan0: RX AssocResp from 00:1e:2a:dc:50:26 (capab=0x421 status=0 aid=1)
Mar 14 14:04:11 hbarile-laplnx kernel: [ 4356.302057] wlan0: associated
Mar 14 14:04:11 hbarile-laplnx NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Mar 14 14:04:11 hbarile-laplnx NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed
Mar 14 14:04:11 hbarile-laplnx NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'few'.
Mar 14 14:04:11 hbarile-laplnx NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 14 14:04:11 hbarile-laplnx NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Mar 14 14:04:11 hbarile-laplnx NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Mar 14 14:04:11 hbarile-laplnx NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Mar 14 14:04:11 hbarile-laplnx dhclient: Internet Systems Consortium DHCP Client V3.1.2
Mar 14 14:04:11 hbarile-laplnx dhclient: Copyright 2004-2008 Internet Systems Consortium.
Mar 14 14:04:11 hbarile-laplnx dhclient: All rights reserved.
Mar 14 14:04:11 hbarile-laplnx dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Mar 14 14:04:11 hbarile-laplnx dhclient: 
Mar 14 14:04:11 hbarile-laplnx NetworkManager: <info>  dhclient started with pid 2786
Mar 14 14:04:11 hbarile-laplnx NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Mar 14 14:04:11 hbarile-laplnx NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Mar 14 14:04:11 hbarile-laplnx NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Mar 14 14:04:11 hbarile-laplnx NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Mar 14 14:04:11 hbarile-laplnx NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Mar 14 14:04:11 hbarile-laplnx dhclient: Listening on LPF/wlan0/00:26:c6:82:07:22
Mar 14 14:04:11 hbarile-laplnx dhclient: Sending on   LPF/wlan0/00:26:c6:82:07:22
Mar 14 14:04:11 hbarile-laplnx dhclient: Sending on   Socket/fallback
Mar 14 14:04:11 hbarile-laplnx dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Mar 14 14:04:14 hbarile-laplnx dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Mar 14 14:04:21 hbarile-laplnx dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Mar 14 14:04:33 hbarile-laplnx dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Mar 14 14:04:43 hbarile-laplnx dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Mar 14 14:04:50 hbarile-laplnx dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Mar 14 14:04:57 hbarile-laplnx NetworkManager: <info>  (wlan0): DHCP transaction took too long, stopping it.
Mar 14 14:04:57 hbarile-laplnx NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 2786
Mar 14 14:04:57 hbarile-laplnx NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Mar 14 14:04:57 hbarile-laplnx NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Mar 14 14:04:57 hbarile-laplnx NetworkManager: <info>  (wlan0): device state change: 7 -> 9 (reason 5)
Mar 14 14:04:57 hbarile-laplnx NetworkManager: <info>  Activation (wlan0) failed for access point (few)
Mar 14 14:04:57 hbarile-laplnx NetworkManager: <info>  Marking connection 'Auto few' invalid.
Mar 14 14:04:57 hbarile-laplnx NetworkManager: <info>  Activation (wlan0) failed.
Mar 14 14:04:57 hbarile-laplnx NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Mar 14 14:04:57 hbarile-laplnx NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Mar 14 14:04:57 hbarile-laplnx NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Mar 14 14:04:57 hbarile-laplnx kernel: [ 4401.926839] wlan0: disassociating by local choice (reason=3)
Mar 14 14:04:57 hbarile-laplnx wpa_supplicant[1408]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys

sudo iwconfig wlan0 essid few
hbarile@hbarile-laplnx:/etc/wpa_supplicant$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 2575
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:26:c6:82:07:22
Sending on   LPF/wlan0/00:26:c6:82:07:22
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
resolvconf: Error: /etc/resolv.conf must be a symlink
hbarile@hbarile-laplnx:/etc/wpa_supplicant$

---

