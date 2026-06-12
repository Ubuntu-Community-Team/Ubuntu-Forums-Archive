---
title: "Wireless network stops working after hibernation"
date: 2009-10-17
forum: Networking &amp; Wireless
---

### Post by guedesav on 2009-10-17
Oddly, there's always a random chance my wireless card(RTL8187B) will stop authenticating properly after I turn my laptop back from hibernation. The drivers are all okay(I checked lsmod before and after the problem) and this is the bestI could manage to discover from syslog:

```

Oct 15 11:41:39 guedesav-laptop NetworkManager: <info>  wlan0: driver is 'rtl8187'. 
Oct 15 11:41:39 guedesav-laptop NetworkManager: <info>  wlan0: driver supports SSID scans (scan_capa 0x01). 
Oct 15 11:41:39 guedesav-laptop NetworkManager: <info>  Found new 802.11 WiFi device 'wlan0'. 
Oct 15 11:41:39 guedesav-laptop NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_15_af_d5_dc_c7_0 
Oct 15 11:41:43 guedesav-laptop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
Oct 15 11:41:43 guedesav-laptop NetworkManager: <info>  (wlan0): bringing up device. 
Oct 15 11:41:59 guedesav-laptop kernel: [58992.817480] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 15 11:41:59 guedesav-laptop NetworkManager: <info>  (wlan0): preparing device. 
Oct 15 11:41:59 guedesav-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
Oct 15 11:41:59 guedesav-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Oct 15 11:41:59 guedesav-laptop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
Oct 15 11:41:59 guedesav-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Oct 15 11:41:59 guedesav-laptop NetworkManager: <info>  (wlan0): supplicant interface state change: 1 -> 2. 
Oct 15 11:42:03 guedesav-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Oct 15 11:42:04 guedesav-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'basement' 
Oct 15 11:42:04 guedesav-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Oct 15 11:42:04 guedesav-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Oct 15 11:42:04 guedesav-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 15 11:42:04 guedesav-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Oct 15 11:42:04 guedesav-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 15 11:42:04 guedesav-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Oct 15 11:42:04 guedesav-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Oct 15 11:42:04 guedesav-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Oct 15 11:42:04 guedesav-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Oct 15 11:42:04 guedesav-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'basement' has security, and secrets exist.  No new secrets needed. 
Oct 15 11:42:04 guedesav-laptop NetworkManager: <info>  Config: added 'ssid' value 'basement' 
Oct 15 11:42:04 guedesav-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Oct 15 11:42:04 guedesav-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Oct 15 11:42:04 guedesav-laptop NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN' 
Oct 15 11:42:04 guedesav-laptop NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>' 
Oct 15 11:42:04 guedesav-laptop NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0' 
Oct 15 11:42:04 guedesav-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Oct 15 11:42:04 guedesav-laptop NetworkManager: <info>  Config: set interface ap_scan to 1 
Oct 15 11:42:07 guedesav-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 1 -> 2 
Oct 15 11:42:09 guedesav-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Oct 15 11:42:10 guedesav-laptop kernel: [59003.301317] wlan0: authenticate with AP 00:21:29:e9:c2:39
Oct 15 11:42:10 guedesav-laptop kernel: [59003.302960] wlan0: authenticated
Oct 15 11:42:10 guedesav-laptop kernel: [59003.302967] wlan0: associate with AP 00:21:29:e9:c2:39
Oct 15 11:42:10 guedesav-laptop kernel: [59003.305362] wlan0: RX AssocResp from 00:21:29:e9:c2:39 (capab=0x411 status=0 aid=1)
Oct 15 11:42:10 guedesav-laptop kernel: [59003.305367] wlan0: associated
Oct 15 11:42:10 guedesav-laptop kernel: [59003.306238] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct 15 11:42:10 guedesav-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 4 
Oct 15 11:42:10 guedesav-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 7 
Oct 15 11:42:10 guedesav-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'basement'. 
Oct 15 11:42:10 guedesav-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 15 11:42:10 guedesav-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Oct 15 11:42:10 guedesav-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 
Oct 15 11:42:10 guedesav-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Oct 15 11:42:10 guedesav-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Oct 15 11:42:10 guedesav-laptop NetworkManager: <info>  dhclient started with pid 27893 
Oct 15 11:42:10 guedesav-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 

```

This is the usual routine of messages NetworkManager displays when connecting. After this comes network parameters configuration(SSID, key, gateway, DNS, etc.). But this is where I noticed a major change:

```

Oct 15 11:42:04 guedesav-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'basement' has security, and secrets exist.  No new secrets needed. 

```

**Because when the network isn't working properly this turns into**

```

Oct 17 11:46:40 guedesav-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'basement' has security, but secrets are required. 

```

With everything before the same, and this is what comes after

```

Oct 17 11:46:40 guedesav-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 
Oct 17 11:46:40 guedesav-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Oct 17 11:46:40 guedesav-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Oct 17 11:46:40 guedesav-laptop NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: A security policy in place prevents this sender from sending this message to this recipient, see message bus configuration file (rejected message had interface "org.freedesktop.NetworkManagerSettings.Connection.Secrets" member "GetSecrets" error name "(unset)" destination "org.freedesktop.NetworkManagerUserSettings"). 
Oct 17 11:46:40 guedesav-laptop NetworkManager: <info>  (wlan0): device state change: 6 -> 9 
Oct 17 11:46:40 guedesav-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (basement) 
Oct 17 11:46:40 guedesav-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Oct 17 11:46:40 guedesav-laptop NetworkManager: <info>  Marking connection 'basement' invalid. 
Oct 17 11:46:40 guedesav-laptop NetworkManager: <info>  Activation (wlan0) failed. 
Oct 17 11:46:40 guedesav-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 
Oct 17 11:46:40 guedesav-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 
Oct 17 11:46:40 guedesav-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 

```

I have no idea why, though, I changed nothing on the laptop or the router configuration. Then, after rebooting the system(actually turning off and on, not hibernation) it goes back to normal.

I've already tried restarting NetworkManager, networking, reinstall the drivers... to no avail. Only rebooting works, but this makes no sense, so... does anyone have a hint of what's going on?

---

