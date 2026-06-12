---
title: "Wireless roaming"
date: 2009-03-19
forum: Networking &amp; Wireless
---

### Post by maino82 on 2009-03-19
I have a strange issue when roaming on my laptop. APs that I have connected to before come up fine, but if it's the first time I'm connecting, it takes a bunch of times and a bunch of "Disconnected" messages before it works.

Here is part of the /var/log/wpa_supplicant.log file:
```
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:21:43:47:8b:20 (SSID='Caffe Teatro' freq=2462 MHz)
Associated with 00:21:43:47:8b:20
CTRL-EVENT-CONNECTED - Connection to 00:21:43:47:8b:20 completed (reauth) [id=0 id_str=]
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
No network configuration found for the current AP
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:21:43:47:8b:20 (SSID='Caffe Teatro' freq=2462 MHz)
Associated with 00:21:43:47:8b:20
CTRL-EVENT-CONNECTED - Connection to 00:21:43:47:8b:20 completed (reauth) [id=0 id_str=]
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
No network configuration found for the current AP
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:21:43:47:8b:20 (SSID='Caffe Teatro' freq=2462 MHz)
Associated with 00:21:43:47:8b:20
CTRL-EVENT-CONNECTED - Connection to 00:21:43:47:8b:20 completed (reauth) [id=0 id_str=]
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
No network configuration found for the current AP
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:09:5b:6e:c4:58 (SSID='AAPCHO Space' freq=2432 MHz)
CTRL-EVENT-SCAN-RESULTS 
Associated with 00:09:5b:6e:c4:58
CTRL-EVENT-CONNECTED - Connection to 00:09:5b:6e:c4:58 completed (reauth) [id=0 id_str=]
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:18:f8:f4:8f:7f (SSID='EdPioneer' freq=2417 MHz)
CTRL-EVENT-SCAN-RESULTS 
Associated with 00:18:f8:f4:8f:7f
CTRL-EVENT-CONNECTED - Connection to 00:18:f8:f4:8f:7f completed (reauth) [id=0 id_str=]
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Associated with 00:18:f8:f4:8f:7f
CTRL-EVENT-CONNECTED - Connection to 00:18:f8:f4:8f:7f completed (reauth) [id=0 id_str=]
CTRL-EVENT-SCAN-RESULTS 
```


Here is part of the /var/log/syslog file:
```
Mar 19 06:52:08 sheen NetworkManager: <info>  (ath0): device state change: 9 -> 3 
Mar 19 06:52:08 sheen NetworkManager: <info>  (ath0): deactivating device (reason: 0). 
Mar 19 06:52:31 sheen NetworkManager: <info>  Activation (ath0) starting connection 'Auto Caffe Teatro' 
Mar 19 06:52:31 sheen NetworkManager: <info>  (ath0): device state change: 3 -> 4 
Mar 19 06:52:31 sheen NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 19 06:52:31 sheen NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Mar 19 06:52:31 sheen NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Mar 19 06:52:31 sheen NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Mar 19 06:52:31 sheen NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Mar 19 06:52:31 sheen NetworkManager: <info>  (ath0): device state change: 4 -> 5 
Mar 19 06:52:31 sheen NetworkManager: <info>  Activation (ath0/wireless): connection 'Auto Caffe Teatro' requires no security.  No secrets needed. 
Mar 19 06:52:31 sheen NetworkManager: <info>  Config: added 'ssid' value 'Caffe Teatro' 
Mar 19 06:52:31 sheen NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Mar 19 06:52:31 sheen NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Mar 19 06:52:31 sheen NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Mar 19 06:52:31 sheen NetworkManager: <info>  Config: set interface ap_scan to 1 
Mar 19 06:52:31 sheen NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 2 
Mar 19 06:52:33 sheen NetworkManager: <info>  (ath0): supplicant connection state change: 2 -> 3 
Mar 19 06:52:33 sheen NetworkManager: <info>  (ath0): supplicant connection state change: 3 -> 4 
Mar 19 06:52:33 sheen NetworkManager: <info>  (ath0): supplicant connection state change: 4 -> 7 
Mar 19 06:52:33 sheen NetworkManager: <info>  Activation (ath0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Caffe Teatro'. 
Mar 19 06:52:33 sheen NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) scheduled. 
Mar 19 06:52:33 sheen NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) started... 
Mar 19 06:52:33 sheen NetworkManager: <info>  (ath0): device state change: 5 -> 7 
Mar 19 06:52:33 sheen NetworkManager: <info>  Activation (ath0) Beginning DHCP transaction. 
Mar 19 06:52:33 sheen NetworkManager: <info>  dhclient started with pid 8844 
Mar 19 06:52:33 sheen NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) complete. 
Mar 19 06:52:33 sheen dhclient: Internet Systems Consortium DHCP Client V3.1.1
Mar 19 06:52:33 sheen dhclient: Copyright 2004-2008 Internet Systems Consortium.
Mar 19 06:52:33 sheen dhclient: All rights reserved.
Mar 19 06:52:33 sheen dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar 19 06:52:33 sheen dhclient: 
Mar 19 06:52:33 sheen dhclient: wifi0: unknown hardware address type 801
Mar 19 06:52:33 sheen NetworkManager: <info>  DHCP: device ath0 state changed normal exit -> preinit 
Mar 19 06:52:33 sheen dhclient: wifi0: unknown hardware address type 801
Mar 19 06:52:33 sheen dhclient: Listening on LPF/ath0/00:19:7d:4d:75:b3
Mar 19 06:52:33 sheen dhclient: Sending on   LPF/ath0/00:19:7d:4d:75:b3
Mar 19 06:52:33 sheen dhclient: Sending on   Socket/fallback
Mar 19 06:52:35 sheen dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
Mar 19 06:52:39 sheen dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
Mar 19 06:52:47 sheen dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
Mar 19 06:53:02 sheen dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
Mar 19 06:53:15 sheen dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 21
Mar 19 06:53:18 sheen NetworkManager: <info>  Device 'ath0' DHCP transaction took too long (>45s), stopping it. 
Mar 19 06:53:18 sheen NetworkManager: <info>  ath0: canceled DHCP transaction, dhcp client pid 8844 
Mar 19 06:53:18 sheen NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Mar 19 06:53:18 sheen NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Timeout) started... 
Mar 19 06:53:18 sheen NetworkManager: <info>  (ath0): device state change: 7 -> 9 
Mar 19 06:53:18 sheen NetworkManager: <info>  Activation (ath0) failed for access point (Caffe Teatro) 
Mar 19 06:53:18 sheen NetworkManager: <info>  Marking connection 'Auto Caffe Teatro' invalid. 
Mar 19 06:53:18 sheen NetworkManager: <info>  Activation (ath0) failed. 
Mar 19 06:53:18 sheen NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Timeout) complete. 
Mar 19 06:53:18 sheen NetworkManager: <info>  (ath0): device state change: 9 -> 3 
Mar 19 06:53:18 sheen NetworkManager: <info>  (ath0): deactivating device (reason: 0). 
Mar 19 06:53:31 sheen NetworkManager: <info>  Activation (ath0) starting connection 'Auto AAPCHO Space' 
Mar 19 06:53:31 sheen NetworkManager: <info>  (ath0): device state change: 3 -> 4 
Mar 19 06:53:31 sheen NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 19 06:53:31 sheen NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Mar 19 06:53:31 sheen NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Mar 19 06:53:31 sheen NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Mar 19 06:53:31 sheen NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Mar 19 06:53:31 sheen NetworkManager: <info>  (ath0): device state change: 4 -> 5 
Mar 19 06:53:31 sheen NetworkManager: <info>  Activation (ath0/wireless): connection 'Auto AAPCHO Space' requires no security.  No secrets needed. 
Mar 19 06:53:31 sheen NetworkManager: <info>  Config: added 'ssid' value 'AAPCHO Space' 
Mar 19 06:53:31 sheen NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Mar 19 06:53:31 sheen NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Mar 19 06:53:31 sheen NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Mar 19 06:53:31 sheen NetworkManager: <info>  Config: set interface ap_scan to 1 
Mar 19 06:53:31 sheen NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 2 
Mar 19 06:53:33 sheen NetworkManager: <info>  (ath0): supplicant connection state change: 2 -> 3 
Mar 19 06:53:34 sheen NetworkManager: <info>  (ath0): supplicant connection state change: 3 -> 4 
Mar 19 06:53:34 sheen NetworkManager: <info>  (ath0): supplicant connection state change: 4 -> 7 
Mar 19 06:53:34 sheen NetworkManager: <info>  Activation (ath0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'AAPCHO Space'. 
Mar 19 06:53:34 sheen NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) scheduled. 
Mar 19 06:53:34 sheen NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) started... 
Mar 19 06:53:34 sheen NetworkManager: <info>  (ath0): device state change: 5 -> 7 
Mar 19 06:53:34 sheen NetworkManager: <info>  Activation (ath0) Beginning DHCP transaction. 
Mar 19 06:53:34 sheen NetworkManager: <info>  dhclient started with pid 8859 
Mar 19 06:53:34 sheen NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) complete. 
Mar 19 06:53:34 sheen dhclient: Internet Systems Consortium DHCP Client V3.1.1
Mar 19 06:53:34 sheen dhclient: Copyright 2004-2008 Internet Systems Consortium.
Mar 19 06:53:34 sheen dhclient: All rights reserved.
Mar 19 06:53:34 sheen dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar 19 06:53:34 sheen dhclient: 
Mar 19 06:53:34 sheen dhclient: wifi0: unknown hardware address type 801
Mar 19 06:53:34 sheen dhclient: wifi0: unknown hardware address type 801
Mar 19 06:53:34 sheen NetworkManager: <info>  DHCP: device ath0 state changed normal exit -> preinit 
Mar 19 06:53:34 sheen dhclient: Listening on LPF/ath0/00:19:7d:4d:75:b3
Mar 19 06:53:34 sheen dhclient: Sending on   LPF/ath0/00:19:7d:4d:75:b3
Mar 19 06:53:34 sheen dhclient: Sending on   Socket/fallback
Mar 19 06:53:35 sheen dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
Mar 19 06:53:39 sheen dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
Mar 19 06:53:43 sheen dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
Mar 19 06:53:50 sheen dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
Mar 19 06:54:04 sheen dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
Mar 19 06:54:19 sheen dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
Mar 19 06:54:19 sheen NetworkManager: <info>  Device 'ath0' DHCP transaction took too long (>45s), stopping it. 
Mar 19 06:54:20 sheen NetworkManager: <info>  ath0: canceled DHCP transaction, dhcp client pid 8859 
Mar 19 06:54:20 sheen NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Mar 19 06:54:20 sheen NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Timeout) started... 
Mar 19 06:54:20 sheen NetworkManager: <info>  (ath0): device state change: 7 -> 9 
Mar 19 06:54:20 sheen NetworkManager: <info>  Activation (ath0) failed for access point (AAPCHO Space) 
Mar 19 06:54:20 sheen NetworkManager: <info>  Marking connection 'Auto AAPCHO Space' invalid. 
Mar 19 06:54:20 sheen NetworkManager: <info>  Activation (ath0) failed. 
Mar 19 06:54:20 sheen NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Timeout) complete. 
Mar 19 06:54:20 sheen NetworkManager: <info>  (ath0): device state change: 9 -> 3 
Mar 19 06:54:20 sheen NetworkManager: <info>  (ath0): deactivating device (reason: 0). 
Mar 19 06:54:31 sheen NetworkManager: <info>  Activation (ath0) starting connection 'Auto EdPioneer' 
Mar 19 06:54:31 sheen NetworkManager: <info>  (ath0): device state change: 3 -> 4 
Mar 19 06:54:31 sheen NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 19 06:54:31 sheen NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Mar 19 06:54:31 sheen NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Mar 19 06:54:31 sheen NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Mar 19 06:54:31 sheen NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Mar 19 06:54:31 sheen NetworkManager: <info>  (ath0): device state change: 4 -> 5 
Mar 19 06:54:31 sheen NetworkManager: <info>  Activation (ath0/wireless): connection 'Auto EdPioneer' requires no security.  No secrets needed. 
Mar 19 06:54:31 sheen NetworkManager: <info>  Config: added 'ssid' value 'EdPioneer' 
Mar 19 06:54:31 sheen NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Mar 19 06:54:31 sheen NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Mar 19 06:54:31 sheen NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Mar 19 06:54:31 sheen NetworkManager: <info>  Config: set interface ap_scan to 1 
Mar 19 06:54:31 sheen NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 2 
Mar 19 06:54:33 sheen NetworkManager: <info>  (ath0): supplicant connection state change: 2 -> 3 
Mar 19 06:54:34 sheen NetworkManager: <info>  (ath0): supplicant connection state change: 3 -> 4 
Mar 19 06:54:34 sheen NetworkManager: <info>  (ath0): supplicant connection state change: 4 -> 7 
Mar 19 06:54:34 sheen NetworkManager: <info>  Activation (ath0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'EdPioneer'. 
Mar 19 06:54:34 sheen NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) scheduled. 
Mar 19 06:54:34 sheen NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) started... 
Mar 19 06:54:34 sheen NetworkManager: <info>  (ath0): device state change: 5 -> 7 
Mar 19 06:54:34 sheen NetworkManager: <info>  Activation (ath0) Beginning DHCP transaction. 
Mar 19 06:54:34 sheen dhclient: Internet Systems Consortium DHCP Client V3.1.1
Mar 19 06:54:34 sheen dhclient: Copyright 2004-2008 Internet Systems Consortium.
Mar 19 06:54:34 sheen dhclient: All rights reserved.
Mar 19 06:54:34 sheen dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar 19 06:54:34 sheen dhclient: 
Mar 19 06:54:34 sheen dhclient: wifi0: unknown hardware address type 801
Mar 19 06:54:34 sheen NetworkManager: <info>  dhclient started with pid 8873 
Mar 19 06:54:34 sheen NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) complete. 
Mar 19 06:54:34 sheen NetworkManager: <info>  DHCP: device ath0 state changed normal exit -> preinit 
Mar 19 06:54:34 sheen dhclient: wifi0: unknown hardware address type 801
Mar 19 06:54:34 sheen dhclient: Listening on LPF/ath0/00:19:7d:4d:75:b3
Mar 19 06:54:34 sheen dhclient: Sending on   LPF/ath0/00:19:7d:4d:75:b3
Mar 19 06:54:34 sheen dhclient: Sending on   Socket/fallback
Mar 19 06:54:34 sheen dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
Mar 19 06:54:35 sheen dhclient: DHCPOFFER of 10.24.11.115 from 10.24.11.1
Mar 19 06:54:35 sheen dhclient: DHCPREQUEST of 10.24.11.115 on ath0 to 255.255.255.255 port 67
Mar 19 06:54:35 sheen dhclient: DHCPACK of 10.24.11.115 from 10.24.11.1
Mar 19 06:54:35 sheen NetworkManager: <info>  DHCP: device ath0 state changed preinit -> bound 
Mar 19 06:54:35 sheen NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Get) scheduled... 
Mar 19 06:54:35 sheen NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Get) started... 
Mar 19 06:54:35 sheen NetworkManager: <info>    address 10.24.11.115 
Mar 19 06:54:35 sheen NetworkManager: <info>    prefix 24 (255.255.255.0) 
Mar 19 06:54:35 sheen NetworkManager: <info>    gateway 10.24.11.1 
Mar 19 06:54:35 sheen NetworkManager: <info>    hostname 'sheen' 
Mar 19 06:54:35 sheen NetworkManager: <info>    nameserver '129.250.35.250' 
Mar 19 06:54:35 sheen NetworkManager: <info>    nameserver '129.250.35.251' 
Mar 19 06:54:35 sheen NetworkManager: <info>  Activation (ath0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Mar 19 06:54:35 sheen dhclient: bound to 10.24.11.115 -- renewal in 33492 seconds.
Mar 19 06:54:35 sheen NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Get) complete. 
Mar 19 06:54:35 sheen NetworkManager: <info>  Activation (ath0) Stage 5 of 5 (IP Configure Commit) started... 
Mar 19 06:54:35 sheen avahi-daemon[4983]: Joining mDNS multicast group on interface ath0.IPv4 with address 10.24.11.115.
Mar 19 06:54:35 sheen avahi-daemon[4983]: New relevant interface ath0.IPv4 for mDNS.
Mar 19 06:54:35 sheen avahi-daemon[4983]: Registering new address record for 10.24.11.115 on ath0.IPv4.
Mar 19 06:54:36 sheen NetworkManager: <info>  (ath0): device state change: 7 -> 8 
Mar 19 06:54:36 sheen NetworkManager: <info>  Policy set 'Auto EdPioneer' (ath0) as default for routing and DNS. 
Mar 19 06:54:36 sheen NetworkManager: <info>  Activation (ath0) successful, device activated. 
Mar 19 06:54:36 sheen NetworkManager: <info>  Activation (ath0) Stage 5 of 5 (IP Configure Commit) complete.
```

Above you can see that I'm trying to connect to two access points ("Cafe Teatro" and "AAPCHO Space"), which fail. But then when I try EdPioneer it works fine. None of them are password protected.

Here is the output of lshw:

```
           *-network:1
                description: Wireless interface
                product: AR2413 802.11bg NIC
                vendor: Atheros Communications Inc.
                physical id: 2
                bus info: pci@0000:06:02.0
                logical name: wifi0
                version: 01
                serial: 00:19:7d:4d:75:b3
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci ip=10.24.11.115 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
```

It's not a huge problem since eventually I can get connected, but it just doesn't seem to be logical as to why it won't work for new APs. Any help or guidance is appreciated.

Thanks,
Dave

---

### Post by maino82 on 2009-03-30
OK, so I've noticed that APs with spaces in the name tend to cause problems (though not always). Could this be the culprit? Has anyone else experienced this?

---

