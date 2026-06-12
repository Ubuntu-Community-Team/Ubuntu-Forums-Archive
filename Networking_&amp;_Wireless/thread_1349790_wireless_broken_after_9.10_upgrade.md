---
title: "wireless broken after 9.10 upgrade"
date: 2009-12-08
forum: Networking &amp; Wireless
---

### Post by sharp11 on 2009-12-08
I've never had a problem before connecting my desktop wirelessly to my home network. Wireless card is Ralink RT2561/RT61 802.11g PCI. 

After the upgrade, it actually worked for a while, sporadically, and now it has given up completely. One weird thing I noticed is that lshw uses the logical name wmaster0, but netmanager seems to use the logical name wlan0. I am not savvy enough to know whether that's significant.

Any suggestions would be great - I've pored over the troubleshooting docs, but nothing seems to fit. Both NM and wifi-radar just sit their trying and trying and finally give up.

Here is possibly relevant section of syslog: 

```
Dec  8 13:19:12 boletus NetworkManager: <info>  Config: added 'ssid' value 'MY_ESSID'
Dec  8 13:19:12 boletus NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Dec  8 13:19:12 boletus NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Dec  8 13:19:12 boletus NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Dec  8 13:19:12 boletus NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Dec  8 13:19:12 boletus NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Dec  8 13:19:12 boletus NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec  8 13:19:12 boletus NetworkManager: <info>  Config: set interface ap_scan to 1
Dec  8 13:19:12 boletus NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
Dec  8 13:19:14 boletus wpa_supplicant[809]: CTRL-EVENT-SCAN-RESULTS 
Dec  8 13:19:20 boletus wpa_supplicant[809]: CTRL-EVENT-SCAN-RESULTS 
Dec  8 13:19:27 boletus wpa_supplicant[809]: CTRL-EVENT-SCAN-RESULTS 
Dec  8 13:19:33 boletus wpa_supplicant[809]: CTRL-EVENT-SCAN-RESULTS 
Dec  8 13:19:39 boletus wpa_supplicant[809]: CTRL-EVENT-SCAN-RESULTS 
Dec  8 13:19:46 boletus wpa_supplicant[809]: CTRL-EVENT-SCAN-RESULTS 
Dec  8 13:19:52 boletus wpa_supplicant[809]: CTRL-EVENT-SCAN-RESULTS 
Dec  8 13:19:52 boletus wpa_supplicant[809]: Trying to associate with 00:24:7b:04:88:ea (SSID='MY_ESSID' freq=2412 MHz)
Dec  8 13:19:52 boletus wpa_supplicant[809]: Association request to the driver failed
```

---

### Post by jared3000 on 2009-12-08
EDIT: I should have read your first sentence... the bug I've been grappling with is on a Broadcom BCM4312 802.11

Sorry I can't actually help; good luck!

---

### Post by sharp11 on 2009-12-08
Thanks, but as mentioned above, I'm using Ralink wireless card.

---

### Post by TimBilly on 2010-01-29
I think I'm having the same problem. I disabled my wireless adapter (unchecked it in the GUI) to diagnose some issues with my router, and now it doesn't see any SSIDs no matter what I do.

[FONT="Courier New"]~& iwlist scan
lo           Interface doesn't support scanning

eth0          Interface doesn't support scanning

wmaster0     Interface doesn't support scanning

wlan0        No scan results[/FONT]

Did you solve this?

---

### Post by sharp11 on 2010-01-29
> **TimBilly said:**
> 

Did you solve this?

Sorry, I never did. I strung an ethernet cable across my office and wrote off the wifi. But my situation may be different from yours. I get sporadic connections, not a total blank.

---

### Post by TimBilly on 2010-02-02
Well, I solved my problem. I did a clean install of 9.10 on a second hard drive, and was having the exact same problem with the new install. I shut everything down, took out the PCI card (Belkin F5D7000 v3001) and reinserted it. After I booted back up, I can see wireless APs (mine, my neighbor's, etc) again. So, must have been a loose PCI slot connection, or dust or something. Go figure.

---

### Post by JMorg on 2010-02-02
Have any other networks appeared in your area. Are you picking up different SSID's other than your own? And have you also tried changing the channel that the network broadcasts on to see if the intermittent drops isn't caused from channel interference or high amounts of packet loss? Or are you no longer seeing any broadcasts in general?

---

