---
title: "GNOME Network Manager doesn't see wireless network"
date: 2009-07-11
forum: Networking &amp; Wireless
---

### Post by ricky22 on 2009-07-11
Hi,

I had a problem with my broadband for the last two weeks (Tiscali is officially the worst ISP ever, absolutely appalling). Now it's back on, I reconfigured the router, but the Network Manager doesn't see my wireless network at all. When I try to connect manually to a hidden network, it prompts for the password but then nothing happens. I tried to switch from WPA to WEP, then to turn the security off completely, no joy. Other devices see the network and connect OK. Here's the log:

Jul 11 19:50:42 P NetworkManager: <info>  Activation (eth1) starting connection 'Auto United We Stand' 
Jul 11 19:50:42 P NetworkManager: <info>  (eth1): device state change: 3 -> 4 
Jul 11 19:50:42 P NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jul 11 19:50:42 P NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jul 11 19:50:42 P NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jul 11 19:50:42 P NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jul 11 19:50:42 P NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jul 11 19:50:43 P NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Jul 11 19:50:43 P NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto United We Stand' has security, and secrets exist.  No new secrets needed. 
Jul 11 19:50:43 P NetworkManager: <info>  Config: added 'ssid' value 'United We Stand' 
Jul 11 19:50:43 P NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Jul 11 19:50:43 P NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Jul 11 19:50:43 P NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Jul 11 19:50:43 P NetworkManager: <info>  Config: added 'proto' value 'WPA RSN' 
Jul 11 19:50:43 P NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP' 
Jul 11 19:50:43 P NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP' 
Jul 11 19:50:43 P NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jul 11 19:50:43 P NetworkManager: <info>  Config: set interface ap_scan to 2 
Jul 11 19:50:43 P NetworkManager: <info>  (eth1): supplicant connection state change: 1 -> 2 
Jul 11 19:50:43 P NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 3 
Jul 11 19:51:43 P NetworkManager: <info>  Activation (eth1/wireless): association took too long. 
Jul 11 19:51:43 P NetworkManager: <info>  (eth1): device state change: 5 -> 6 
Jul 11 19:51:43 P NetworkManager: <info>  Activation (eth1/wireless): asking for new secrets 
Jul 11 19:51:43 P NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 0 
Jul 11 19:51:50 P NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jul 11 19:51:50 P NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jul 11 19:51:50 P NetworkManager: <info>  (eth1): device state change: 6 -> 4 
Jul 11 19:51:50 P NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jul 11 19:51:50 P NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jul 11 19:51:50 P NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jul 11 19:51:50 P NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Jul 11 19:51:50 P NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto United We Stand' has security, and secrets exist.  No new secrets needed. 
Jul 11 19:51:50 P NetworkManager: <info>  Config: added 'ssid' value 'United We Stand' 
Jul 11 19:51:50 P NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Jul 11 19:51:50 P NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Jul 11 19:51:50 P NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Jul 11 19:51:50 P NetworkManager: <info>  Config: added 'proto' value 'WPA RSN' 
Jul 11 19:51:50 P NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP' 
Jul 11 19:51:50 P NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP' 
Jul 11 19:51:50 P NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jul 11 19:51:50 P NetworkManager: <info>  Config: set interface ap_scan to 2 
Jul 11 19:51:50 P NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Jul 11 19:51:50 P NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 3 
Jul 11 19:52:50 P NetworkManager: <info>  Activation (eth1/wireless): association took too long. 
Jul 11 19:52:50 P NetworkManager: <info>  (eth1): device state change: 5 -> 6 
Jul 11 19:52:50 P NetworkManager: <info>  Activation (eth1/wireless): asking for new secrets 
Jul 11 19:52:50 P NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 0 
Jul 11 19:52:56 P NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jul 11 19:52:56 P NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jul 11 19:52:56 P NetworkManager: <info>  (eth1): device state change: 6 -> 4 
Jul 11 19:52:56 P NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jul 11 19:52:56 P NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jul 11 19:52:56 P NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jul 11 19:52:56 P NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Jul 11 19:52:56 P NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto United We Stand' has security, and secrets exist.  No new secrets needed. 
Jul 11 19:52:56 P NetworkManager: <info>  Config: added 'ssid' value 'United We Stand' 
Jul 11 19:52:56 P NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Jul 11 19:52:56 P NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Jul 11 19:52:56 P NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Jul 11 19:52:56 P NetworkManager: <info>  Config: added 'proto' value 'WPA RSN' 
Jul 11 19:52:56 P NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP' 
Jul 11 19:52:56 P NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP' 
Jul 11 19:52:56 P NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jul 11 19:52:56 P NetworkManager: <info>  Config: set interface ap_scan to 2 
Jul 11 19:52:56 P NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Jul 11 19:52:56 P NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 3 
Jul 11 19:53:56 P NetworkManager: <info>  Activation (eth1/wireless): association took too long. 
Jul 11 19:53:56 P NetworkManager: <info>  (eth1): device state change: 5 -> 9 
Jul 11 19:53:56 P NetworkManager: <info>  Activation (eth1) failed for access point (United We Stand) 
Jul 11 19:53:56 P NetworkManager: <info>  Marking connection 'Auto United We Stand' invalid. 
Jul 11 19:53:56 P NetworkManager: <info>  Activation (eth1) failed. 
Jul 11 19:53:56 P NetworkManager: <info>  (eth1): device state change: 9 -> 3 
Jul 11 19:53:56 P NetworkManager: <info>  (eth1): deactivating device (reason: 0). 
Jul 11 19:53:56 P NetworkManager: <WARN>  nm_device_wifi_disable_encryption(): error setting key for device eth1: Invalid argument 

I have a built-in Broadcom wireless device, with proprietary driver provided by Ubuntu. It has worked OK so far, with only minor issues.

Any help on this would be much appreciated! 

Thanks,

Patrick

---

### Post by ricky22 on 2009-07-12
Update: WiFi Radar doesn't see the access point either, even though I am able to connect to it and use Internet from a Mac laptop and Symbian mobile phone.

This is the lshw output: 

 *-network
                description: Wireless interface
                product: BCM4311 802.11b/g WLAN
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:10:00.0
                logical name: eth1
                version: 02
                serial: 00:1a:73:9b:40:c4
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl1 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg

---

### Post by superprash2003 on 2009-07-12
post output of **sudo iwlist scanning**

---

### Post by ricky22 on 2009-07-12
Hey,

It miraculously started working again, and **sudo iwlist scanning** shows: 

Cell 02 - Address: 00:21:04:14:BE:89
                    ESSID:"United We Stand"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-57 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

I'll try that if it happens again, and get back. 

Thanks!

Patrick

---

