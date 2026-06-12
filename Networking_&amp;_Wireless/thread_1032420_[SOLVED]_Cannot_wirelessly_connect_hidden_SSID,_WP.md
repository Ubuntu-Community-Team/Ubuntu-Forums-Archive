---
title: "[SOLVED] Cannot wirelessly connect: hidden SSID, WPA"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by HDave on 2009-01-06
I am running Ibex on a Dell laptop and can connect to wireless networks flawlessly, including ones with WPA security.  However, I cannot connect to the main one at my office -- which does not broadcast the SSID.

I manually create the connection in the wireless tab of the network manager, and it appears to try to connect -- but always fails.

I have read a vexing array of launchpad issues regarding hidden SSID's, but most of them seem to be fixed.

My wifi is a Broadcom BCM4328 (Vendor = 0x14E4, Product = 0x4328). Any help is much appreciated!!

---

### Post by HDave on 2009-01-06
Here is the relevant section from my syslog:


```
Jan  6 12:09:43 my-m1210 NetworkManager: <info>  Activation (eth1) starting connection 'cl-wlan' 
Jan  6 12:09:43 my-m1210 NetworkManager: <info>  (eth1): device state change: 3 -> 4 
Jan  6 12:09:43 my-m1210 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jan  6 12:09:43 my-m1210 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jan  6 12:09:43 my-m1210 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jan  6 12:09:43 my-m1210 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jan  6 12:09:43 my-m1210 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jan  6 12:09:43 my-m1210 NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Jan  6 12:09:43 my-m1210 NetworkManager: <info>  Activation (eth1/wireless): access point 'cl-wlan' has security, but secrets are required. 
Jan  6 12:09:43 my-m1210 NetworkManager: <info>  (eth1): device state change: 5 -> 6 
Jan  6 12:09:43 my-m1210 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jan  6 12:09:43 my-m1210 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jan  6 12:09:43 my-m1210 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jan  6 12:09:43 my-m1210 NetworkManager: <info>  (eth1): device state change: 6 -> 4 
Jan  6 12:09:43 my-m1210 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jan  6 12:09:43 my-m1210 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jan  6 12:09:43 my-m1210 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jan  6 12:09:43 my-m1210 NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Jan  6 12:09:43 my-m1210 NetworkManager: <info>  Activation (eth1/wireless): connection 'cl-wlan' has security, and secrets exist.  No new secrets needed. 
Jan  6 12:09:43 my-m1210 NetworkManager: <info>  Config: added 'ssid' value 'cl-wlan' 
Jan  6 12:09:43 my-m1210 NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Jan  6 12:09:43 my-m1210 NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Jan  6 12:09:43 my-m1210 NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Jan  6 12:09:43 my-m1210 NetworkManager: <info>  Config: added 'proto' value 'WPA RSN' 
Jan  6 12:09:43 my-m1210 NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP' 
Jan  6 12:09:43 my-m1210 NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP' 
Jan  6 12:09:43 my-m1210 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jan  6 12:09:43 my-m1210 NetworkManager: <info>  Config: set interface ap_scan to 2 
Jan  6 12:09:43 my-m1210 NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 0 
Jan  6 12:09:43 my-m1210 NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Jan  6 12:09:43 my-m1210 NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 3 
Jan  6 12:09:58 my-m1210 NetworkManager: <info>  eth1: link timed out. 
Jan  6 12:10:43 my-m1210 NetworkManager: <info>  Activation (eth1/wireless): association took too long. 
Jan  6 12:10:43 my-m1210 NetworkManager: <info>  (eth1): device state change: 5 -> 6 
Jan  6 12:10:43 my-m1210 NetworkManager: <info>  Activation (eth1/wireless): asking for new secrets 
Jan  6 12:10:43 my-m1210 NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 0 
Jan  6 12:10:43 my-m1210 NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Jan  6 12:10:43 my-m1210 NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 3 
Jan  6 12:10:43 my-m1210 NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 0 
Jan  6 12:10:58 my-m1210 NetworkManager: <info>  eth1: link timed out. 
Jan  6 12:11:01 my-m1210 NetworkManager: <info>  (eth3): device state change: 8 -> 3 
Jan  6 12:11:01 my-m1210 NetworkManager: <info>  (eth3): deactivating device (reason: 0). 
Jan  6 12:11:01 my-m1210 NetworkManager: <info>  eth3: canceled DHCP transaction, dhcp client pid 7463 
```

---

### Post by Favux on 2009-01-07
Hi HDave,

You don't say what kind of WPA security you're trying to connect to.  I'm going to guess WPA2-TKIP.  If so you need to remove CCMP from your group key.  See:

[http://ubuntuforums.org/showthread.php?t=1010650]("http://ubuntuforums.org/showthread.php?t=1010650")

---

### Post by HDave on 2009-01-07
> **Favux said:**
> Hi HDave,

You don't say what kind of WPA security you're trying to connect to.  I'm going to guess WPA2-TKIP.  If so you need to remove CCMP from your group key.  See:

[http://ubuntuforums.org/showthread.php?t=1010650]("http://ubuntuforums.org/showthread.php?t=1010650")

If I could hit the thank you button 1,000 times I would.   It took a few extra steps in my case, but your guide helped me tremendously.  THANKS!!! :popcorn:

---

### Post by Favux on 2009-01-07
Hi HDave,

I'm glad it was of help.  If I might ask, do you remember what extra steps?

edit:  Oops.  Never mind.  You posted the extra steps on the guide thread.  Thanks.  Clever too!

---

