---
title: "WiFi Dongle Hangs the Computer"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by LoneSt4r on 2009-10-31
Hello!

I have been working all afternoon on this and could not find a solution on my own.

This happens on an old IBM ThinkPad laptop.  It was running Jaunty up until last night, when I upgraded to Karmic.  With Jaunty, I could use my WiFi dongle, but it would hang from time to time.  Now, with Karmic, it always hangs.

The dongle is a TrendNet TEW-424UB.  I use it with the original Windows XP drivers through ndiswrapper.

What makes this bug so hard to troubleshoot is that the laptop hangs only a few seconds after I plug the dongle in.  I tried to boot with the dongle pluged in (the boot sequences hands) or to plug it in midway through the boot process (the splash screen hangs immediately).

At least, that tells me that it is not an issue with the Network Manager, as it is not yet loaded at that point.

lsusb returns (on another computer)

```
Bus 001 Device 010: ID 0457:0163 Silicon Integrated Systems Corp. 802.11 Wireless LAN Adapter
```

I extracted the relevant syslog information from when it used to work.

```
Oct 30 20:50:27 Reboot kernel: [ 1824.472086] usb 1-1: reset full speed USB device using uhci_hcd and address 5
Oct 30 20:50:28 Reboot kernel: [ 1824.917000] ndiswrapper: driver sis163u (TRENDnet,11/02/2005,5.1.1039.1050) loaded
Oct 30 20:50:30 Reboot kernel: [ 1826.862741] wlan0: ethernet device 00:40:f4:e2:c3:58 using NDIS driver: sis163u, version: 0x1000000, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0457:0163.F.conf
Oct 30 20:50:30 Reboot kernel: [ 1826.912917] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Oct 30 20:50:30 Reboot nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_40_f4_e2_c3_58, iface: wlan0): not well known
Oct 30 20:50:30 Reboot NetworkManager: <info>  (wlan0): driver does not support SSID scans (scan_capa 0x00). 
Oct 30 20:50:30 Reboot NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper') 
Oct 30 20:50:30 Reboot NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_40_f4_e2_c3_58 
Oct 30 20:50:35 Reboot NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
Oct 30 20:50:35 Reboot NetworkManager: <info>  (wlan0): bringing up device. 
Oct 30 20:50:35 Reboot NetworkManager: <info>  (wlan0): preparing device. 
Oct 30 20:50:35 Reboot NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
Oct 30 20:50:35 Reboot kernel: [ 1831.729504] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 30 20:50:35 Reboot NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Oct 30 20:50:35 Reboot NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
Oct 30 20:50:35 Reboot NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Oct 30 20:50:35 Reboot kernel: [ 1832.203627] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct 30 20:50:37 Reboot avahi-daemon[2589]: Registering new address record for fe80::240:f4ff:fee2:c358 on wlan0.*.
Oct 30 20:50:37 Reboot NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready 
Oct 30 20:50:45 Reboot kernel: [ 1842.608070] wlan0: no IPv6 routers present
Oct 30 20:50:47 Reboot NetworkManager: <info>  Activation (wlan0) starting connection 'Auto LoneStar' 
Oct 30 20:50:47 Reboot NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Oct 30 20:50:47 Reboot NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Oct 30 20:50:47 Reboot NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 30 20:50:47 Reboot NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Oct 30 20:50:47 Reboot NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 30 20:50:47 Reboot NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Oct 30 20:50:47 Reboot NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Oct 30 20:50:47 Reboot NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Oct 30 20:50:47 Reboot NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Oct 30 20:50:47 Reboot NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto LoneStar' has security, and secrets exist.  No new secrets needed. 
Oct 30 20:50:47 Reboot NetworkManager: <info>  Config: added 'ssid' value 'LoneStar' 
Oct 30 20:50:47 Reboot NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Oct 30 20:50:47 Reboot NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Oct 30 20:50:47 Reboot NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Oct 30 20:50:47 Reboot NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Oct 30 20:50:47 Reboot NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Oct 30 20:50:47 Reboot NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Oct 30 20:50:47 Reboot NetworkManager: <info>  Config: set interface ap_scan to 1 
Oct 30 20:50:47 Reboot NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected 
Oct 30 20:50:47 Reboot NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Oct 30 20:50:52 Reboot NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Oct 30 20:50:52 Reboot NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated 
Oct 30 20:50:52 Reboot NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Oct 30 20:50:52 Reboot NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Oct 30 20:50:52 Reboot NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed 
Oct 30 20:50:52 Reboot NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'LoneStar'. 
Oct 30 20:50:52 Reboot NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 30 20:50:52 Reboot NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Oct 30 20:50:52 Reboot NetworkManager: <info>  (wlan0): device state change: 5 -> 7 
Oct 30 20:50:52 Reboot NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Oct 30 20:50:52 Reboot NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Oct 30 20:50:53 Reboot NetworkManager: <info>  dhclient started with pid 5700 
Oct 30 20:50:53 Reboot NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Oct 30 20:50:53 Reboot dhclient: Internet Systems Consortium DHCP Client V3.1.1
Oct 30 20:50:53 Reboot dhclient: Copyright 2004-2008 Internet Systems Consortium.
Oct 30 20:50:53 Reboot dhclient: All rights reserved.
Oct 30 20:50:53 Reboot dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Oct 30 20:50:53 Reboot dhclient: 
Oct 30 20:50:53 Reboot NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit 
Oct 30 20:50:53 Reboot dhclient: Listening on LPF/wlan0/00:40:f4:e2:c3:58
Oct 30 20:50:53 Reboot dhclient: Sending on   LPF/wlan0/00:40:f4:e2:c3:58
Oct 30 20:50:53 Reboot dhclient: Sending on   Socket/fallback
Oct 30 20:50:55 Reboot dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 30 20:50:55 Reboot dhclient: DHCPOFFER of 192.168.2.108 from 192.168.2.254
Oct 30 20:50:55 Reboot dhclient: DHCPREQUEST of 192.168.2.108 on wlan0 to 255.255.255.255 port 67
Oct 30 20:50:55 Reboot dhclient: DHCPACK of 192.168.2.108 from 192.168.2.254
Oct 30 20:50:55 Reboot NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> bound 
Oct 30 20:50:55 Reboot NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct 30 20:50:55 Reboot NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
Oct 30 20:50:55 Reboot NetworkManager: <info>    address 192.168.2.108 
Oct 30 20:50:55 Reboot NetworkManager: <info>    prefix 24 (255.255.255.0) 
Oct 30 20:50:55 Reboot NetworkManager: <info>    gateway 192.168.2.254 
Oct 30 20:50:55 Reboot NetworkManager: <info>    nameserver '192.168.2.254' 
Oct 30 20:50:55 Reboot NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 30 20:50:55 Reboot NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
Oct 30 20:50:55 Reboot NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Oct 30 20:50:55 Reboot avahi-daemon[2589]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.2.108.
Oct 30 20:50:55 Reboot dhclient: bound to 192.168.2.108 -- renewal in 481226 seconds.
Oct 30 20:50:55 Reboot avahi-daemon[2589]: New relevant interface wlan0.IPv4 for mDNS.
Oct 30 20:50:55 Reboot avahi-daemon[2589]: Registering new address record for 192.168.2.108 on wlan0.IPv4.
Oct 30 20:50:56 Reboot NetworkManager: <info>  (wlan0): device state change: 7 -> 8 
Oct 30 20:50:56 Reboot NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Oct 30 20:50:56 Reboot NetworkManager: <info>  Policy set 'Auto LoneStar' (wlan0) as default for routing and DNS. 
Oct 30 20:50:56 Reboot NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Oct 30 20:50:56 Reboot NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 30 20:51:00 Reboot dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Oct 30 20:51:01 Reboot ntpdate[5763]: adjust time server 91.189.94.4 offset 0.153129 sec
Oct 30 20:51:07 Reboot dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Oct 30 20:51:17 Reboot dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
Oct 30 20:51:38 Reboot dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Oct 30 20:51:49 Reboot dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Oct 30 20:52:01 Reboot dhclient: No DHCPOFFERS received.
Oct 30 20:52:01 Reboot dhclient: No working leases in persistent database - sleeping.
Oct 30 20:55:04 Reboot NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake 
Oct 30 20:55:05 Reboot NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed 
Oct 30 20:55:54 Reboot avahi-daemon[2589]: Interface wlan0.IPv4 no longer relevant for mDNS.
Oct 30 20:55:54 Reboot avahi-daemon[2589]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.2.108.
Oct 30 20:55:54 Reboot dhclient: receive_packet failed on wlan0: Network is down
Oct 30 20:55:54 Reboot kernel: [ 2150.824114] usb 1-1: USB disconnect, address 5
Oct 30 20:55:55 Reboot NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected 
Oct 30 20:55:55 Reboot avahi-daemon[2589]: Withdrawing address record for fe80::240:f4ff:fee2:c358 on wlan0.
Oct 30 20:55:55 Reboot avahi-daemon[2589]: Withdrawing address record for 192.168.2.108 on wlan0.
Oct 30 20:55:55 Reboot kernel: [ 2152.369468] ndiswrapper: device wlan0 removed
Oct 30 20:55:55 Reboot nm-system-settings:    SCPlugin-Ifupdown: devices removed (udi: /org/freedesktop/Hal/devices/net_00_40_f4_e2_c3_58)
Oct 30 20:55:55 Reboot NetworkManager: <info>  (wlan0): now unmanaged 
Oct 30 20:55:55 Reboot NetworkManager: <info>  (wlan0): device state change: 8 -> 1 
Oct 30 20:55:55 Reboot NetworkManager: <info>  (wlan0): deactivating device (reason: 36). 
Oct 30 20:55:55 Reboot NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 5700 
Oct 30 20:55:56 Reboot NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Oct 30 20:55:56 Reboot NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
Oct 30 20:55:56 Reboot NetworkManager: <info>  (wlan0): cleaning up... 
Oct 30 20:55:56 Reboot NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
```

Here is what I get now before the computer hangs.

```
Oct 31 15:07:20 Reboot kernel: [ 1046.396202] usb 1-1: new full speed USB device using uhci_hcd and address 2
Oct 31 15:07:20 Reboot kernel: [ 1046.543485] usb 1-1: configuration #1 chosen from 1 choice
Oct 31 15:07:21 Reboot kernel: [ 1047.344146] Disabling lock debugging due to kernel taint
Oct 31 15:07:21 Reboot kernel: [ 1047.366357] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Oct 31 15:07:21 Reboot kernel: [ 1047.608090] usb 1-1: reset full speed USB device using uhci_hcd and address 2
Oct 31 15:07:22 Reboot kernel: [ 1047.828291] ndiswrapper: driver sis163u (TRENDnet,11/02/2005,5.1.1039.1050) loaded
```

Any insight would be highly appreciated.

Thanks!

---

### Post by LoneSt4r on 2009-11-02
Hello!

I found out that it is related to the kernel version.  With Jaunty I was using 2.6.28-16-generic.  My wireless dongle still works when I use that kernel.

However, the two kernels installed with Karmic (2.6.31-11-generic and 2.6.31-14-generic) hang when I plug the dongle in.

Hoping that helps pin pointing the problem...

---

### Post by LordOfTheCows on 2009-11-04
Having just upgraded to 9.10, I can confirm this issue. Note that for me the wifi dongle (trendnet TEW-424UB V2) worked perfectly on 9.04. I have tried the Windows 98, 2000 and XP drivers with the same results.

Help!

---

