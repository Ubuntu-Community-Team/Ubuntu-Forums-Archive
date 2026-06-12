---
title: "Dell TrueMobile 1300 (Broadcom 4306) and Jaunty problems"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by MilesCrew on 2009-04-30
I'm a newbie so bear with me. I've installed the final release of 9.04 on a Dell Latitude X300 with the Dell TrueMobile 1300 wireless card which is a Broadcom 4306 chipset. At first it didn't work at all, but I did some digging and research and finally got it somewhat working. I've installed the ndiswrapper and the corresponding Windows driver (bcmwl5) and then blacklisted the b43-legacy and ssb. After this it finally let me see the available networks as well as connect to Open authencticated networks with no passwords or encryption. However, I cannot connect to (a) my home network of WPA2-TKIP or WPA2-AES (tried both) and (b) my corporate network with WPA-Enterprise, TKIP, MSCHAPv2, with certificate. The home network fails with DHCP and the corporate network fails by continually asking me for the credentials. To aid in the help, here are some outputs that I've seen usually asked for...

'lshw -C Network' gives...

```
  *-network:0             
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: wlan0
       version: 02
       serial: 00:90:4b:2e:96:e3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.53+Broadcom,12/04/2006, 4.10.4 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```

'ndiswrapper -l' gives...

```
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)

```

'cat /etc/modprobe.d/blacklist.conf' gives...

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

blacklist ssb

```

'iwconfig' gives...

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

This is the syslog messages when I try to connect at home (WPA2-TKIP or WPA2-AES)...

```
Apr 30 07:02:00 robert-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto MilesCrew' 
Apr 30 07:02:00 robert-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Apr 30 07:02:00 robert-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 30 07:02:00 robert-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Apr 30 07:02:00 robert-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Apr 30 07:02:00 robert-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Apr 30 07:02:00 robert-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Apr 30 07:02:00 robert-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Apr 30 07:02:00 robert-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto MilesCrew' has security, but secrets are required. 
Apr 30 07:02:00 robert-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 
Apr 30 07:02:00 robert-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Apr 30 07:02:00 robert-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 30 07:02:00 robert-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Apr 30 07:02:00 robert-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 
Apr 30 07:02:00 robert-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Apr 30 07:02:00 robert-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Apr 30 07:02:00 robert-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Apr 30 07:02:00 robert-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Apr 30 07:02:00 robert-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto MilesCrew' has security, and secrets exist.  No new secrets needed. 
Apr 30 07:02:00 robert-laptop NetworkManager: <info>  Config: added 'ssid' value 'MilesCrew' 
Apr 30 07:02:00 robert-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Apr 30 07:02:00 robert-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Apr 30 07:02:00 robert-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Apr 30 07:02:00 robert-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Apr 30 07:02:00 robert-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Apr 30 07:02:00 robert-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Apr 30 07:02:00 robert-laptop NetworkManager: <info>  Config: set interface ap_scan to 1 
Apr 30 07:02:00 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected 
Apr 30 07:02:00 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Apr 30 07:02:05 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Apr 30 07:02:06 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated 
Apr 30 07:02:06 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Apr 30 07:02:06 robert-laptop kernel: [12155.852599] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Apr 30 07:02:06 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Apr 30 07:02:06 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed 
Apr 30 07:02:06 robert-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'MilesCrew'. 
Apr 30 07:02:06 robert-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr 30 07:02:06 robert-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Apr 30 07:02:06 robert-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 
Apr 30 07:02:06 robert-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Apr 30 07:02:06 robert-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Apr 30 07:02:06 robert-laptop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Apr 30 07:02:06 robert-laptop dhclient: All rights reserved.
Apr 30 07:02:06 robert-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Apr 30 07:02:06 robert-laptop dhclient: 
Apr 30 07:02:06 robert-laptop NetworkManager: <info>  dhclient started with pid 15757 
Apr 30 07:02:06 robert-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Apr 30 07:02:06 robert-laptop NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit 
Apr 30 07:02:06 robert-laptop dhclient: Listening on LPF/wlan0/00:90:4b:2e:96:e3
Apr 30 07:02:06 robert-laptop dhclient: Sending on   LPF/wlan0/00:90:4b:2e:96:e3
Apr 30 07:02:06 robert-laptop dhclient: Sending on   Socket/fallback
Apr 30 07:02:07 robert-laptop avahi-daemon[2576]: Registering new address record for fe80::290:4bff:fe2e:96e3 on wlan0.*.
Apr 30 07:02:10 robert-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Apr 30 07:02:10 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associated 
Apr 30 07:02:10 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Apr 30 07:02:10 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Apr 30 07:02:10 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed 
Apr 30 07:02:14 robert-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Apr 30 07:02:14 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associated 
Apr 30 07:02:14 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Apr 30 07:02:14 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Apr 30 07:02:14 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed 
Apr 30 07:02:16 robert-laptop kernel: [12166.672148] wlan0: no IPv6 routers present
Apr 30 07:02:19 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associated 
Apr 30 07:02:19 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Apr 30 07:02:19 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Apr 30 07:02:19 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed 
Apr 30 07:02:23 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associated 
Apr 30 07:02:23 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Apr 30 07:02:23 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Apr 30 07:02:23 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed 
Apr 30 07:02:24 robert-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
Apr 30 07:02:28 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associated 
Apr 30 07:02:28 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Apr 30 07:02:28 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Apr 30 07:02:28 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed 
Apr 30 07:02:32 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associated 
Apr 30 07:02:32 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Apr 30 07:02:32 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Apr 30 07:02:32 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed 
Apr 30 07:02:36 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associated 
Apr 30 07:02:36 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Apr 30 07:02:36 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Apr 30 07:02:36 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed 
Apr 30 07:02:41 robert-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Apr 30 07:02:41 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associated 
Apr 30 07:02:42 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Apr 30 07:02:42 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Apr 30 07:02:42 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed 
Apr 30 07:02:46 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associated 
Apr 30 07:02:46 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Apr 30 07:02:46 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Apr 30 07:02:46 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed 
Apr 30 07:02:50 robert-laptop NetworkManager: <info>  Device 'wlan0' DHCP transaction took too long (>45s), stopping it. 
Apr 30 07:02:51 robert-laptop NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 15757 
Apr 30 07:02:51 robert-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Apr 30 07:02:51 robert-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) started... 
Apr 30 07:02:51 robert-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 9 
Apr 30 07:02:51 robert-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (MilesCrew) 
Apr 30 07:02:51 robert-laptop NetworkManager: <info>  Marking connection 'Auto MilesCrew' invalid. 
```

This is the wpa_supplicant log when I try to connect at home...

```
Trying to associate with 00:23:69:45:40:f2 (SSID='MilesCrew' freq=2437 MHz)
Associated with 00:23:69:45:40:f2
WPA: Key negotiation completed with 00:23:69:45:40:f2 [PTK=CCMP GTK=CCMP]
CTRL-EVENT-CONNECTED - Connection to 00:23:69:45:40:f2 completed (reauth) [id=0 id_str=]
Associated with 00:23:69:45:40:f2
WPA: Key negotiation completed with 00:23:69:45:40:f2 [PTK=CCMP GTK=CCMP]
CTRL-EVENT-CONNECTED - Connection to 00:23:69:45:40:f2 completed (reauth) [id=0 id_str=]
Associated with 00:23:69:45:40:f2
WPA: Key negotiation completed with 00:23:69:45:40:f2 [PTK=CCMP GTK=CCMP]
CTRL-EVENT-CONNECTED - Connection to 00:23:69:45:40:f2 completed (reauth) [id=0 id_str=]
Associated with 00:23:69:45:40:f2
WPA: Key negotiation completed with 00:23:69:45:40:f2 [PTK=CCMP GTK=CCMP]
CTRL-EVENT-CONNECTED - Connection to 00:23:69:45:40:f2 completed (reauth) [id=0 id_str=]
Associated with 00:23:69:45:40:f2
WPA: Key negotiation completed with 00:23:69:45:40:f2 [PTK=CCMP GTK=CCMP]
CTRL-EVENT-CONNECTED - Connection to 00:23:69:45:40:f2 completed (reauth) [id=0 id_str=]
Associated with 00:23:69:45:40:f2
WPA: Key negotiation completed with 00:23:69:45:40:f2 [PTK=CCMP GTK=CCMP]
CTRL-EVENT-CONNECTED - Connection to 00:23:69:45:40:f2 completed (reauth) [id=0 id_str=]
Associated with 00:23:69:45:40:f2
WPA: Key negotiation completed with 00:23:69:45:40:f2 [PTK=CCMP GTK=CCMP]
CTRL-EVENT-CONNECTED - Connection to 00:23:69:45:40:f2 completed (reauth) [id=0 id_str=]
Associated with 00:23:69:45:40:f2
WPA: Key negotiation completed with 00:23:69:45:40:f2 [PTK=CCMP GTK=CCMP]
CTRL-EVENT-CONNECTED - Connection to 00:23:69:45:40:f2 completed (reauth) [id=0 id_str=]
Associated with 00:23:69:45:40:f2
WPA: Key negotiation completed with 00:23:69:45:40:f2 [PTK=CCMP GTK=CCMP]
CTRL-EVENT-CONNECTED - Connection to 00:23:69:45:40:f2 completed (reauth) [id=0 id_str=]
Associated with 00:23:69:45:40:f2
WPA: Key negotiation completed with 00:23:69:45:40:f2 [PTK=CCMP GTK=CCMP]
CTRL-EVENT-CONNECTED - Connection to 00:23:69:45:40:f2 completed (reauth) [id=0 id_str=]
Associated with 00:23:69:45:40:f2
WPA: Key negotiation completed with 00:23:69:45:40:f2 [PTK=CCMP GTK=CCMP]
CTRL-EVENT-CONNECTED - Connection to 00:23:69:45:40:f2 completed (reauth) [id=0 id_str=]
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
```

This is the syslog when I try to connect at corporate (WPA-Enterprise, TKIP, MSCHAPv2, certificate)...

```
Apr 29 08:42:49 robert-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'WPBC Private' 
Apr 29 08:42:49 robert-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Apr 29 08:42:49 robert-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 29 08:42:49 robert-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Apr 29 08:42:49 robert-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Apr 29 08:42:49 robert-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Apr 29 08:42:49 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected 
Apr 29 08:42:49 robert-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Apr 29 08:42:49 robert-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Apr 29 08:42:49 robert-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'WPBC Private' has security, but secrets are required. 
Apr 29 08:42:49 robert-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 
Apr 29 08:42:49 robert-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Apr 29 08:42:52 robert-laptop NetworkManager: <debug> [1241008972.000308] ensure_killed(): waiting for dnsmasq pid 7719 to exit 
Apr 29 08:42:52 robert-laptop NetworkManager: <debug> [1241008972.000462] ensure_killed(): dnsmasq pid 7719 cleaned up 
Apr 29 08:42:59 robert-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 29 08:42:59 robert-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Apr 29 08:42:59 robert-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 
Apr 29 08:42:59 robert-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Apr 29 08:42:59 robert-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Apr 29 08:42:59 robert-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Apr 29 08:42:59 robert-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Apr 29 08:42:59 robert-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'WPBC Private' has security, and secrets exist.  No new secrets needed. 
Apr 29 08:42:59 robert-laptop NetworkManager: <info>  Config: added 'ssid' value 'WPBC Private' 
Apr 29 08:42:59 robert-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Apr 29 08:42:59 robert-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-EAP' 
Apr 29 08:42:59 robert-laptop NetworkManager: <info>  Config: added 'password' value '<omitted>' 
Apr 29 08:42:59 robert-laptop NetworkManager: <info>  Config: added 'eap' value 'PEAP' 
Apr 29 08:42:59 robert-laptop NetworkManager: <info>  Config: added 'fragment_size' value '1300' 
Apr 29 08:42:59 robert-laptop NetworkManager: <info>  Config: added 'phase2' value 'auth=MSCHAPV2' 
Apr 29 08:42:59 robert-laptop NetworkManager: <info>  Config: added 'ca_cert' value 'blob://-org-freedesktop-NetworkManagerSettings-0-ca_cert' 
Apr 29 08:42:59 robert-laptop NetworkManager: <info>  Config: added 'identity' value 'woodlandpark\rmiles' 
Apr 29 08:42:59 robert-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Apr 29 08:42:59 robert-laptop NetworkManager: <info>  Config: set interface ap_scan to 2 
Apr 29 08:42:59 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Apr 29 08:43:00 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Apr 29 08:44:00 robert-laptop NetworkManager: <info>  Activation (wlan0/wireless): association took too long. 
Apr 29 08:44:00 robert-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 
Apr 29 08:44:00 robert-laptop NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets 
Apr 29 08:44:00 robert-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected 
Apr 29 08:44:07 robert-laptop NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: applet-device-wifi.c.1539 (get_secrets_dialog_response_cb): canceled. 
Apr 29 08:44:07 robert-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 9 
Apr 29 08:44:07 robert-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (WPBC Private) 
Apr 29 08:44:07 robert-laptop NetworkManager: <info>  Marking connection 'WPBC Private' invalid. 
```

This is the wpa_supplicant when I try to connect at work...

```
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with SSID 'WPBC Private'
CTRL-EVENT-SCAN-RESULTS 
Authentication with 00:00:00:00:00:00 timed out.
Trying to associate with SSID 'WPBC Private'
CTRL-EVENT-SCAN-RESULTS 
Authentication with 00:00:00:00:00:00 timed out.
CTRL-EVENT-SCAN-RESULTS 
```

---

### Post by chili555 on 2009-04-30
This probably doesn't have much effect on WPA, however, just to be tidy, where in *blacklist* do I see:```
blacklist b43
```You said:> and then blacklisted the b43-legacy and ssb.What does this tell us?```
lsmod | grep b43
lsmod | grep ssb
```This part:> bcmwl5 : driver installed
	device (14E4:4320) present [COLOR="Red"](alternate driver: ssb)[/COLOR]suggests, to me, that because b43 is not blacklisted, it loads and brings ssb along with it. I wonder if they are fighting you.

---

### Post by MilesCrew on 2009-04-30
Thanks for the reply. You're right, I didn't actually blacklist b43, but I had ssb in there. So, I just added "blacklist b43" in there and rebooted. Still no go.

To answer your question, "lsmod | grep b43" and "lsmod | grep ssb" both return nothing. Even after explicitly blacklisting b43, "ndiswrapper -l" still shows "alternate driver: ssb".

In my research I'm seeing people talk about changing the /etc/wpa_supplicant.conf file, but I don't have this file. I have a directory of /etc/wpa_supplicant with three other files in there which are not config files. Is this right?

---

### Post by Guitarmaster316 on 2009-05-11
I have the same issue with my HP pavillion and 4306.  I got it to work by installing ndiswrapper with Build Install. Ndistk didn't work for me. After that I had to go to System/Hardware Drivers and activate b43legacy.


IT WORKED but....

It gives me this

```
matt@mattz:~$ dmesg | grep -e ndis -e wlan0
[   22.690499] ndiswrapper version 1.54 loaded (smp=yes, preempt=no)
[   22.771701] ndiswrapper: driver bcmwl5 (Linksys,02/12/2003, 3.10.39.7) loaded
[   22.772630] ndiswrapper 0000:00:09.0: PCI INT A -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
[   22.862755] ndiswrapper: using IRQ 10
[   23.077250] wlan0: ethernet device 00:90:4b:42:d4:a8 using NDIS driver: bcmwl5, version: 0x50000, NDIS version: 0x500, vendor: 'NDIS Network Adapter', 14E4:4320.5.conf
[   23.077399] ndiswrapper (set_ndis_auth_mode:619): setting auth mode to 3 failed (C0010015)
[   23.077404] wlan0: encryption modes supported: none
[   23.079982] usbcore: registered new interface driver ndiswrapper
[   29.871825] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  235.167086] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  245.404087] wlan0: no IPv6 routers present
matt@mattz:~$
```

It seems that ndiswrapper is not loading WPA_supplicant.  I don't know how to fix that.

If I blacklist b43legacy, wlan0 disappears altogether.
I learned recently that you can't blacklist ssb because it is in use by b44.

---

