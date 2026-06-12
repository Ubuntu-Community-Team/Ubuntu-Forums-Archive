---
title: "WUSB54G Unable to Authenticate"
date: 2009-06-19
forum: Networking &amp; Wireless
---

### Post by trelichiban on 2009-06-19
I have two wireless adapters (Linksys WUSB54G ver. 4) that I am trying to use to connect to a home network via Verizon modem/router (MI424WR-GEN2).  Both Linksys adapters work on Windows machines, for I have tested both on on a Win XP laptop and this Vista 32 machine.  Yes, I am posting this with one of the USB adapters.

Now, whenever I plug in the adapters to the Ubuntu machine in question, the device is recognized.  It is then used by NetworkManager to find nearby wireless networks.  It succeeds in identifying my Verizon router, neighbor's Verizon routers, and another Netgear router I set up to test it.  Whenever I try to connect with a network, the task fails.  On both adapters!  This scenario plays out on the native Gutsy install and a Fedora 11 Live CD.

The Verizon network uses a WPA2-personal encryption and the Netgear router is set up as an AP running WPA-personal.  The following log corresponds to daemon.log additions after trying to connect to the Netgear router's "Orange Portal" network.

```
Jun 18 17:10:44 Monitor NetworkManager: <debug> [1245359444.519809] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'Orange Portal' 
Jun 18 17:10:44 Monitor NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / Orange Portal 
Jun 18 17:10:44 Monitor NetworkManager: <info>  Deactivating device wlan0. 
Jun 18 17:10:44 Monitor NetworkManager: <info>  Device wlan0 activation scheduled... 
Jun 18 17:10:44 Monitor NetworkManager: <info>  Activation (wlan0) started... 
Jun 18 17:10:44 Monitor NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Jun 18 17:10:44 Monitor NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Jun 18 17:10:44 Monitor NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Jun 18 17:10:44 Monitor NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Jun 18 17:10:44 Monitor NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Jun 18 17:10:44 Monitor NetworkManager: <info>  Activation (wlan0/wireless): access point 'Orange Portal' is encrypted, but NO valid key exists.  New key needed. 
Jun 18 17:10:44 Monitor NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'Orange Portal'. 
Jun 18 17:10:44 Monitor NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Jun 18 17:11:02 Monitor NetworkManager: <info>  Activation (wlan0) New wireless user key for network 'Orange Portal' received. 
Jun 18 17:11:02 Monitor NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Jun 18 17:11:02 Monitor NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Jun 18 17:11:02 Monitor NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Jun 18 17:11:02 Monitor NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Jun 18 17:11:02 Monitor NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Jun 18 17:11:02 Monitor NetworkManager: <info>  Activation (wlan0/wireless): access point 'Orange Portal' is encrypted, and a key exists.  No new key needed. 
Jun 18 17:11:03 Monitor NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Jun 18 17:11:03 Monitor NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Jun 18 17:11:03 Monitor NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant2^I' 
Jun 18 17:11:03 Monitor NetworkManager: <info>  SUP: response was 'OK' 
Jun 18 17:11:03 Monitor NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Jun 18 17:11:03 Monitor NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Jun 18 17:11:03 Monitor NetworkManager: <info>  SUP: response was 'OK' 
Jun 18 17:11:03 Monitor NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Jun 18 17:11:03 Monitor NetworkManager: <info>  SUP: response was '0' 
Jun 18 17:11:03 Monitor NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 4f72616e676520506f7274616c' 
Jun 18 17:11:03 Monitor NetworkManager: <info>  SUP: response was 'OK' 
Jun 18 17:11:03 Monitor NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Jun 18 17:11:03 Monitor NetworkManager: <info>  SUP: response was 'OK' 
Jun 18 17:11:03 Monitor NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Jun 18 17:11:03 Monitor NetworkManager: <info>  SUP: response was 'OK' 
Jun 18 17:11:03 Monitor NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Jun 18 17:11:03 Monitor NetworkManager: <info>  SUP: response was 'OK' 
Jun 18 17:11:03 Monitor NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Jun 18 17:11:03 Monitor NetworkManager: <info>  SUP: response was 'OK' 
Jun 18 17:11:03 Monitor NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Jun 18 17:11:10 Monitor NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Jun 18 17:11:44 Monitor last message repeated 6 times
Jun 18 17:11:55 Monitor last message repeated 2 times
Jun 18 17:12:03 Monitor NetworkManager: <info>  Activation (wlan0/wireless): association took too long (>60s), failing activation. 
Jun 18 17:12:03 Monitor NetworkManager: <info>  Activation (wlan0) failure scheduled... 
Jun 18 17:12:03 Monitor NetworkManager: <info>  Activation (wlan0) failed for access point (Orange Portal) 
Jun 18 17:12:03 Monitor NetworkManager: <info>  Activation (wlan0) failed. 
Jun 18 17:12:03 Monitor NetworkManager: <info>  Deactivating device wlan0. 
Jun 18 17:12:03 Monitor NetworkManager: <info>  SUP: sending command 'DISABLE_NETWORK 0' 
Jun 18 17:12:03 Monitor NetworkManager: <info>  SUP: response was 'OK' 
Jun 18 17:12:03 Monitor NetworkManager: <info>  SUP: sending command 'AP_SCAN 0' 
Jun 18 17:12:03 Monitor NetworkManager: <info>  SUP: response was 'OK' 
Jun 18 17:12:03 Monitor NetworkManager: <info>  SUP: sending command 'TERMINATE' 
Jun 18 17:12:03 Monitor NetworkManager: <info>  SUP: response was 'OK' 

```

I don't understand how the system can recognize the router and identify network SSIDs but not connect to them.  Especially when the problem spans distros but doesn't manifest with Windows.

---

### Post by trelichiban on 2009-06-19
Bompity bump.

---

### Post by trelichiban on 2009-06-20
Any ideas?

---

